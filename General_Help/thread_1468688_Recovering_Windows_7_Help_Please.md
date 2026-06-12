---
title: "Recovering Windows 7 Help Please"
date: 2010-05-01
forum: General Help
---

### Post by iLeet on 2010-05-01
Hi, I have a 64-bit HP G60 Notebook and I installed Ubuntu 10
The problem is that if i want to recover Windows 7 from the Partition I can i pressed Esc and selected Recovery but it said wrong filesystem then when booting Ubuntu i wend down to Windows Vista Loader and it opened HP Recovery but said there was a problem can someone please help me? I want to get Windows 7 back with all HP Factory software installed

---

### Post by iLeet on 2010-05-01
BuMp

---

### Post by prodigy_ on 2010-05-01
Are you sure your recovery partition is intact? Maybe you deleted it? Use ```
sudo fdisk -l
``` in Ubuntu to get the list of all partitions.

---

### Post by iLeet on 2010-05-02
> cory@cory-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7cd1aca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       28714   230434816   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           28714       30402    13557760    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.


I can boot into it and I see HP Recovery window open up all it says though when i click recover is there was a problem recovering

---

### Post by itiswhatitis on 2010-05-02
You should have an option under recovery that says something like advanced.  There should be an option there restore your partition tables.  This will remove Ubuntu completely.

I have an HP, but when I installed Ubuntu I removed the recovery partition - so I can't reboot and look.

This HP Doc looks about right.  [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00809678&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00809678&product=18703)

---

### Post by iLeet on 2010-05-02
There was no advanced option unfortunately, I clicked System Recovery and i saw that it quickly went past reformatting the windows partition of your hard drive then failed.

---

### Post by iLeet on 2010-05-02
I saw this in the article

> Resolving a common recovery issue.
If the original operating system is changed to a non-Vista OS, the Recovery Manager cannot be launched from either the desktop or by pressing the f11 key on startup. You can use the recovery disc to restore the computer to the original operating condition in Vista. If using an non-Vista OS, you can use a third-party partition manager program to reclaim the hard drive space.

Can someone help me out with this?

---

### Post by itiswhatitis on 2010-05-02
This is the recovery document for your laptop.

[http://h10010.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=3768344&docname=c00814731](http://h10010.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=3768344&docname=c00814731)

The picture shows button labeled **Advanced Options** on the bottom left side.

---

### Post by iLeet on 2010-05-02
that is not what my Recovery Manager Looks like though its black with more options on the first page but no advanced im also using Windows 7 thats why the interface may be different

---

### Post by itiswhatitis on 2010-05-02
If you have the recovery CD/DVD I'd suggest booting to that.

Calling HP support might get you some extra options as well.  You are certainly not the first person to run into this issue.

---

### Post by iLeet on 2010-05-02
yeah it didnt come with a CD but formatting the partition to NTFS Would that help?

> Resolving a common recovery issue.
If the original operating system is changed to a non-Vista OS, the Recovery Manager cannot be launched from either the desktop or by pressing the f11 key on startup. You can use the recovery disc to restore the computer to the original operating condition in Vista. If using an non-Vista OS, you can use a third-party partition manager program to reclaim the hard drive space

---

### Post by itiswhatitis on 2010-05-02
Yeah, HP does not send the discs anymore.  When you first start the computers up, it prompts you to make them.  If you don't and can't use the F11 option, then you have to call HP and sweet talk them into sending you discs. or... locate a 3rd party tool that can fix your partitions.

---

### Post by iLeet on 2010-05-02
> **itiswhatitis said:**
> Yeah, HP does not send the discs anymore.  When you first start the computers up, it prompts you to make them.  If you don't and can't use the F11 option, then you have to call HP and sweet talk them into sending you discs. or... locate a 3rd party tool that can fix your partitions.

So If I have a tool to fix my partitions what would I do format the partition to NTFS?

---

### Post by itiswhatitis on 2010-05-02
You would have to follow the tool's instructions.  It would probably want you to delete the partitions first then let you create a new one that is either NTFS or FAT.

---

### Post by iLeet on 2010-05-02
> **itiswhatitis said:**
> You would have to follow the tool's instructions.  It would probably want you to delete the partitions first then let you create a new one that is either NTFS or FAT.
then use recovery and it should work? It was NTFS before

---

### Post by itiswhatitis on 2010-05-02
If recovery recognizes the file system, then yes it should work.

---

### Post by iLeet on 2010-05-02
Thannks :p ill give it a try

---

### Post by iLeet on 2010-05-02
Well it didnt seem to work I just got GRUB Rescue im going to download a image of vista/7 or xp and just use it to install then recover

---

### Post by iLeet on 2010-05-05
didnt work someone please help

---

### Post by sevenX on 2010-05-05
Hey iLeet, I have an hp mini and had to order recovery discs from hp. I think all of they're products have a 1 year warranty so if your still in that time frame try giving them a call.  They were very good to deal with, it took a couple hours of being on hold and going from tech to tech who tried to help me with restoring it and after a few tests they mailed my restore to factory default discs and I got them about 4 business days later.  Now Im running win7 again on mini sadly... I have too for chart navigation program I use.  When they are running you through tests just say you can get into bios screen and thats it... when u try to boot its blinking cursor..  and after each test say same thing.. just blinking cursor ;) Hope its still warrantied.

---

### Post by oldfred on 2010-05-05
Do you want the possibly missing recovery partition or the windows install partition. To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by iLeet on 2010-05-06
> **sevenX said:**
> Hey iLeet, I have an hp mini and had to order recovery discs from hp. I think all of they're products have a 1 year warranty so if your still in that time frame try giving them a call.  They were very good to deal with, it took a couple hours of being on hold and going from tech to tech who tried to help me with restoring it and after a few tests they mailed my restore to factory default discs and I got them about 4 business days later.  Now Im running win7 again on mini sadly... I have too for chart navigation program I use.  When they are running you through tests just say you can get into bios screen and thats it... when u try to boot its blinking cursor..  and after each test say same thing.. just blinking cursor ;) Hope its still warrantied.

Yep its only 2 weeks old so ill give them a call and tell them what you said todo just out of curiosity what would they say if i said I used Ubuntu or Linux? and I would just buy the CD but shipping is over $35 and i cant choose other options

---

### Post by iLeet on 2010-05-06
> **oldfred said:**
> Do you want the possibly missing recovery partition or the windows install partition. To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

My results:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   461,279,231   460,869,632  83 Linux
/dev/sda3         461,279,232   488,394,751    27,115,520   7 HPFS/NTFS


---

### Post by oldfred on 2010-05-06
It looks like you did not post the entire boot script. Also post it in code tags (# on edit panel). 

You have two NTFS partitions. sda1 looks like a boot partition, was the current Linux on sda2 your original windows install or the recovery partition. sda3 then has another NTFS partition that looks more like a recovery partition since it does not have the rest of the windows boot -  /Windows/System32/winload.exe??

---

