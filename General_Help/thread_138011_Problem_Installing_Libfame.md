---
title: "Problem Installing Libfame"
date: 2006-03-01
forum: General Help
---

### Post by mrgnash on 2006-03-01
After installing dvdrip, I ran into the following problem when trying to resolve an unmet dependency through apt-get -f install:

```
root@smg:/home/mrgnash/temp/gaim# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame-0.9
The following NEW packages will be installed:
  libfame-0.9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/77.7kB of archives.
After unpacking 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 168046 files and directories currently installed.)
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame0
Errors were encountered while processing:
 /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can anyone enlighten me? :confused:

---

### Post by Formidable1987 on 2006-03-04
I have the same problem atm. Could someone please help a newb out =(

---

