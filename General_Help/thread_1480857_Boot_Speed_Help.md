---
title: "Boot Speed Help"
date: 2010-05-12
forum: General Help
---

### Post by lvleph on 2010-05-12
I have been trying to get my Linux Mint Isadora (Lucid based) working perfectly. I have suspend, hibernate, and my graphics working. Now, I would like to improve my boot time. I started off with a 1:14 boot time and have gotten it down to 0:46, but compared to many others this is still slow. My goal is to get it down in the low to mid 30s. Anyway, please check my bootchart and help me fix things. **There is a dl link, _on picasa_,** so that you can see the full size.

One thing I know for sure is that CIFS (Samba) is causing some slow down. I can't seem to get it to just skip over my samba until the network is up and running.

[[IMG]http://lh5.ggpht.com/_AhWVbXcsVMQ/S-o06Sq9tcI/AAAAAAAAAoQ/B8t80fX-VIQ/s144/erichs-isadora-20100512-2.png[/IMG]]("http://picasaweb.google.com/lh/photo/4oV5hiro2zNEzgPukIDRAl2PRrzbTwml4QDAAzOCeIE?feat=embedwebsite"")

---

### Post by QIII on 2010-05-12
Hard to see at the resolution available, but it looks like an AMD Athlon, but I can't see if it is multi-core or not.

Remember that boot time is still affected by parameters such as drive speed (SATA or IDE?, RPM?, cache?), amount and speed of  RAM, the motherboard, the CPU, number of drives you are mounting, whether directories are encrypted, etc.

My boot charts indicate an average of about 15 seconds.  That's probably a function of my hardware.  

It can be said with a fair amount of certainty, for instance, that boot time with a Pentium 4 and 500MB of memory is going to be slower than with a nice new six-core processor and 16GB of DDR3 memory.

(Oh, boy!  I can't wait until the accountant (my wife) authorizes that purchase!)

---

### Post by lvleph on 2010-05-12
There is a download link on picasa. It is above the image in a menu.

I have seen netbooks with boot time in the 20s. I have a 1.2ghz single core (AMD L110) amd64 with 2GB RAM, SATA drive.

---

### Post by QIII on 2010-05-12
I downloaded it and still couldn't make it all out.

---

