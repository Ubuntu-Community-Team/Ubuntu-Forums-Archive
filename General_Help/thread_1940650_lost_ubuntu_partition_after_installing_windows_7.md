---
title: "lost ubuntu partition after installing windows 7"
date: 2012-03-14
forum: General Help
---

### Post by nsakiotis on 2012-03-14
Hi
I had an 70GB ubuntu partition and I installed windows 7 on the rest odf the disk.
After the installation the ubuntu partition seemed deleted, I used a live cd and gparted showed that parttion as unallocated space.
I found here an old thread saying about TestDisk and how I could copy my lost data.
I followed the instruction, installed TestDisk and found my lost ubuntu partition. 
The problem is my files where very large and could not be copeid.
I tried to fix the partition table with that tool, although the instruction where not very clear.
After analyzing with TestData the partition table was like this: 

> TestDisk 6.14-WIP, Data Recovery Utility, March 2012
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0   1  1 51559 254 63  828311337
 P Linux                51559 192 26 58713   7 46  114917376
 P Linux Swap           58713  40 16 59234 240 14    8382464
 P Linux Swap           59235  50 16 59756 250 14    8382464
 P Linux Swap           59757  60 16 60279   5 14    8382464
 L Linux Swap           60279  70 16 60801  47 46    8384512I thought tha the correct structure would be like that, so I changed it that way:

> 

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>P HPFS - NTFS              0   1  1 51559 254 63  828311337
 * Linux                51559 192 26 58713   7 46  114917376
 P Linux Swap           58713  40 16 59234 240 14    8382464
 P Linux Swap           59235  50 16 59756 250 14    8382464
 P Linux Swap           59757  60 16 60279   5 14    8382464
 L Linux Swap           60279  70 16 60801  47 46    8384512

I then removed the live cd and rebooted, the system found no OS, so I logged in again with live cd
I ran TestDisk again and unforunately my partition table looks like this now 

> 
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>D HPFS - NTFS              0   1  1 51559 254 63  828311337
 D Linux                51559 192 26 58713   7 46  114917376
 * Linux Swap           58713  40 16 59234 240 14    8382464
 P Linux Swap           59235  50 16 59756 250 14    8382464
 P Linux Swap           59757  60 16 60279   5 14    8382464
 L Linux Swap           60279  70 16 60801  47 46    8384512
I tried to change it like it was before , but testdisk wont let me, it says it has a bad structure.

Please help!!

---

### Post by cottfcfan on 2012-03-14
It may just be that windows has overwritten the mbr, and doesn't recognize your Ubuntu partition.
It could just be a case of writing grub2 to the mbr using your ubuntu livecd.
Instructions are here:
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)
But before you do that more info would probably help.
What version of ubuntu are you using?
Even a copy of your partition setup using gparted.

---

### Post by nsakiotis on 2012-03-14
what's really frightening is that with "p" I can still browse my lost ubuntu partition and find all my data.
But after the last (bad) change that isnt happening with the windows 7 partition!!!!
After pressing p on it, I get  "File system seems to be damaged"!!!
:confused:

i also ran gparted and all of my space ,excpet the linux swaps, is marked as unallocated !!

---

### Post by cottfcfan on 2012-03-14
Windows will call anything damaged that isn't 100% windows.
I wouldn't worry about that yet. My Windows 7 cried when I 1st put Ubuntu on it, but ive had no problems since.

---

### Post by nsakiotis on 2012-03-14
> **cottfcfan said:**
> Windows will call anything damaged that isn't 100% windows.
I wouldn't worry about that yet. My Windows 7 cried when I 1st put Ubuntu on it, but ive had no problems since.
teh fact is that the results of gparted i said about is from ubuntu live cd! I am runinng on 11.10

---

### Post by rng on 2012-03-14
You can use dd or dd_rescue to bakup the damaged disk to a file on an external harddisk.  Then even if there is further damage you will still have a bakup to work with. Photorec is also useful in many cases.

---

### Post by nsakiotis on 2012-03-14
> **rng said:**
> You can use dd or dd_rescue to bakup the damaged disk to a file on an external harddisk.  Then even if there is further damage you will still have a bakup to work with. Photorec is also useful in many cases.

i will try photorec.
you can look in this old thread, it may be helpful for proposing me another solution
[http://ubuntuforums.org/showthread.php?t=1154829]("http://ubuntuforums.org/showthread.php?t=1154829")

---

### Post by cottfcfan on 2012-03-14
You could also try repairing your partition table by using the fdisk command.
From the live cd, use gparted to unmount all partitions, then in a terminal:
```
sudo fdisk /dev/sda
```
Check the output and if all looks correct, press p, then press w and this writes your partition table to disk.
Reboot and see if that helps.
As has been mentioned though try copying all your data somewhere else 1st if possible.

ps. This solved my problem when gparted showed some of my partitions as unallocated.

---

### Post by nsakiotis on 2012-03-14
> **cottfcfan said:**
> You could also try repairing your partition table by using the fdisk command.
From the live cd, use gparted to unmount all partitions, then in a terminal:
```
sudo fdisk /dev/sda
```Check the output and if all looks correct, press p, then press w and this writes your partition table to disk.
Reboot and see if that helps.
As has been mentioned though try copying all your data somewhere else 1st if possible.

ps. This solved my problem when gparted showed some of my partitions as unallocated.
unfortunately it doesn't look correct, it's exactlye like in TestDisk before analyzing

---

### Post by cottfcfan on 2012-03-14
Before you go any further could you take a screenshot of your partition table using gparted, and post it here?

---

