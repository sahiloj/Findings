## eScan Management Console 14.0.1400.2281 - SQL Injection (Authenticated) ###

**Description:**
SQL injection in the View User Profile in MicroWorld Technologies eScan Management Console 14.0.1400.2281 allows any remote attacker to dump entire database and gain windows XP command shell to perform code execution on database server via GetUserCurrentPwd?UsrId=1.

**Vulnerable Product Version:**
14.0.1400.2281

**Date:**
16/05/2023

**CVE:** 
CVE-2023-31702

**CVE Author:**
Sahil Ojha

**Vendor Homepage:**
https://www.escanav.com

**Software Link:** 
https://cl.escanav.com/ewconsole.dll

**Tested on:** 
Windows

**Steps to reproduce:**
1. Login into the escan management console with a valid username and password as root user.
2. Navigate to URL: https://cl.escanav.com/ewconsole/ewconsole.dll/GetUserCurrentPwd?UsrId=1&cnt=5493 
![HTML Render](https://github.com/sahiloj/Findings/blob/main/sql%201.png)

3. Inject the payload into the UsrId parameter to confirm the SQL injection as shown below: 
https://cl.escanav.com/ewconsole/ewconsole.dll/GetUserCurrentPwd?UsrId=1;WAITFOR DELAY '0:0:5'--&cnt=4176
![HTML Render](https://github.com/sahiloj/Findings/blob/main/sql%204.png)
4. The time delay of 5 seconds confirmed that "UsrId" parameter was vulnerable to SQL Injection. Furthermore, it was also possible to dump all the databases and inject OS shell directly into the MS SQL Server using SQLMap tool.
![HTML Render](https://github.com/sahiloj/Findings/blob/main/sql%205%20to%20get%20os%20shell.png)
![HTML Render](https://github.com/sahiloj/Findings/blob/main/sql%206%20executing%20%20OS%20command%20on%20sql%20server.png)



