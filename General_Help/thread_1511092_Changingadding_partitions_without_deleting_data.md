---
title: "Changing/adding partitions without deleting data?"
date: 2010-06-16
forum: General Help
---

### Post by JustSteph on 2010-06-16
Hi

I have a 160GB hard drive and have 137GB dedicated to Windows XP, and I installed Ubuntu on the random 22Gb that Windows left. I'd like to make the Ubuntu partition bigger, and the Windows one smaller, and add a partition for data storage. Can I do this without deleting everything on the hard drive?

Thanks
Steph

---

### Post by oldfred on 2010-06-16
Yes, but as with anything related to repartitioning there is some risk and you need to have backups. Often the biggest risk is the user. I created several new partitions and installed to the wrong one, but fortunately did not lose any data.

Of course if your hard drive is full is may not be possible or if nearly full it may be difficult.

With XP you can use gparted to shrink your XP partition (use windows tools for Vista/7). Some say you do not even have to defrag but I defrag normally on a regular basis.  You do need to leave 20-30% free space in windows for it to keep working.

If you want to share the data with XP you should put the data in a NTFS partition, otherwise any linux ext3 or ext4 partition will be better. I have  some data in NTFS and now most in /data ext3 partition.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Oldfred - Converting to data partition
[http://ubuntuforums.org/showthread.php?p=9074762](http://ubuntuforums.org/showthread.php?p=9074762)

---

### Post by K.J. on 2010-06-16
> **oldfred said:**
> Yes, but as with anything related to repartitioning there is some risk and you need to have backups. Often the biggest risk is the user. I created several new partitions and installed to the wrong one, but fortunately did not lose any data.

Of course if your hard drive is full is may not be possible or if nearly full it may be difficult.

With XP you can use gparted to shrink your XP partition (use windows tools for Vista/7). Some say you do not even have to defrag but I defrag normally on a regular basis.  You do need to leave 20-30% free space in windows for it to keep working.

If you want to share the data with XP you should put the data in a NTFS partition, otherwise any linux ext3 or ext4 partition will be better. I have  some data in NTFS and now most in /data ext3 partition.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Oldfred - Converting to data partition
[http://ubuntuforums.org/showthread.php?p=9074762](http://ubuntuforums.org/showthread.php?p=9074762)

The gparted live cd is a lovely tool.  Defragging does make the resize more likely to be successful.  However, the first thing you should do is disable swap/virtual memory in XP since it creates an unmovable file.

---

### Post by JustSteph on 2010-06-18
I deleted the Windows partition and just reinstalled XP on 45Gb worth of space, but now it doesn't show the boot menu when I turn my laptop on, it just automatically loads XP. I've checked and Ubuntu is definitely still installed (I booted from the Ubuntu disc and it showed it), but in the startup options in Control Panel on XP, it only shows XP. How can I fix this?

---

### Post by jerome1232 on 2010-06-18
You'll need to use an Ubuntu live cd to reinstall grub (Windows just assumes it's the only bad boy on your computer and nukes the mbr for ya)


I think you can just run grub-install from a live cd but I haven't gotten current with all the new grub2 stuff so it may differ.

I did find some info about grub2 in ubuntu docs

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2010-06-18
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)


the short version is this, but occasionly you have to use the full chroot verison in above links.

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by JustSteph on 2010-06-18
It worked! Thank you.

---

