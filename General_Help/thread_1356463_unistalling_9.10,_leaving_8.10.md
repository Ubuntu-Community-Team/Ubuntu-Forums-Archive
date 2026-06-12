---
title: "unistalling 9.10, leaving 8.10"
date: 2009-12-16
forum: General Help
---

### Post by gazpacho61 on 2009-12-16
Hi, everyone. Yesterday I tried to install Ubuntu 9.10 on a machine  (Asus Coolbox) with Ubuntu 8.10 (this is the original SO that came with it). Apparently I created 2 partitions (one for each SO) and, fortunately, with the GRUB I can still begin a session with Ub. 8.10, but I have a problem with Ub. 9.10: it freezes approx. 30 seconds after starting and need to do a hard reset everytime.
Now, I want to get rid of 9.10 and keep the version that works, recovering the space that Ubuntu 9.10 took. Any simple way to do that for a nearly 100% newbie?
8.10 goes fine, no problem at all from the beginning, which is why I want to keep it.
Thanks in advance

---

### Post by zvacet on 2009-12-16
You can remove partition with your Ubunt ulive Cd or with_ _[http://gparted.sourceforge.net . ]("http://gparted.sourceforge.net/")
Maybe you will have to reinstall grub.See [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

[]("http://gparted.sourceforge.net/")

---

### Post by gazpacho61 on 2009-12-16
Thanks for your help. I'll give it a go.

---

### Post by gazpacho61 on 2009-12-17
One question, before I try anything. If I use gparted do I get rid of Ubuntu 9.10 in that partition? i.e. is it like format d: in DOS? or do I have to do anything before that?
Thanks.

---

### Post by zvacet on 2009-12-17
In both cases (using Ubuntu live Cd or Gparted live CD) you will remove Ubuntu 9.10 .Just mark that partition for removal and that is it.You can add free space to your Intrepid or make home partition if you don´t have one.

---

