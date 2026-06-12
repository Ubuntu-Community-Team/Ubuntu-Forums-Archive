---
title: "help I've broken my partitions"
date: 2010-11-03
forum: General Help
---

### Post by Thestinger on 2010-11-03
I'm an idiot and decide to hit the create new partition table button in Gparted.

I used Test Disk and seem to have managed to get back my main xp partition. I still cannot boot though other and can only use the computer with the live CD.

Can anyone help- Test disk finds all my old partitions but seems to only want to let me have one of them bootable.

estDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1   514 254 63    8273412 [PRESARIO_RP]
D HPFS - NTFS            514 210  1 14238 254 63  220478895 [PRESARIO]
L Linux                14238  31  1 19237 254 63   80323047
D Linux Swap           19237 166  1 19456 254 63    3523842








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 1804 MB / 1720 MiB


This what it says at the moment

Can anyone help I was running 10.1 and xp on dual boot
athlon 3400   1.5 GBRam 160 GB HD

My live cd is 10.04

Oh and I have clearly shown I know nothing so if you can help assume no knowledge

---

### Post by alphaamanitin on 2010-11-03
Dont worry too much, I did basically the exact same thing recently while in a hurry to reformat a USB drive for my girlfriend. If you have rebuilt your Windows XP partition with TestDisk, just like I did, then you have lost the Windows XP MBR (master boot record).  If you have a handy Windows XP operating system disk handy you can use that and follow the instructions from microsoft:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

If you do not, go get yourself a copy of the amazing SuperGrub:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It and TestDisk are things that everyone should have.  Anyway, I used it to rebuild my XP MBR and now my computer works perfectly fine.  I find it a little awkward to do and can't really describe how to do it (confession I just screw around with it until I get it to work:)).  But there should be some good tutorials online on how to use it.

AlphaA

---

### Post by Thestinger on 2010-11-03
Thanks for that.

Will it help me get back the recovery partition or will i have to live without that- its an OEM version on my mums old computer so i have no system disk

---

### Post by alphaamanitin on 2010-11-03
No I think you will have to try to rebuild the old partition table with TestDisk.  Did you make up the entire drive before working on it?  I think you might have damaged you chances by restoring the XP volume, most likely what you should have done first was try to rebuild the entire drives partition table, which I believe testdisk can do.  If I were you I would clone the hard drive onto another drive and work on that.  Then I would try to use testdisk to rebuild the original partition table.  If that didn't work I about probably just try to recover all my files with testdisk.  I recovered my XP system after deleting the partition and reformatting to FAT32 with testdisk.  

Use the supergrub to try and restore your boot loaders after recovering the partitions. 

Anyway, here is what the TestDisk website has to say about losing all partitions:

> **Disk geometry problem - When all partitions are deleted **

 In this case, all partitions have been deleted. TestDisk shows no partition! The user has run **testdisk /debug /log**. Extract of testdisk.log 
 Analyse Disk /dev/hdb - CHS 5169 240 63 - 38161 MB
No partition is bootable
search_part()
Disk /dev/hdb - CHS 5169 240 63 - 38161 MB
FAT32 at 0/1/1
heads/cylinder 255 (FAT) != 240 (HD)
A FAT32 partition has been found but there is a warning about hard disk geometry. The BIOS has selected another hard disk geometry because of the content of the MBR (empty in this case). Under TestDisk, choose geometry, set the number of heads to 255 instead of 240 and run Analyse again. 


Alternatively, you could email the creator and ask him.  I did and he responded.  Seemed to be very nice.

AlphaA

---

