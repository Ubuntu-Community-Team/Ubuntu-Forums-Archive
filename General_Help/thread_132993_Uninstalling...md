---
title: "Uninstalling.."
date: 2006-02-19
forum: General Help
---

### Post by netoster on 2006-02-19
Im getting a new hard disk and i would like to uninstall ubuntu from this one, is there a safe way to do it so the boot manager wont screw up everything?

Help please

---

### Post by Robgould on 2006-02-19
Do you dual boot with windows?

---

### Post by netoster on 2006-02-20
yes i dual boot w/ Windows XP Sp2

Update: I deleted Linux partitions with PartitionMagic (secure delete)...Grub wont start..i had to make a disk (ntldr?) so i can boot up windows..now im floppy dependant..help plz

---

### Post by Robgould on 2006-02-20
you need to repair your master boot record.  When you deleted your partition you confused grub.  Grus installs to your mbr by default.  
 
To repair your mbr
 
Use you windows install cd to boot windows in rescue mode.
 
Once at the prompt, type fixmbr
 
it will ask are you sure...say yes
 
 
then when you get to the promot again type exit
 
Your computer will reboot.   Should boot to windows fine now.
 
As a side note, the procedure is what I do every time.  Use Partition magic to remove partition (Actually windows XP can do this natively), then do fixmbr.  Ready to go.

---

### Post by cotcot on 2006-02-20
The disk partitioner of the ubuntu install can help you. If you choose manual partitioning you can make the ubuntu root and swap partition on your new drive (i guess you will install this as slave). The old one will have free space (because you deleted the ubuntu partition). The disk partitioner of the install allows you to resize it or to add another one for instance a FAT or better a ext2 for shared files between XP and ubuntu. Therefore you have to install de ext2 driver ([www.fs-driver.org](www.fs-driver.org)) in XP.
At the end of the install the grub loader will be installed to the location you want. If you allow installing it in the MBR (of your XP disk) you wil get rid of your floppy.

---

