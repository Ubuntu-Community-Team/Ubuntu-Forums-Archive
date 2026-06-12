---
title: "Wubi won't install Netbook Edition"
date: 2010-08-28
forum: General Help
---

### Post by AngGalaxy on 2010-08-28
I'm trying to install Ubuntu Netbook Edition on my Asus Eee PC 1015 netbook (running Windows 7 starter) using wubi, but it fails to install every time. Wubi will download the torrent, download the .iso, then tell me it "cannot retrieve the required installation files."  I have also tried manually downloading the .iso and placing it in the same folder as wubi, but it fails to validate the file and begins downloading the torrent.

Just to check, I tried using wubi to install Ubuntu 10.4 and had no problems at all.

I took a look at the log, which says 
```
08-27 13:37 DEBUG  TaskList: ### Running check_iso...
08-27 13:37 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
08-27 13:37 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
08-27 13:37 DEBUG  Distro: wrong version: 10.04 != 10.04.1
08-27 13:37 DEBUG  TaskList: ### Finished check_iso
08-27 13:37 ERROR  TaskList: Could not retrieve the required installation files
```Seems to say the version is incorrect.  What am I missing?

EDIT:  Right, so it was the wrong version:  Ubuntu is 10.04.1, Ubuntu Netbook Edition is still 10.04 and won't work with wubi 10.4.1.  I found wubi version 10.4 on cnet.com and used that, install worked.

---

### Post by rubing on 2010-09-25
same problem.  bump

---

### Post by Immahazmacookie on 2010-12-05
Just burn the Iso to a cd, or mount it using Deamon Tools or something, then run Wubi off the Iso.

---

