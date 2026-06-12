---
title: "ubuntu notebook edition"
date: 2010-05-27
forum: General Help
---

### Post by Drenriza on 2010-05-27
i have just installed ubuntu notebook 10.04 edition instead of the desktop edition that i had.

but at the left side bar, under files and folders. I cannot see my sda1 anywhere, or my cd-rom drive, home, network drives, and so on.

How can i get these visable? is their some feature somewhere i need to activate or something.

Kind Regards

---

### Post by Drenriza on 2010-05-28
bump

---

### Post by mikewhatever on 2010-05-28
Please post the output of the following:

sudo fdisk -l

cat /etc/fstab

---

### Post by Drenriza on 2010-05-28
cristian@cristian-laptop:~$ sudo fdisk -l
[sudo] password for cristian: 

Disk /dev/sda: 200.0 Gb, 200049647616 byte
255 heads, 63 sectors/track, 24321 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c97cd

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1   *           1       24073   193358848   83  Linux
/dev/sda2           24073       24322     2000896   82  Linux swap / Solaris
cristian@cristian-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

---

### Post by mikewhatever on 2010-05-28
Let me backtrack a little and ask, did you reinstall or just added the netbook edition packages?

---

### Post by Drenriza on 2010-05-28
clean install

---

### Post by mikewhatever on 2010-05-28
Right, so let's sea, sda1 is your root partition, it's mounted at boot and is not supposed to show as sda1 in the left panel. To put it another way, all of the files are on sda1, including the home folder and all of the system files. The network drivers are not visible because home network is not installed by default. You'll need to install and configure it again. Cdrom is a mystery to me. There is usually a line for it in fstab, not sure why your's have none.

---

