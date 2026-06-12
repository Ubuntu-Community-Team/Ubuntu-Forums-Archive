---
title: "Suprise!  sh:&gt;grub at boot and that's it."
date: 2010-01-25
forum: General Help
---

### Post by bluefoxox on 2010-01-25
Hello All,
 
Today I was in class excited that I was downloading the Ubuntu .iso to my USB drive so I could go home and install a bootable version of Ubuntu to my USB... I side tracked a little and ended up at McDonald's (hey why not they now have free wifi now!). I just got done with a double QP with cheese some fries and a coke and was transfering my newly aquired .iso file to my Ubuntu's downloads folder when the computer decided to freeze up entirely. I did not worry, since I knew I was working with Linux here (right?). I had to do a hard shut down. When I rebooted and chose Ubuntu from the windows boot loader (Windows 7), I got a suprise. The screen renedered 
 
sh:grub>
 
The install is from Wubi and is 64bit. I am in over my head at this point. I would rather not have to re-install everything since I have spent countless hours getting this notebook just the way I want it using Ubuntu. I could use a hand in fixing this, any help is greatly appreciated.
 
Thanks!
Patrick

---

### Post by gnack on 2010-01-25
Seems like a known issue with wubi:

[http://ubuntuforums.org/showthread.php?t=1314064](http://ubuntuforums.org/showthread.php?t=1314064)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

---

### Post by bluefoxox on 2010-01-25
Thanks for the reply, as it ends up running chkdsk /r C: in windows happened to put everything back in it's place.  Joy!

---

### Post by sroberson on 2010-01-25
I get this, too, after a full reinstall.  I've had a dickens of a time getting my new install to work.  I have multiple disks and partitions. 

Anyway, I now get this and I type "exit" [enter] and grub then loads.

Hopefully this will be fixed soon.

Scott

---

### Post by bluefoxox on 2010-01-26
Scott have you tried grub 1.97 beta 4?  It worked for me.  Grub2 is buggy.  In fact, Linux is buggy, locks up and does not work well with others in general.  Sometimes I do not know why I bother!

---

