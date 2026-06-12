---
title: "Laptop hangs and freezes ( 20iso_scan line 45 error)"
date: 2010-04-26
forum: General Help
---

### Post by Slimshad86 on 2010-04-26
I have laptop ASUS F5RLseries and had lots of problems installing ubuntu on hard disk
common problems includes hang ups , freezes , error messages 
example :
> /scripts/casper-premount/20iso_scan: line 45: can't open /dev/sdx: No medium found
stdin:  I/O error

(initramfs) Could not find the ISO /ubuntu/install/installation.iso This could also happen if the file system is not clean because of an operating system crash, ................The problem cause was locking my hard disk from BIOS with a password , it was solved after I cleared this password

the problem can also be caused by using Windows Vista BitLocker drive encryption as stated in the following thread :
[http://ubuntuforums.org/showthread.php?t=875570](http://ubuntuforums.org/showthread.php?t=875570)

---

### Post by MasterSplyntr on 2010-07-20
I have the same problem with my Windows 7 and Wubi Ubuntu 10.04 LTS. I have executed "chkdsk /R" but still it doesn't work. (I should maybe mention that I use the amd64 version - i will try the i386 one in the next minutes.)
Can someone please help me to handle this problem?
Thanks in advance,
Chris

---

