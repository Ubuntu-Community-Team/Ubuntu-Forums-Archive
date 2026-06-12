---
title: "set default boot partition"
date: 2010-12-22
forum: General Help
---

### Post by nilanjan1988 on 2010-12-22
i have installed ubuntu few days ago. after that i have instlled cent os in another partition.now i want to delete cent os but at present my default grub is loaded in centos,s boot partition. how to fix mbr with ubuntu grub as my default boot loader........please help me..........

---

### Post by howefield on 2010-12-22
Moved to General Help.

---

### Post by hhh on 2010-12-22
Boot into your Ubuntu partition. Open a terminal and run...
```
sudo grub-setup /dev/xxx
```...where xxx is the name of the drive Ubuntu is on (probably sda or hda. NOT the individual partition, e.g. sda5. One way to tell is to open System>Administration>Gparted or Partition Editor or whatever they call it there and see how the drive is labeled in the drop-down menu in the upper right corner.) Then run```
sudo update-grub
``` When you reboot, Ubuntu will be at the top of your Grub menu and you can then remove CentOS.

---

### Post by efflandt on 2010-12-22
If you read **man grub-setup** it says:

> You should not normally run this program directly.  Use grub-install insteadSo you should normally use **sudo grub-install /dev/sdx** (use the actual boot drive like /dev/sda).

For everything you wanted to know about Ubuntu and grub2 (or not) see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by hhh on 2010-12-22
> **efflandt said:**
> So you should normally use **sudo grub-install /dev/sdx** (use the actual boot drive like /dev/sda).
As was explained to me elsewhere, grub-install is a more sophisticated command, which does some testing and checking and redoes a lot of the grub installation, while grub-setup is a simple process of writing onto the disk. The end result may well be the same in most cases, but on the principle of "if it ain't broke, don't fix it", I'd prefer grub-setup if the grub installation is basically OK.

---

### Post by garvinrick4 on 2010-12-22
Centos uses grub-legacy and ubuntu grub2. Might as well look at grub-script as to get rid
of grub-legacy and have only grub2 installed in Ubuntu as to save any problems in future.
If you can partner download this script to DESKTOP and then run this code in a terminal and post to this thread only takes 1 minute. Puts a file called RESULTS on your desktop, copy and paste it here and then highlight whole thing and hit # sign in upper right of message box, will put it in nice box to read from. Here is site and below code to run after downloaded to DESKTOP:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```Just noticed you want to delete Centos, that is good will make this easy. Post bootscript please so as to know surprises.

---

### Post by nilanjan1988 on 2011-01-03
> **hhh said:**
> Boot into your Ubuntu partition. Open a terminal and run...
```
sudo grub-setup /dev/xxx
```...where xxx is the name of the drive Ubuntu is on (probably sda or hda. NOT the individual partition, e.g. sda5. One way to tell is to open System>Administration>Gparted or Partition Editor or whatever they call it there and see how the drive is labeled in the drop-down menu in the upper right corner.) Then run```
sudo update-grub
``` When you reboot, Ubuntu will be at the top of your Grub menu and you can then remove CentOS.



[COLOR="Blue"]**_*THANK YOU VERY MUCH........MANY MANY THANX:popcorn:*_**[/COLOR]

---

