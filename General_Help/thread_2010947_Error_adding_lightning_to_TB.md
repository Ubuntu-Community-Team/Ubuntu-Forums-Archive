---
title: "Error adding lightning to TB"
date: 2012-06-26
forum: General Help
---

### Post by lsutiger on 2012-06-26
OS - Ubuntu 9.10 Thunderbird 13.0.1
Program is installed in folder /usr/lib/thunderbird, with a link in /usr/bin. The data folder in in the /home/<USER> folder

I am trying to add lightning to TB , but it will not show after installing. A look at the error console shows these two errors:
```
Timestamp: 06/26/2012 08:24:41 AM
Error: ERROR addons.xpi: SQL error 8: attempt to write a readonly database
Source File: resource:///modules/XPIProvider.jsm
Line: 3953

Timestamp: 06/26/2012 08:24:41 AM
Error: ERROR addons.xpi: Failed to add add-on {e2fda1a4-762b-4020-b5ad-a41df1933103} in app-profile to database: [Exception... "Component returned failure code: 0x80520013 (NS_ERROR_FILE_READ_ONLY) [mozIStorageStatement.execute]"  nsresult: "0x80520013 (NS_ERROR_FILE_READ_ONLY)"  location: "JS frame :: resource:///modules/XPIProvider.jsm :: executeStatement :: line 3975"  data: no]
Source File: resource:///modules/XPIProvider.jsm
Line: 3975
```



So the question is, which files do I need to change the read only permission?

---

