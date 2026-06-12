---
title: "ODBCConfig failed"
date: 2010-03-01
forum: General Help
---

### Post by luisridaocruz on 2010-03-01
[SIZE=4]Hy,

[SIZE=3]I'm trying to create a ODBC data source after installation of an easySoft ODBC driver.
When I run ODBCConfig and try to create the data source in the 
User DSN tab the program terminates
with the following:

[/SIZE][SIZE=3]> sudo ODBCConfig
ODBCConfig: libltdl/ltdl.c:1178: try_dlopen: Assertion `filename && *filename' failed.
Aborted[/SIZE]

[SIZE=3]M[/SIZE]y odbc.ini and odbcinst.ini files are as follows:
[SIZE=3]
odbcinst.ini
------------------------------------------
[Easysoft ODBC-Oracle WP]
Description        = Easysoft Oracle ODBC WP Driver
Driver        = /usr/local/easysoft/oraclewp/lib/libesorawp.so
Setup        = /usr/local/easysoft/oraclewp/lib/libesorawpS.so
Threading        = 0
FileUsage        = 1
DontDLClose        = 1
UsageCount        = 1

odbc.ini
--------------------------------------- 
[ORACLE_SAMPLE]
driver        = Easysoft ODBC-Oracle WP
description        = Easysoft Oracle ODBC WP driver
server        = oserver
port        = 1521
sid        = 666.666.66.666/MAGNUS
user        = luisr
password        = myPassword
logging        = No
logfile        = 
enable_user_catalog        = yes
enable_synonyms        = yes
metadata_dont_change_case        = no
metadata_dont_do_schema        = no
metadata_id        = no
limit_long        = 0
 [/SIZE]
[/SIZE]

---

