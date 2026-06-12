---
title: "grub problem"
date: 2011-09-28
forum: General Help
---

### Post by utkarshjadhav on 2011-09-28
I am currently using both windows 7 &  ubuntu 10.04
I have installed ubuntu using manually partitioning.and now I want to uninstall ubuntu.
Through windows if I delete all partitions of ubuntu,would that cause grub loss?
if so -Are there any grub loader options which ultimately will  rescue windows?

---

### Post by garvinrick4 on 2011-09-28
> **utkarshjadhav said:**
> I am currently using both windows 7 &  ubuntu 10.04
I have installed ubuntu using manually partitioning.and now I want to uninstall ubuntu.
Through windows if I delete all partitions of ubuntu,would that cause grub loss?
if so -Are there any grub loader options which ultimately will  rescue windows?
Yes you are booting off of Ubuntu install with grub2 bootloader. When Ubuntu removed
have to install Windows bootloader with windows disks/recovery disk. Just a couple of
commands. 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
#If you do not have a windows disk use ubuntu live cd with internet connection
open a terminal and copy and paste will boot windows only.
#Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Reboot and have a bootloader named lilo capable of booting windows.

---

### Post by utkarshjadhav on 2011-10-15
thanks [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") .
did with recovery disk.

---

### Post by garvinrick4 on 2011-10-15
> **utkarshjadhav said:**
> thanks [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") .
did with recovery disk.
Wow two weeks later glad you are up and working.

---

