---
title: "Cannot copy files to usb..weather root or not"
date: 2012-06-14
forum: General Help
---

### Post by Quiane on 2012-06-14
OKay, I've got a clean install of ubuntu 12.04..very little changed from when it was installed last week...kept up to date. 

When i try to copy from my home folder to a USB key i get 
"Error opening file '/media/usb0/The Subtle Knife - Pullman, Philip.epub': Permission denied"

(just a random file i pulled, but i tested a lot of differnt files...)

Then, when i sudo nautilus first i got "pleast ask your administrator to enable user sharing"..i did that ...but there is no real reason that samba is the issue here (i installed samba anyway because i do share folders over my network, but bla).  After doing that and restarting my nautilius session, i now get the following error in terminal...

** (nautilus:6068): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

SO, i haven't really found any reason why file transfering doesn't work.  It works in windows on the same computer (dual boot, seperate hard drives)..

Any idea what to google or what permissions to change.  Oh, when i right clicked my home folder in the sudo nautilus window, i made sure that i was the "owner" and ensured that all permissions were read & write, as well as create and delete..but it appears that the permission tab is changing it after i close it.  hmm...

Thanks!

---

### Post by cholericfun on 2012-06-14
You should have all permissions on your home folder,
how about the USB-drive, what are the permissions there?
(although they shouldn't be restricted...)

---

### Post by kanikilu on 2012-06-14
If the USB drive works in Windows, as you say, it's very likely formatted as either FAT32 or NTFS, so you're not going to be able to change the permissions.

NTFS read/write support should be included in Ubuntu, though, so I'm not really sure what the problem is...

With the drive plugged in, can you post the results of the **mount** and **sudo fdisk -l** commands?

Also, I know sometimes if a device is not ejected property, it will need to be either plugged back into a Windows machine and "safely removed", or mounted with the *force* option:

[https://help.ubuntu.com/community/Mount/USB#Unclean_LogFile](https://help.ubuntu.com/community/Mount/USB#Unclean_LogFile)

---

### Post by Quiane on 2012-06-14
> mark@Mark-Desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sde on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)


> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd865eb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   156246015    78121984    7  HPFS/NTFS/exFAT
/dev/sdb2       156246016   156248063        1024   83  Linux

Disk /dev/sde: 1471 MB, 1471904768 bytes
244 heads, 36 sectors/track, 327 cylinders, total 2874814 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde4   ?  4237352519  6515205033  1138926257+  a5  FreeBSD


I should also be clear that this is all usb drives, not just one.  The formatting is generally in fat32.  I can't firgure out what happened either..it's really strange..it seems like the permissions went haywire and now i just don't have a place to start to fix them.

Thanks for the replys guys.

---

### Post by kanikilu on 2012-06-14
This doesn't seem right:

> Disk /dev/sde: 1471 MB, 1471904768 bytes
244 heads, 36 sectors/track, 327 cylinders, total 2874814 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sde4 ? 4237352519 6515205033 1138926257+ a5 FreeBSD

Can you post the contents of /etc/fstab?

---

### Post by Quiane on 2012-06-14
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e36430f7-36cb-4d4c-a9df-174732d0fb80 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=58611cce-65b9-41ff-aa1f-bbbe69c2acf0 none            swap    sw              0       0

i had to repair the grub menu due to the dual boot..i may have messed that up... (but i dont think so..the 2 seem unrelated, and my dual boot works fine)

---

### Post by kanikilu on 2012-06-14
Ok, nothing jumps out from fstab. I still don't think that warning from fdisk is normal. Do you still get the same "This doesn't look like a partition table. Probably you selected the wrong device." message if you plug in another USB flash drive? FWIW, this is what I get from an 8GB flash drive on my computer, formatted as NTFS:

> Disk /dev/sdc: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15240575     7616256    7  HPFS/NTFS/exFAT

---

### Post by Quiane on 2012-06-14
> mark@Mark-Desktop:~$ sudo fdisk -l
[sudo] password for mark: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd865eb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   156246015    78121984    7  HPFS/NTFS/exFAT
/dev/sdb2       156246016   156248063        1024   83  Linux

Disk /dev/sde: 3998 MB, 3998220288 bytes
123 heads, 62 sectors/track, 1024 cylinders, total 7809024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af870

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          62     7809023     3904481    c  W95 FAT32 (LBA)


that's the output with a different usb key, but i still get the same permission error..
thanks a lot for your input! :)

---

### Post by Quiane on 2012-06-14
i just had a re-read of this thread, and it appears i missed checking the permissions on the usb.  

Here is the screenshot:
[IMG]http://i.imgur.com/IakZJ.png[/IMG]

So...that should say "mark" right?  So, how do i change that system wide (because it's not just 1 usb key, it's all of them...)

When trying to change just the usb key that's plugged in this is the error i get

[IMG]http://i.imgur.com/ugsDF.png[/IMG]

---

### Post by Quiane on 2012-06-14
I fixed it! 

The problem was usbmount.  I went to synaptic and uninstalled it, restarted the computer and it works fine.

I found the solution on this thread [http://ubuntuforums.org/showthread.php?t=1484042&page=3](http://ubuntuforums.org/showthread.php?t=1484042&page=3)

Thanks a lot for everyone's help! Much appreciated!

---

