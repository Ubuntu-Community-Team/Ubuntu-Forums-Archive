---
title: "Not able to ftp"
date: 2010-04-09
forum: General Help
---

### Post by gargrk72 on 2010-04-09
Recently, I installed Ubuntu Karmic 9.10 on one P-IV cmptr. I am able to do all internet activities. However, not able to download from ftp site. Windows PC is still able to download from the same site. I tried to disable/enable ufw also but in vain.


Snapshots:-
**********************************************************
$ sudo ufw status
[sudo] password for rkgarg: 
Status: active
To                         Action      From
--                         ------      ----
21/tcp                     ALLOW       Anywhere

$ ftp ftpprd.ncep.noaa.gov
Connected to ftp.ncep.noaa.gov.
...
...
220 192.168.50.100 FTP server ready
Name (ftpprd.ncep.noaa.gov:rkgarg): anonymous

***********************************************************

After this it should ask for password as email address. However, it is stuck. Again REDHAT is able to login the ftp site.

Request for sol..

Regards!

gargrk72

---

### Post by lisati on 2010-04-09
Moved to own thread

---

