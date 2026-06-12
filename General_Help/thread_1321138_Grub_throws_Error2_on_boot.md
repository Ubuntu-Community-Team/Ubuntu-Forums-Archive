---
title: "Grub throws Error:2 on boot"
date: 2009-11-09
forum: General Help
---

### Post by SamD42 on 2009-11-09
Upon restart recently the computer gets through to grub which then throws an error 2. I can't think why the sudden change, all was working perfectly until recently.

Trying to setup grub again the usual way using a live cd:

Having mounted sda1 (partition with / on it)
 
[I]sudo grub
find /boot/grub/stage1[/I]

Returns no file found. Upon inspection /boot/grub doesn't appear to actually have a stage1 file. Knowing root is on /dev/sda1, I opened a terminal and tried to run grub-install.

[I]sudo mkdir /media/sda1 
sudo mount /dev/sda1 /media/sda1

sudo mount --bind /dev /media/sda1/dev
sudo chroot /media/sda1

sudo grub-install /dev/sda[/I]

gives /boot/grub/device.map stale NFS file handle
/dev/sda does not have any corresponding bios drive

fstab shows:

[I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=80707297-fe0f-4d59-91c8-d327f5368c87 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a321d69d-08cb-4894-8804-312fbb08e282 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=57c72f0d-1361-421c-bb2b-c3f54ecf0129 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/I]

I'm completely stuck, any ideas anyone has on the issue would be much appreciated!

---

### Post by SamD42 on 2009-11-10
Update:

The issue appears to have been the fact it was reporting 'stale nfs file handle'. Running fsck -f from a livecd on the affected partition found around twenty to thirty files with errors. Gnome now no longer throws an error two, and instead goes to an error 15, due to the fact that most of the files that were affected now no longer exist!

The plan is to do a bit of repair work, or just reinstall / if the damage appears to have been too extensive.

If anyone knows a better way this could have been handled, or even why it might have happened in the first place I'd be very much interested to know!

---

