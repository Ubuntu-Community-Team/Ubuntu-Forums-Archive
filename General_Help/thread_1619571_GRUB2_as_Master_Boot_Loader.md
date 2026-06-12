---
title: "GRUB2 as Master Boot Loader"
date: 2010-11-11
forum: General Help
---

### Post by vikrang on 2010-11-11
I had this doubt for quite some time
 
i am very much comfortable with GRUB 2 and configuring the same...
 
However one thing that prevents me is my fear of WIN partition bein inaccessibe due to my constant swithcover of distros
 
I have this doubt ,...
 
Assume I have one WIN installation and I decide to install a couple of distros
 
First , I install Ubuntu 10.04 using GRUB2 and opt to install in MBR...Grub 2 detects WIN and no problems
 
Next I want to install a second distro say Fedora or Mepis which uses Legacy GRUB , Here I opt to install GRUB in the local partition..When I run grub-mkconfig in Ubuntu, this entry is auto probed and adds it up ...Very impressive
 
Next , some distro like Slackware using LILO , I think this can be hooked to GRUB 2 as well
 
So far so good 
 
 
Now , suppose I want to uninstall the base from where GRUB2 was installed namedly UBUNTU 10.04 (just a hypothetical case ..Will never uninstall Ubunntu!!!) by deleting Ubuntu Partition then I would not be able to boot into any any of the remaining OS right?..This is what I dread...There are workarounds like re-install GRUb, system rescue CD etc..But I dont want that...
 
Another doubt that is lingering , in the case of a Dual boot say Linux and WIN7 
 
On deletion of Linux partition , will GRUB2 boot with just WIN7 or it requires a Linux installation? I understand that this is meaningless as you cant do anything in GRUB without Linux...But still? a theoretical case!!

---

### Post by dcstar on 2010-11-12
[http://ubuntuforums.org/showthread.php?t=1300461](http://ubuntuforums.org/showthread.php?t=1300461)

---

### Post by hhh on 2010-11-12
I've never used Lilo, but with Grub and Grub2 the last OS you install will be the one controlling Grub, but you can change that easily. Boot into another Linux partition and run (sudo) grub-update and then run grub-setup to your hard drive. Mine is labeled sda so...
```
sudo grub-setup /dev/sda
```

Boom, this partition now controls Grub.

Yes, if you were to delete the partition that installed Grub you'd get a grub error, it won't just boot Windows or another Linux partition. There are tools out there to restore the Windows MBR though (I dual boot XP so Super Grub Disc had saved my butt a few times, but I don't know which tools are good for later Windows versions).

---

### Post by vikrang on 2010-11-13
Thx DC Star and HHH

---

