---
title: "Ubuntu Backup &amp; Restore"
date: 2011-11-14
forum: General Help
---

### Post by fnyahoo on 2011-11-14
I have a quick and simple question. 

What should I do when I mess up the Ubuntu system? I cant do a clean install every time. That just kills me since I install many libraries and SDKs and stuff like that. With clean install i have to do them over again which takes long time. When i mess up Ubuntu and lets say it doesnt work properly and I can not solve it, can't I just go back to old kernels and update back again or something or perhaps use Sbackup??? i also use 2 partitions as "/" and "/home" would that make any difference??? Thank you in advance. I read some info on the web but I couldnt find a good answer for this situation.

---

### Post by Fred Doolie on 2011-11-14
I have the same situation. The simple answer is keep track of what you added/changed and copy it to a backup folder. For me that would be:
/home/fred
/etc/grub d/40_custom
/var/something-I-forget-what/apt/cache
and a few others.

When I reinstall I simply do a clean install, copy all that back, use Synaptic to put back LXDE and KDE and type "sudo update-grub2" in a shell window. The var/// folder is all the .debs Synaptic downloaded so reinstalling is very quick.

However I will add my own "YEAH! What's a good way to backup changes to the system?" 

I suppose the easier way is just to copy / (except for /mnt  /media and a few others) to a backup folder or use Clonezilla. Unlike a certain M$ OS you can restore Linux files right over a running system. Just reboot afterwards.

---

### Post by Rodney9 on 2011-11-14
When you get your OS just how you want, clone it with Clonezilla

How to - [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

Rodney

---

### Post by trudysmile on 2011-11-14
what is this&#65311; this is simple to solve&#65311;

---

### Post by fnyahoo on 2011-11-14
i have never used Clonezilla but I will give it a try. It sounds like the simplest solution for now. Any other ideas??? Thank you for both replies btw.

---

### Post by Mark Phelps on 2011-11-15
Strongly recommend Clonezilla -- use it all the time.  It does backups either of partitions or of entire disks.  I use the partition backup because it takes less space.

One tip in using it, you need to choose the Destination of the backup first.  Usually, in backup apps, you choose the Source first, but Clonezilla is different, so keep this in mind.

---

### Post by freechelmi on 2011-11-24
Hi, Clone Zilla is a Good Tool , but you can go further : 


-  I installed all my Stuff in / (sda2) , I created another partition for /home (sda3)


- I use Fsarchiver to create bu.fsa : a backup of / , you could use partclone as in clonezilla

- I customize a ubuntu Minimal LiveCD which contains a script at startup that can launch fsarchiver to restore bu.fsa on sda2

- I Put this customized live system on sda1 and modify Grub to be able to boot sda1.


So i always have an entry at boot to restore my system to the same as when it was installed.

---

### Post by BC59 on 2011-11-24
Some days ago I tested Remastersys. It's amazing!

First you fresh install your OS. Then you make all the tweaks possible, install uninstall apps and after a couple days of hard work you finish. Then before starting to load your personal staff, so the size of the whole system to keep it less than the capacity of a DVD, you start Remastersys.

This app is creating a new OS, your OS! You boot it and is installed exactly the same way like Ubuntu for example, but with all the changes you made.

Besides you can clone the DVD and distribute it to friends, to have a reference of a personalized OS.

Only drawbacks, you have to stay below of the size of a DVD as mentioned above and the proprietary drivers. If you like to use your new OS other computers, don't install the drivers because you will have conflicts.

---

### Post by mastablasta on 2011-11-24
that's not really for making backups.
 
also clonezilla...very complicated compared to RedoBackup. just look at how many steps are needed to mkae a simple image in clonezilla...
 
Also Deja Dup should be on Ubuntu.

---

### Post by HermanAB on 2011-11-24
Actually, the best solution is to use Kickstart on any one of the RPM distributions.  With a Debian distro you are out of luck though.

---

### Post by BC59 on 2011-11-24
> **mastablasta said:**
> that's not really for making backups.
 


No Remastersys doesn't have the capability to make a backup because of the size limitation. 
It's only a good solution to restore your computer status.

---

### Post by jjex22 on 2011-11-24
> **HermanAB said:**
> Actually, the best solution is to use Kickstart on any one of the RPM distributions.  With a Debian distro you are out of luck though.

I'm also a massive fan of YUM History on Fedora - really hopping we get something like that soon for Ubuntu!

Personally I have an install of puppy next to my swap partition (only 1GB) that I boot into to do my backup from every Sunday - I just unmount all partitions, then clone the whole disk to a backup drive and tar it so I can have the last two week's HDD images available whenever something goes wrong. 

Trouble is I've been doing this since day one so I've never looked at the alternatives - think I might give deje dup a go at file back up - Thanks Masterblaster - I'll still make a full HDD clone, but maybe less often - it does take a whole day at present!

---

