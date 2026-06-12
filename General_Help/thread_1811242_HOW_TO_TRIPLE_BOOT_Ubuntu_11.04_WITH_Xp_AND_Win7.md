---
title: "HOW TO TRIPLE BOOT Ubuntu 11.04 WITH Xp AND Win7"
date: 2011-07-24
forum: General Help
---

### Post by love_linux1 on 2011-07-24
**[SIZE="2"][FONT="Arial Black"]how to triple boot ubuntu with xp and 7?[/FONT][/SIZE]**

 I have installed 'WIN XP' 1st on HD1, then installed 'WIN 7' on HD2.. Now i want to install ubuntu 11.04  on HD3, means fresh install (not windows alongside). I want to know whether there will be any BOOT problem for XP and 7? Will it show all 3 os?

Please help..

---

### Post by Jerry N on 2011-07-24
> **love_linux1 said:**
> **[SIZE="2"][FONT="Arial Black"]how to triple boot ubuntu with xp and 7?[/FONT][/SIZE]**

 I have installed 'WIN XP' 1st on HD1, then installed 'WIN 7' on HD2.. Now i want to install ubuntu 11.04  on HD3, means fresh install (not windows alongside). I want to know whether there will be any BOOT problem for XP and 7? Will it show all 3 os?

Please help..

I assume you mean you 3 separate hard drives.  If so, disconnect HD1 and HD2 then install Ubuntu on HD3.  Get Ubuntu running the way you want and the (with the power off, of course) reconnect HD1 and HD2.  On your next bootup, your computer should boot to Ubuntu and should find XP and Win 7.  On subsequent boot-ups, XP and Win 7 should be on the list of boot options.  In my case, I have XP and Win 7 on one drive and 3 different Mint and Ubuntu versions on a second drive.  

Jerry

Jerry

---

### Post by love_linux1 on 2011-07-24
sorry, i wantd to mean 3 hd partitions.. Hdp1, hdp2, hdp3.

---

### Post by Jerry N on 2011-07-24
> **love_linux1 said:**
> sorry, i wantd to mean 3 hd partitions.. Hdp1, hdp2, hdp3.

I would suggest using the manual partitioning option.  That way you can set up Ubuntu just the way you want, not the way the installer thinks it should be.  DO NOT let the Ubuntu partitioner try to adjust the size of a Windows partition. As it's installed, Ubuntu should have no problem in finding the Windows partitions and putting them on the boot option list.  

Jerry

---

### Post by ssreddy555 on 2011-07-24
Install Windows versions first on different partitions (NTFS) & then Ubuntu on the 3rd partition (ext 4) which will load the GRUB with all the necessary options.

---

### Post by loolooyyyy on 2011-07-24
> **love_linux1 said:**
> **[SIZE="2"][FONT="Arial Black"]how to triple boot ubuntu with xp and 7?[/FONT][/SIZE]**

 I have installed 'WIN XP' 1st on HD1, then installed 'WIN 7' on HD2.. Now i want to install ubuntu 11.04  on HD3, means fresh install (not windows alongside). I want to know whether there will be any BOOT problem for XP and 7? Will it show all 3 os?

Please help..

if you already have used all the space in your disk, resize it IN windows, then you'll have extra space
install ubuntu there, remember to create the swap area too
and there will be no booting problem, ubuntu recognizes both windows installations
BUT do create backup of your data, if you make a mistake during installation of ANY OS, you can erase all your data

---

### Post by love_linux1 on 2011-07-24
Thanks everyone to reply.

Which installer should I use? 

Ubuntu-11.04-desktop-i386.iso or Ubuntu-11.04-desktop-amd64? I have a 32-bit intel pc. 

Which one is called natty narwhal?

thank you.

---

### Post by ssreddy555 on 2011-07-25
i 386.iso.

Ubuntu 11.04 - aka Natty Narwhal.

---

### Post by love_linux1 on 2011-07-25
Should I change the filesystem of the partition (ex. ntfs to ext4) while installing Ubuntu on 2nd partition of that hard disk containing XP on its 1st partition?

---

### Post by Vaphell on 2011-07-25
ubuntu does support ntfs filesystems but wouldn't work when installed on one, because ntfs doesn't support linux permissions. You need to use ext3/4 for ubuntu partition.

---

### Post by love_linux1 on 2011-07-25
yea, but will it affect windows xp bootloader?

---

### Post by ssreddy555 on 2011-07-25
Once u install Ubuntu, It will load GRUB which will overwrite windows boot loader; so it will not exist anymore.

---

