---
title: "Dual Boot issues with file sharing"
date: 2011-01-25
forum: General Help
---

### Post by amunger on 2011-01-25
Hi, I am running Ubuntu 10.0.4 on a dual boot with Windows 7. I was happily dual-booting, when one day, my Windows OS lost a driver info and the keyboard and mouse rendered useless (oh Windows...). Anyway, i could not access any files without the keyboard/mouse, and there are some very important files on my Windows drive. Fortunately I can still use my computer through Ubuntu. 

I know that I could set up file sharing if I have access to both Windows and Ubuntu, but is there any way to access my Windows files from Ubuntu without logging on to Windows an setting anything up?

P.S. I'm a relative beginner in terminal. 

Thank in advance for your help!

---

### Post by mikewhatever on 2011-01-25
Ubuntu should have read/write access to the Windows partition by default. The Windows partition should show in the left panel of the file browser, just click it. Is there any difficulty in accessing the files? Setting up file sharing would have been useful, had you had several computers, but as the dual boot term implies, you only have one.

---

### Post by drewsus on 2011-01-25
as said above, but to add, if you hadn't already labelled the windows partitions, then it will be called something like "##GB File System" (where ## is the size of that partition).

---

### Post by amunger on 2011-01-25
Yes, I see what you mean, there is a drive called "SYSTEM" or "1.0 TB Hard Disk: SYSTEM", which I thought would be the C: Drive on Windows. but when I open it, there are only two folders, "Boot" and "System Volume Information", and 2 files, "bootmgr" and "BOOTSECT.BAK". None of my windows files are in any of these folders. Am I doing something wrong?

---

### Post by mikewhatever on 2011-01-25
That seems to be the boot partition, just not clear why it would be 1TB the size. Can you post the output of the **sudo fdisk -l** command to show your partition layout.

---

### Post by amunger on 2011-01-26
Sure, 
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      119991   963719168    7  HPFS/NTFS
/dev/sda4          119991      121602    12938240    7  HPFS/NTFS

```

---

### Post by garvinrick4 on 2011-01-26
Add this program to make a label for Windows:
Boot into Ubuntu and open a terminal and:
```
sudo apt-get install gparted
```Go to System/Admin to gparted and open:
Right click on sda2 and go to label and make a label name;
Then hit green apply arrow and close gparted:
Now in places drop down menu should be the partition label name:
Open it and it will be your Windows partition:
##sda1 that is labeled SYSTEM just leave it be it is your Windows boot partition:
##sda4 is recovery partition that is how it comes from factory
I am assuming your Ubuntu drive is a USB drive and you did not give us that in the
fdisk -l and it is the sdb drive.

---

### Post by amunger on 2011-01-26
It worked, thank you so much. The problem was I just couldn't find it. When I looked in GParted in the Information about sda2, I saw it was mounted on /host. when I went in /host, there was my C: drive. 
Thanks again to everyone who helped.

---

### Post by garvinrick4 on 2011-01-26
> **amunger said:**
> It worked, thank you so much. The problem was I just couldn't find it. When I looked in GParted in the Information about sda2, I saw it was mounted on /host. when I went in /host, there was my C: drive. 
Thanks again to everyone who helped. That is a WUBI install, from now on when
posting make sure you say WUBI install in post. 
That is good you found it in your file system under /host. 
In partition set-up no /host in file system as there is in WUBI install. 
Enjoy your Ubuntu.

---

### Post by amunger on 2011-01-27
Ok, thanks. And WUBI is the program that I used to install Ubuntu, I remember. And I assume that has something to do with the dual-boot.

---

### Post by garvinrick4 on 2011-01-27
#Wubi is a Folder inside of Windows C: drive called Ubuntu right next to Users and you
can uninstall from there. It attaches itself to Windows bootmanager and so as to give you
your choice of Windows or Ubuntu to boot from.
#The other style is a partition install where it is seperate from windows on its own partition
of Hard Drive. 
#They use two different methods of booting and there are some users that are very good with WUBI and can be very helpful and some that are good at partition installs. 
##Enjoy your Ubuntu.
#Here are a couple of links to save for reading:
[[wubi] Wubi megathread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by amunger on 2011-01-27
Good explanation, Thanks.

---

