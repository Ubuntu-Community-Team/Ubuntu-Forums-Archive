---
title: "Dedicating more space to Ubuntu"
date: 2010-09-21
forum: General Help
---

### Post by Chishio on 2010-09-21
Okay, so I have successfully installed Ubuntu. However, it is the 9.10 version. Now when I want to upgrade to 10.04, it says that there is not enough space. It requires 500 MB more (the whole installation is said to have 1 GB). I am pretty sure that I have the required space on my disk but somehow I feel like that I have to dedicate it to Ubuntu. So, how do I do it ?

---

### Post by garvinrick4 on 2010-09-21
> **Chishio said:**
> Okay, so I have successfully installed Ubuntu. However, it is the 9.10 version. Now when I want to upgrade to 10.04, it says that there is not enough space. It requires 500 MB more (the whole installation is said to have 1 GB). I am pretty sure that I have the required space on my disk but somehow I feel like that I have to dedicate it to Ubuntu. So, how do I do it ? You have to download a package called gparted.
```
sudo apt-get install gparted
```
open the package and take a screenshot of it and put it as an attachment so we can see
if you have a setup that will allow to resize your ubuntu partition. 
 It is a Partitioning program so be careful not to screw around with drive until you get instruction.

---

### Post by Chishio on 2010-09-21
> **garvinrick4 said:**
> You have to download a package called gparted.
```
sudo apt-get install gparted
```open the package and take a screenshot of it and put it as an attachment so we can see
if you have a setup that will allow to resize your ubuntu partition. 
 It is a Partitioning program so be careful not to screw around with drive until you get instruction.

There you go 

[IMG]http://i282.photobucket.com/albums/kk249/NickSmasher/001.png[/IMG]

Hope this is what you ment.

---

### Post by -kg- on 2010-09-21
> **Chishio said:**
> Hope this is what you ment.

Actually, no.  If you've already installed Ubuntu, you didn't install it on the displayed hard drive.  You need to click on the drop down box in the upper right hand corner that displays "/dev/sda" and select your other hard drive (/dev/sdb), or if more than two, the one that actually has your Ubuntu installation on it.

All sda has on it is Windows partitions.  Of course, we're all assuming that you made a regular installation, and not with Wubi (installing Ubuntu under Windows).  If you installed using Wubi, that will be an entirely different matter.

---

### Post by Chishio on 2010-09-21
> **-kg- said:**
> Actually, no.  If you've already installed Ubuntu, you didn't install it on the displayed hard drive.  You need to click on the drop down box in the upper right hand corner that displays "/dev/sda" and select your other hard drive (/dev/sdb), or if more than two, the one that actually has your Ubuntu installation on it.

All sda has on it is Windows partitions.  Of course, we're all assuming that you made a regular installation, and not with Wubi (installing Ubuntu under Windows).  If you installed using Wubi, that will be an entirely different matter.

Ahh, sorry, completely forgot to mention that... did it with Wubi (under Windows, meaning I got dual boot...) My original HDD has 2 partitions - C and D drive. C has Windows on and D Ubuntu. The Unused 11,7 GB is refering to D.

---

### Post by Chishio on 2010-09-22
> **How do I resize the virtual disks?**

 You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) 
As an alternative, you can use the following script to move /home to a dedicated virtual disk.   
Download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), open a terminal and run: 

sudo sh wubi-add-virtual-disk /home 15000Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.  
You  should now reboot. If you are happy with the result, you can now remove  /home.backup. To undo the changes remove /home, copy rename  /home.backup to /home and remove the /home line in /etc/fstab. 
Note that contrary to previous information, this script is **not**  suitable for moving /usr - experienced users may be able to do this  manually, at own risk, following a process similar to that outlined in  the file. (Do not rename /usr until the very last moment, as rsync is  installed there.) 

Just found this, but I am not sure whether I could run LVPM on 9.10 and I do not know how to run wubi-add-virtual-disk (BIN file)... Any tips on this or possibly another solution ?

---

### Post by bcbc on 2010-09-22
Instead of upgrading to 10.04 on wubi, you could consider migrating to a direct install, or reinstalling. Is there a reason you need to keep using wubi?

Before you try to upgrade, migrate or resize - you should take a full backup of your data.

PS to run the wubi-add-virtual-disk you would just download it and run:```
sudo sh ~/Downloads/wubi-ad[TAB] /home size
``` (tab autocompletes, and size would be in MB e.g. 5000 = 5GB)

I haven't tested this but it looks like it will still work. (LVPM has some issues with recent versions of ubuntu, one of which is it requires grub-legacy, so it will replace grub2 when you install it).

---

