---
title: "Failure on Startup"
date: 2011-01-17
forum: General Help
---

### Post by fredgal on 2011-01-17
I installed ubuntu 10.10 on a Dell Dimension 3100 as the sole operating system. It ran well for several startups/restarts, then it failed with results shown below.  After Ifailed to correct the problem, I reinstalled 10.10 from a different disk.  Again after running well for a while, it failed giving the same error messages. 
   Upon failure, I got the message:
   mount: dev/disk/by -uuid b50f85d-dd6d-4c00-91aa-9faf1efb0bba on /root
   failed: Invalid argument.
   mount: mounting /dev on /root/dev failed: Nosuch file or directory
   Target file system doesn't have requested sbin/init.
   No init found.  Try passing init= bootarg
A prompt came, "initramfs".
I entered:
   init= bootarg (also tried init=bootarg)
and got
   /bin/sh bootarg: not found

I then booted a live version of ubuntu 10.10.  It reported that there was a file system of the size if the hard disk.  I tried to load it and got:
   Error mounting: mount: wrong for type,bad option,bad superblock ondev/sda1, missing code    page or helper program or other error.  In some cases useful info is found in syslog -    try dmesg |tail or so.
I did see anything that seemed to help in syslog.
   
My desire is to copy the the data in my home file even if I cannot first reboot the operating system.
Thanks in advance for any help
fredgal

---

