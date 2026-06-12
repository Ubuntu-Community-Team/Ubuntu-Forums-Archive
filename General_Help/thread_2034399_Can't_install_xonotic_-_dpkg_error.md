---
title: "Can't install xonotic - dpkg error"
date: 2012-07-28
forum: General Help
---

### Post by J V on 2012-07-28
Long story short: There's an error I've never seen before and I don't know why it's happening. Can anyone help?

```
$ sudo apt-get install xonotic-data 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 arxcrashreporter libglew1.5
  libboost-program-options1.46.1 sni-qt:i386 libdevil1c2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xonotic-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/948 MB of archives.
After this operation, 955 MB of additional disk space will be used.
(Reading database ... 317275 files and directories currently installed.)
Unpacking xonotic-data (from .../xonotic-data_0.6.0-1~getdeb2_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/xonotic-data_0.6.0-1~getdeb2_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/xonotic-data_0.6.0-1~getdeb2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

