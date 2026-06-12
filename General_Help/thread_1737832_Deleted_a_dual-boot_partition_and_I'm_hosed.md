---
title: "Deleted a dual-boot partition and I'm hosed"
date: 2011-04-23
forum: General Help
---

### Post by noshoesnoshirt on 2011-04-23
I searched the threads and found several likely solutions, but no luck yet,
So I deleted the Ubuntu partition on my old Dell work lappy (WinXP  Ubuntu 10.04) and now the boot menu says: "error: no such partition grub  rescue".
  I went through the directions here
   [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
  but I don't see any Linux partitions on the list.
  See a screenshot of my drives here;
  [http://i.imgur.com/ckwN0.png.](http://i.imgur.com/ckwN0.png.)
  I'm at a bit of a loss, and it's my *** if I have to send it to the corporate geeks.
Any help would be greatly appreciated


edit; went throught the mkdir, mount process again with what I assumed was my drive and when I got to the grub install step I got an error mesage; "error: bad boot flag"

---

### Post by b0b138 on 2011-04-23
Simply put, grub has two parts. One part thats in the mbr, and the other are files on the linux partition.  You deleted your linux partition, so the files are gone.

You need to boot to an xp disk, go into the recovery console (i think thats what its called) and restore the windows bootloader with the fixmbr command.

---

### Post by kiyop on 2011-04-23
Grub is separated into two part. One is a kind of boot loader which reads the second part, and is installed on MBR (Master Boot Record) or PBR (Partition Boot Record).
The second part is located in /boot/grub directory (folder) in a partition usually.
Grub cannot boot (work) correctly without the second part.
You deleted the partition containing the second part.

You can recover Windows XP by many ways.

One is to use "Windows Installer Disc(CD or DVD)" and enter into recovery console and execute:
```
fixmbr
```Refer [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

2nd way is to install lilo into MBR.
Boot with Ubuntu live CD or USB and open terminal, like
"Application" -> "Accessory" -> "Terminal"
Connect internet cable and type:
```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```You can install [MBM (excuse my linking Japanese Page)]("http://wikiwiki.jp/disklessfun/?mbm") or so.

Edit:

I looked [http://i.imgur.com/ckwN0.png](http://i.imgur.com/ckwN0.png).
I think the information on /dev/sda5 is strange
> 255 heads, 63 sectors/track, 4864 cylinders
...
/dev/sda5  ?   114480   162538  386025298+ ef EFI (FAT-12/16/32)I am not familiar with such information.
Does this HDD have errors?

---

### Post by noshoesnoshirt on 2011-04-23
Your solution worked gracefully, kiyop, I am indebted to you. Thank you very much.
edit; I used solution #2

---

