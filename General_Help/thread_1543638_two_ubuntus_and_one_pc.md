---
title: "two ubuntus and one pc"
date: 2010-08-01
forum: General Help
---

### Post by cherep on 2010-08-01
Hi all,
can I install two ubuntus on one pc using different partitions?
Thanks!

---

### Post by llamabr on 2010-08-01
Uh, huh, though the next person to come along will ask you why, and tell you it's probably a waste of space. But it's your disk -- don't listen to them:

[http://ubuntuforums.org/showthread.php?t=1435769&page=1](http://ubuntuforums.org/showthread.php?t=1435769&page=1)

---

### Post by BenAshton24 on 2010-08-01
Yes, but why? You know it's probably a waste of space :P

---

### Post by cherep on 2010-08-01
> **llamabr said:**
> Uh, huh, though the next person to come along will ask you why, and tell you it's probably a waste of space. But it's your disk -- don't listen to them:

[http://ubuntuforums.org/showthread.php?t=1435769&page=1](http://ubuntuforums.org/showthread.php?t=1435769&page=1)

Thanks, I will try :) I will not listen them!

> **BenAshton24 said:**
> Yes, but why? You know it's probably a waste of space :P

I don't hear you! :D

---

### Post by lukeiamyourfather on 2010-08-01
VirtualBox might help depending on why you want multiple versions of Ubuntu on one machine.

---

### Post by Elfy on 2010-08-01
~I've done it myself - one to keep and one to break. In fact if you have the space you could install a whole bunch of ubuntu's or other distros.

Grub could be problematic in the end.

I'd +1 the vbox scenario unless you have a pressing reason to install to a partition. 

You can pretty much do whatever, within reason, you want to.

Have fun :)


Probably a waste of space though ...

---

### Post by cherep on 2010-08-01
> **lukeiamyourfather said:**
> VirtualBox might help depending on why you want multiple versions of Ubuntu on one machine.

The reason is that I'm using 10.04 64 bit, but it is not so good like expected. (I have some problems with power management, backlight control and nvidia driver installation). Therefore, the tuning is needed. Unfortunately, I must have a working system (say, "ubuntu 1") in order to do some everyday tasks. I want to solve all my problems using test-instance (say, "ubuntu 2") and then apply all changes to "ubuntu 1". I guess, it makes sense. On the other hand, I have no restrictions on the space having 500Gb HDD :)

---

### Post by WorMzy on 2010-08-01
Absolutely, you can have as many partitions as your disk allows, and you can have an installation of Ubuntu in every one of them if you do so desire. :D

May I suggest that you make a dedicated partition to store all your personal data on though (Documents, Music, Pictures, etc), so that you don't end up having to copy over all your data to every partition, and have to try and keep it synchronised.

I currently have Arch Linux x64, Arch Linux x32, Debian 5.10, Ubuntu 9.10, Ubuntu 10.04 and Windows Vista all installed to the same disk.

---

### Post by 23dornot23d on 2010-08-01
There is a link here to one done the other day ..... [LINK]("http://ubuntuforums.org/showthread.php?t=1543183")

You might get some ideas from it ...... 

A Triple Boot ....... but depends if you have Windows or not ....

and if GRUB2 is already installed.

---

### Post by cherep on 2010-08-23
how I did it:

[LIST=1]
[*]load from LIVE CD
[*]run GParted
[*]swapoff the swap partition
[*]resize a partition in order to get some unallocated space
[*] install ubuntu using largest continous free space (grub 2 will be associated with new ubuntu)
[*]run
[/LIST]
```
sudo grub-install /dev/sda
```
to install grub 2 to the previous partition.

Now I have the place for experiments! Thanks!

---

