---
title: "Recover Lost Partitions"
date: 2010-07-10
forum: General Help
---

### Post by asifisbest on 2010-07-10
I installed UBUNTU alongside Windows XP in dual boot mode.But I removed XServer in UBUNTU and restarted.The UBUNTU didn't start in graphical mode.Then I started Windows XP and tried to delete the partition in which the UBUNTU was installed and some how the other partitions got deleted in which all my important data resides.The partitions which I didn't even touch got deleted alongside the UBUNTU partition.Then I reatarted PC.Now even GRUB loader wont show up.What should I do?.I am currently using UBUNTU Live CD to browse the internet.I want my partitions back.PLEASE HELP!

---

### Post by ronnielsen1 on 2010-07-10
[http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/](http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/)

Puppy unlimited has testdisk and photorec which are good for this purpose. The hirens boot cd is also great

[http://www.hirensbootcd.net/cd-contents/136-hbcd-106.html](http://www.hirensbootcd.net/cd-contents/136-hbcd-106.html)

> **Recovery Tools**

 - Partition Find and Mount 2.31: Partition Find and Mount software is  designed to find lost or deleted partitions (Windows Freeware).
- PhotoRec 6.12b: Tool to Recover File and pictures from  Dos/Windows/Linux (Windows/Dos Freeware).
- PartitionRecovery 1.0: A freeware tool to recover accidentally deleted  partitions (Windows Freeware).
- Recuva 1.37.488: Restore deleted files from Hard Drive, Digital Camera  Memory Card, usb mp3 player... (Windows Freeware).
- Restoration 3.2.13: a tool to recover deleted files (Windows  Freeware).
- Smart Partition Recovery 3.3: Find Lost NTFS partitions and restore  them back. (Windows Freeware).
- SoftPerfect File Recovery 1.2: to restore accidentally deleted files  from hard drive, USB flash drives, CF and SD memory cards (Windows  Freeware).
- TestDisk 6.12b: Tool to check and undelete partition from  Dos/Windows/Linux (Windows/Dos Freeware).
- Unstoppable Copier 4.4: Allows you to copy files from disks with  problems such as bad sectors, scratches or that just give errors when  reading data. (Windows Freeware).
- Active Undelete 5.5: a tool to recover deleted files (Windows  Commercial).
- Active Partition Recovery 3.0: To Recover a Deleted partition. (Dos  Commercial).
- DiyDataRecovery Diskpatch 2.1.100: An excellent data recovery  software. (Dos Commercial).
- GetDataBack for FAT/NTFS 4.0: Data recovery software for FAT/NTFS file  systems (Windows Commercial).
- Prosoft Media Tools 5.0 v1.1.2.64: Another excellent data recovery  software with many other options. (Dos Commercial). 

---

### Post by jingaling on 2010-07-10
Hi Asif and welcome to the community!

If i where you I would create an hirens boot CD (you can download it from [HERE]("http://www.hirensbootcd.net/download.html").

Once you have downloaded and written the iso to a CD boot from it and run the CD (boot into the DOS programs part of the CD) then select the recovery tools menu. Under that there a numerous tools that can be used to recover lost or deleted partitions Partition Recovery and Partition find and mount are about the best of the bunch.

Just a quick foot note as well (although this wont help you much now) make a full backup image of your drive before fiddling around with the Partition Table especially if you don't know exactly what you are doing. There are also tools to create image level backups on the Hirens boot CD (just run a bkup to an external USB hard drive or secondary drive).

Hope this helps!

Jing

---

### Post by ronnielsen1 on 2010-07-10
If you're using this computer, don't write anything new to the hard drive until you run test disk to recover the lost partitions

---

### Post by vangop on 2010-07-10
I can recommend [http://www.sysresccd.org/]("http://www.sysresccd.org/System-tools")
This is a system rescue CD full of recovery stuff.
Check their page.
Just make sure that you don't repartition the drive, until then the data is not lost and you can recover the partition. So don't use "create partition" tools, use "recover" ones.
Agree with ronnielsen1 - use test disk (included in this recovery disk)
Here's a good guide on usage [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by asifisbest on 2010-07-10
Hey guys.First of all I want to uninstall GRUB so that i can boot up Windows XP and try testdisk.what should i do to uninstall GRUB?I mean i need to boot into WINDOWS XP whose partition wasn't deleted.Here is what I have.

C:WIndows XP 40GB
D:Windows XP 70 GB
E:DATA 123GB (This dive got disappeared by itself.It has all my data.I want this partition to be as before)
F:Unformated Drive unknown size(actually i cant remember its size)
UBUNTU Drive:19GB (This was the drive which i deleted)
UBUNTU SWAP:927MB (This got deleted when i deleted UBUNTU Drive)

---

### Post by ronnielsen1 on 2010-07-10
> First of all I want to uninstall GRUB so that i can boot up Windows XP  and try testdisk.

It would me simpler to run one of the live cd's that are linked to. You can't run testdisk on partitions that you're using.

---

### Post by asifisbest on 2010-07-10
[i cannot understand ronnielsen1's post.]("http://ubuntuforums.org/member.php?u=61926")
what i need to do to boot into windows XP?
the drives containing Windows Xp are intact.

---

### Post by d0m1n1qu3 on 2010-07-10
or repair your windows from the windows setup disk!! That's all!
 
I was wondering how could u come to know about your partitions if u can't boot!! Your partitions are probably fine. Just insert the bootable windows CD and repair your windows, and ur PC will come bak!
 
And thanx for disturbin me. I was at the highest point of interest, watching porn!!

---

### Post by vangop on 2010-07-10
> **asifisbest said:**
> Hey guys.First of all I want to uninstall GRUB so that i can boot up Windows XP and try testdisk.what should i do to uninstall GRUB?I mean i need to boot into WINDOWS XP whose partition wasn't deleted.Here is what I have.

C:WIndows XP 40GB
D:Windows XP 70 GB
E:DATA 123GB (This dive got disappeared by itself.It has all my data.I want this partition to be as before)
F:Unformated Drive unknown size(actually i cant remember its size)
UBUNTU Drive:19GB (This was the drive which i deleted)
UBUNTU SWAP:927MB (This got deleted when i deleted UBUNTU Drive)
You don't need to boot windows to run testdisk. 
Download the rescue cd, burn it and boot from it.
OR simpler boot from ubuntu liveCD and install testdisk
```
sudo apt-get install testdisk
```

Run testdisk and allow it to repair your lost partition.

To remove grub (you won't be able to boot ubuntu!!!) boot from the windows install CD, follow the prompts to open a recovery console and type
```
fixmbr
```

to fix your grub follow
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
You'll be able to boot both win and ubuntu

---

### Post by jingaling on 2010-07-10
> **d0m1n1qu3 said:**
> or repair your windows from the windows setup disk!! That's all!
 
I was wondering how could u come to know about your partitions if u can't boot!! Your partitions are probably fine. Just insert the bootable windows CD and repair your windows, and ur PC will come bak!
 
And thanx for disturbin me. I was at the highest point of interest, watching porn!!

I totally agree with what d0m1n1qu3 says if you have a C: and D: then your partitions are fine, otherwise they wouldn't have a drive letter. You run a windows repair from the Win XP disk this should repair the MBR (master boot record) and you should be able to boot into windows.

Failing that you could format the ubuntu partitions, install an OS on that drive space then browse the NTFS (windows) partitions and get your data back. Once you have your data back you can completely format the mess that is currently your hard drive and start over.

---

