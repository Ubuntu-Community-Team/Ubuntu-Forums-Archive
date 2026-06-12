---
title: "Install Network Printer"
date: 2012-07-23
forum: General Help
---

### Post by KaisaUbun2 on 2012-07-23
I have a Dell V515w I'm trying to install it on Ubuntu 12.04 I downloaded the drivers off the Dell website for linux I ran the script start the installation and it freezes any clue?

I am given this error 

```
=============================
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install): parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver:i386'
: blank line in value of field 'Description'Errors were encountered while processing: dell-inkjet-09-driver-1.0-1.i386.deb
=============================
Execute: rm -rf /home/username/lua_f3IS5s

=============================
```

---

### Post by KaisaUbun2 on 2012-07-23
Since nobody seems to have a solution i will just login to Windows 7 and try there

---

### Post by empmachine on 2012-12-07
Same exact problem for me: 

after: gksudo sh dell-inkjet-09-driver-1.0-1.i386.deb.sh 

Verifying archive integrity... All good.
Uncompressing nixstaller.........................................................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 140509
cpu speed = 2001 MHz
ram size = 2004.1171875 MB
hd avail = 148327 MB
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 dell-inkjet-09-driver-1.0-1.i386.deb


I tried to look for /var/.../control but  the dir tmp.ci DNE.

I also spent time searching the install script for keywords/dirs/etc with no luck.
(the script was written for UBU 9..  not 12)

I'm beat (before even starting, lol).



It's so LAME that I can't just plug and play this printer... It's old..  I thought UBU was getting good with crap like that.  Oh well,  I don't have windows at all (haven't for yrs), so I guess I'll make some kind of mill out of the stupid printer and continue to use public facilities for printing...

at least I got the thing for free...



but still:
-1 on the UBU coolness count.

---

