---
title: "NFS user ID problem"
date: 2011-08-09
forum: General Help
---

### Post by vielmaj on 2011-08-09
Hello,

I upgraded from Debian Squeeze to Ubuntu 11.04.  I did a fresh install  and transferred the user information from the old system to the new  system (/etc/passwd, /etc/shadow).

If I ssh into the server and run ls -l I get the following.

total 19512
drwxr-xr-x  8 vielmaj users      928 2011-07-31 16:55 BaTiO3
drwxr-xr-x  3 vielmaj users      120 2011-06-22 17:36 BiFeO3
drwxr-xr-x  2 vielmaj users      568 2011-07-28 08:36 bin
drwxr-xr-x  9 vielmaj users      312 2011-06-22 17:38 BTO
drwxr-xr-x  6 vielmaj users      160 2011-04-01 14:24 BTOFit

If I ssh into a client and run ls -l I get this

total 19512
drwxr-xr-x  8 4294967294 4294967294      928 2011-07-31 16:55 BaTiO3
drwxr-xr-x  3 4294967294 4294967294      120 2011-06-22 17:36 BiFeO3
drwxr-xr-x  2 4294967294 4294967294      568 2011-07-28 08:36 bin
drwxr-xr-x  9 4294967294 4294967294      312 2011-06-22 17:38 BTO
drwxr-xr-x  6 4294967294 4294967294      160 2011-04-01 14:24 BTOFit

Both the server and the client were upgraded.  I am not sure where to begin.

Thanks,

Jason

---

