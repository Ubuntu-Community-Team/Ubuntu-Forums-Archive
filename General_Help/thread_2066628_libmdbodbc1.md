---
title: "libmdbodbc1"
date: 2012-10-05
forum: General Help
---

### Post by jbaum on 2012-10-05
Running 12.04 precise and libmdodbc1 with unix odbc. 

when running 'isql -v testdb' it returns 

"[IM002][unixODBC][Driver Manager]Data source name not found, and no default driver specified 
[ISQL]ERROR: Could not SQLConnect" 

/etc/odbc.ini 
```
[testdb] 
Description = test 
Driver = MDBToolsODBC 
Database = /root/test.mdb 
```

/etc/odbcinst.ini 
```
[MDBToolsODBC] 
Description = MDB Tools ODBC drivers 
Driver = libmdbodbc.so.1
Setup = libmdbodbc.so.1
FileUsage = 1 
Usage Count = 1
```

odbcinst -j
unixODBC 2.2.14
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /root/.odbc.ini
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8


~# odbcinst -q -d
[MDBTools]

~# odbcinst -q -s
[testdb]



~# find / -name 'libmdbodbc*'
/usr/lib/x86_64-linux-gnu/odbc/libmdbodbc.so.1.0.0
/usr/lib/x86_64-linux-gnu/odbc/libmdbodbc.so.1
/usr/share/doc/libmdbodbc1
/usr/share/lintian/overrides/libmdbodbc1
/var/lib/dpkg/info/libmdbodbc1:amd64.list
/var/lib/dpkg/info/libmdbodbc1:amd64.prerm
/var/lib/dpkg/info/libmdbodbc1:amd64.postinst
/var/lib/dpkg/info/libmdbodbc1:amd64.shlibs
/var/lib/dpkg/info/libmdbodbc1:amd64.md5sums
/var/lib/dpkg/info/libmdbodbc1:amd64.symbols
/var/cache/apt/archives/libmdbodbc1_0.7~rc1-4_amd64.deb


no sure where to go from here.

---

### Post by markmc on 2012-11-15
unixODBC needs to know the full path to libmdbodbc.so.1

```

Description = MDB Tools ODBC drivers 
Driver = /usr/lib/x86_64-linux-gnu/odbc/libmdbodbc.so.1

```

> **jbaum said:**
> Running 12.04 precise and libmdodbc1 with unix odbc. 

when running 'isql -v testdb' it returns 

"[IM002][unixODBC][Driver Manager]Data source name not found, and no default driver specified 
[ISQL]ERROR: Could not SQLConnect" 

/etc/odbc.ini 
```
[testdb] 
Description = test 
Driver = MDBToolsODBC 
Database = /root/test.mdb 
```

/etc/odbcinst.ini 
```
[MDBToolsODBC] 
Description = MDB Tools ODBC drivers 
Driver = libmdbodbc.so.1
Setup = libmdbodbc.so.1
FileUsage = 1 
Usage Count = 1
```

odbcinst -j
unixODBC 2.2.14
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /root/.odbc.ini
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8


~# odbcinst -q -d
[MDBTools]

~# odbcinst -q -s
[testdb]



~# find / -name 'libmdbodbc*'
/usr/lib/x86_64-linux-gnu/odbc/libmdbodbc.so.1.0.0
/usr/lib/x86_64-linux-gnu/odbc/libmdbodbc.so.1
/usr/share/doc/libmdbodbc1
/usr/share/lintian/overrides/libmdbodbc1
/var/lib/dpkg/info/libmdbodbc1:amd64.list
/var/lib/dpkg/info/libmdbodbc1:amd64.prerm
/var/lib/dpkg/info/libmdbodbc1:amd64.postinst
/var/lib/dpkg/info/libmdbodbc1:amd64.shlibs
/var/lib/dpkg/info/libmdbodbc1:amd64.md5sums
/var/lib/dpkg/info/libmdbodbc1:amd64.symbols
/var/cache/apt/archives/libmdbodbc1_0.7~rc1-4_amd64.deb


no sure where to go from here.

---

