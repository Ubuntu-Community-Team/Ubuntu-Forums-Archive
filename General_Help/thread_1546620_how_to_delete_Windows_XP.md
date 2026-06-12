---
title: "how to delete Windows XP"
date: 2010-08-05
forum: General Help
---

### Post by cookie6 on 2010-08-05
Right now I'm duel booting Windows XP and Ubuntu 10.04. I installed Ubuntu with wubi. I want Ubuntu to be my only operating system, so how would I delete Windows XP?

---

### Post by Rubi1200 on 2010-08-05
> **cookie6 said:**
> Right now I'm duel booting Windows XP and Ubuntu 10.04. I installed Ubuntu with wubi. I want Ubuntu to be my only operating system, so how would I delete Windows XP?
You cannot make Ubuntu the only operating system if you have a Wubi install.
 
In my opinion, you have 4 options:
 
1) make the Wubi install permanent on the hard-drive (which is possible)
 
2) install a fresh version of Ubuntu using the CD
 
3) continue dual-booting until you are comfortable with the idea of having a Linux only system
 
4) read, read, read as much about Ubuntu and Linux as you can before making the jump of getting rid of Windows (I say this because I have read more than a few posts from people who ended up regretting doing what you seem to want to do)

---

### Post by sydbat on 2010-08-05
> **cookie6 said:**
> Right now I'm duel booting Windows XP and Ubuntu 10.04. I installed Ubuntu with wubi. I want Ubuntu to be my only operating system, so how would I delete Windows XP?First, back everything up.

Second, back everything up.

Third - after backing everything up, you can pop the LiveCD in and install Ubuntu on the entire disk. Personally, I would make 3 partitions - / (root), /home, and /swap (usually twice the size of your RAM, if it is 2GB or less).

Fourth - put your backed-up data into your Home folder.

---

### Post by oldfred on 2010-08-05
wubi is installed inside the XP partition. If you delete XP you also delete your wubi install. I would create new partitions and convert to a full dual boot. After copying /home and any settings remove wubi from windows and shrink it to have only 20% (min it needs) free space until you know for sure you do not want it. Later you can delete it and use the space for data.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by corrytonapple on 2010-08-05
Are ubuntu and xp on the same partion?

---

### Post by sydbat on 2010-08-05
> **corrytonapple said:**
> Are ubuntu and xp on the same partion?If it is a wubi install, yes. That is, wubi installs Ubuntu as a program, so it is actually running as a virtual OS inside Windows. The dangers inherent in this mostly concern the fact that if anything happens to Windows (file corruption, for example), it will severely affect Ubuntu.

If Ubuntu and Windows are on separate partitions, this kind of thing does not happen.

I hope that made sense.

---

### Post by cookie6 on 2010-08-05
> **corrytonapple said:**
> Are ubuntu and xp on the same partion?


I have no idea what a partion is. Because I'm getting low on space, I only have a 60gb hard drive, and xp and ubuntu are on it. how would I make the Wubi install permanent on the hard-drive?

---

### Post by X.Cyclop on 2010-08-05
A partition is a storage space n the hard drive.

> **Rubi1200 said:**
>  
4) read, read, read as much about Ubuntu and Linux as you can before making the jump of getting rid of Windows (I say this because I have read more than a few posts from people who ended up regretting doing what you seem to want to do)
100% agree!

---

### Post by oldfred on 2010-08-05
If you have filled your 60GB drive, you will have to backup a lot of data to make room for the new install. It may be time to think about a new harddrive?

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by cookie6 on 2010-08-05
Well, I don't think its full yet, because on XP is says I still have about 20gb left, and is not warning me about low space, only Ubuntu is. So maybe the installation went wrong or something. :-&

---

### Post by cookie6 on 2010-08-05
I have Ubuntu burned on a disk, so should I uninstall it with add and remove programs, and install it with the disk?

---

### Post by oldfred on 2010-08-05
Windows needs about 20-30% free space to work well. Since you installed wubi, it is just a file inside the windows partition. That file is what in now saying it is filling up.

---

### Post by corrytonapple on 2010-08-05
> **sydbat said:**
> If it is a wubi install, yes. That is, wubi installs Ubuntu as a program, so it is actually running as a virtual OS inside Windows. The dangers inherent in this mostly concern the fact that if anything happens to Windows (file corruption, for example), it will severely affect Ubuntu.

If Ubuntu and Windows are on separate partitions, this kind of thing does not happen.

I hope that made sense.
Thank You. I am learning more everyday.
> 
I have no idea what a partion is. Because I'm getting low on space, I  only have a 60gb hard drive, and xp and ubuntu are on it. how would I  make the Wubi install permanent on the hard-drive?     
One hard drive that acts like there is two. Check this out:
[Newegg.com Internal Hard Drives]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=14&name=Internal-Hard-Drives")

---

### Post by cookie6 on 2010-08-05
> **corrytonapple said:**
> Thank You. I am learning more everyday.
One hard drive that acts like there is two. Check this out:
[Newegg.com Internal Hard Drives]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=14&name=Internal-Hard-Drives")

Well, I want get rid of Windows XP, and only have Ubuntu, and when Windows XP is gone, then I will have more space. But I don't know if I should uninstall xp first? Or should I install Ubuntu first? I have the cd burned, but I don't know if it works.....so I think I should remove Ubuntu (with add and remove programs) and then try the cd.

---

### Post by oldfred on 2010-08-05
The CD is a liveCD so you can also run it as is. 

Did you add a lot of programs? Did you back up /home separately so you can reinstall it. If you want a list of programs.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Then you can delete the wubi install from inside windows and shrink XP.

See early post on bcbc's instructions:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by holycow131415 on 2010-08-05
When you run the live CD, run the installer. You will have options to install ubuntu on all of the 60 GB hdd, or doing a true dual boot of XP/ubuntu. Sounds like you want to chose the option to install only ubuntu, so choose to use the whole drive. This will erase and  format your harddrive for you, erasing all your data, including Windows XP and your wubi install of ubuntu.

---

### Post by cookie6 on 2010-08-05
I just tried the cd, but it won't boot. #-o

---

### Post by holycow131415 on 2010-08-05
turn the computer on and hit the F12 key before your computer passes the bios screen for the boot menu, chose CD/DVD.

---

### Post by jroa on 2010-08-05
> **cookie6 said:**
> I just tried the cd, but it won't boot. #-o

What brand is the computer?

---

### Post by bcbc on 2010-08-05
If you uninstall wubi (the entry in Add/Remove programs is actually "Ubuntu") then it deletes your ubuntu install (all programs and data you are currently using under wubi). If there is anything on there you want to keep, make sure you back it up first. 

FYI (since it came up in the thread), Wubi doesn't run virtually under windows. It runs natively on the computer using a virtual disk that is a file under the windows file system (more precisely a file system accessible by windows). Wubi requires windows to install, and the windows boot manager (and grub4dos) to boot - thereafter it's pure ubuntu. e.g. you could take the root.disk, put it on an ntfs formatted external drive and boot it from a computer with only Ubuntu installed, just using grub. Not that you'd want to, but you can :)

---

