---
title: "Boot problem"
date: 2009-09-16
forum: General Help
---

### Post by anil7 on 2009-09-16
Hallo everyone. I just finished upgrading my version to 9.04 and when i try to boot the following message appears:

Gave up waiting for root device. Common problems:
-Boot args (cat/proc/cmdline)
-check rotdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?)
-missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/fc634e39-b4d9-4316-9d50-e38c7d71d4b0 does not exist. Dropping to a shell!

BusyBox v1.10.2(ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)


Any ideas????

---

### Post by blegs38552 on 2009-09-16
Typing exit and pressing enter should allow the boot process to proceed and you to log into Ubuntu.

I have had the same problem, I found that editing menu.lst (I don't remember the exact Terminal syntax but a google search will turn it up for you)and deleting the word "splash" from the selection for Ubuntu (towards the bottom of the file) kills the splash screen at startup, but also, for whatever reason, allows Ubuntu to boot without a problem.

I believe this is a known problem without a solution at this time.

---

### Post by freackout on 2009-09-16
> **anil7 said:**
> Hallo everyone. I just finished upgrading my version to 9.04 and when i try to boot the following message appears:

Gave up waiting for root device. Common problems:
-Boot args (cat/proc/cmdline)
-check rotdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?)
-missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/fc634e39-b4d9-4316-9d50-e38c7d71d4b0 does not exist. Dropping to a shell!


BusyBox v1.10.2(ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)


Any ideas????

its a case of mapping your drives if you can look into that however a drive mapper exists inpmagic live iso [http://partedmagic.com/](http://partedmagic.com/)

or try googling

---

### Post by itsjareds on 2009-09-16
Go to the terminal and type:
```
blkid
```

Do you see a UUID that is the same as the following UUID?
```
fc634e39-b4d9-4316-9d50-e38c7d71d4b0
```

---

