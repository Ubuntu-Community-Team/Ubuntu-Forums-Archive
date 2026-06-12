---
title: "Unable to install likewise-open"
date: 2011-09-06
forum: General Help
---

### Post by karthick87 on 2011-09-06
I am unable to install likewise-open. I am getting the following error..

```
karthick@karthick:~$ sudo apt-get install likewise-open
Reading package lists... Done
Building dependency tree       
Reading state information... Done
likewise-open is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 369 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up likewise-open (5.4.0.42111-2ubuntu2.1) ...
 * Starting Likewise Service Manager: lwsmd                              [fail] 
Error: ERROR_FILE_NOT_FOUND (2)
Unknown error
dpkg: error processing likewise-open (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 likewise-open
E: Sub-process /usr/bin/dpkg returned an error code (1)
karthick@karthick:~$ 
```

---

