---
title: "odbc with ms sql server"
date: 2009-08-26
forum: General Help
---

### Post by davidtuti on 2009-08-26
Hi,

I try to connect using odbc to a microsoft sql server but when I try to connect it says me:
```

isql -v prueba usser password
[S1000][unixODBC][FreeTDS][SQL Server]Unable to connect to data source
[08S01][unixODBC][FreeTDS][SQL Server]Unable to connect: Adaptive Server is unavailable or does not exist
[ISQL]ERROR: Could not SQLConnect
david@david-desktop:/etc$

```

I have this configuration files:

```

/etc/odbc.ini
[prueba]

Description        = Coeenxion para microsoft sql server
Driver          = ms-sql                                
Servername      = ms-sql                                
#Servername      = defekas62                            
UID =           emuser                                  
Port    =               1433   


/etc/freetds/freetds.conf  
....
....
[ms-sql]                    
     # Version 8.0 para SQL Server 2000
     # Version 7.0 para SQL Server 7   
     # Version 6.0 para SQL Server 6   
     host = defekas62                  
     port = 1433                       
     tds version = 7.0



/etc/odbcinst.ini
[ms-sql]
Description             =  Conexiona microsoft sql server
Driver          = /usr/lib/odbc/libtdsodbc.so
Setup           = /usr/lib/odbc/libtdsS.so
UsageCount      = 1
FileUsage       = 1



```

Could you help me?
Many thnaks and sorry for my english!

---

