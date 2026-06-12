---
title: "php adodb mssql"
date: 2009-10-01
forum: General Help
---

### Post by trampman on 2009-10-01
Hi all

im running ubuntu server, and ive just put a site on that was running on iis fine, its coded using php5 and uses the adodb db abstraction layer to connect to a MSSQL database.

i now get the following errors 

**Notice**:  Use of undefined constant ODBC_BINMODE_RETURN - assumed 'ODBC_BINMODE_RETURN' in **/usr/share/php/adodb/adodb.inc.php** on line **4208**

**Notice**:  Use of undefined constant SQL_CUR_USE_DRIVER - assumed 'SQL_CUR_USE_DRIVER' in **/usr/share/php/adodb/adodb.inc.php** on line [B]4208

[/B]im sure it must be something simple but what i have no idea

any help anyone

---

### Post by CyberJack on 2009-10-05
Can you check if the error_reporting setting in the php.ini file is different on IIS and your current installation?
It is possible that the Notice was thrown on the IIS environment, but was not shown because of the error_reporting setting.

The notice is about a wrong definition of a constant.
My guess is that there is a define somewhere like this:
[PHP]define(ODBC_BINMODE_RETURN, 'value');[/PHP]
and it should be like this (with the quotes):
[PHP]define('ODBC_BINMODE_RETURN', 'value');[/PHP]

---

