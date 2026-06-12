---
title: "ODBCConfig  error"
date: 2009-09-17
forum: General Help
---

### Post by fafifurnir on 2009-09-17
Hello to all,

I have installed unixodbc and unixodbc-bin with related libraries on Ubuntu desktop 9.04

From shell odbcinst work well, but when I launch Gui ODBCConfig I have this error :
1) Failed to execute SQLManageDataSources()

I press enter and :

2) The most likely reason for this is that the QT Gui Plugin could not be found or could not be loaded.
Ensure that libodbcinstQ*. files are in the  library search path.
The path can be altered by setting LTD_LIBRARY_PATH environment variable

Qt libraries are installed, I have tried to insert this line in ld.so.conf :
LTDL_LIBRARY_PATH = "usr/lib:"
but without result

Can anyone help me ?

---

