---
title: "Karmic Koala: Convert a single drive system to RAID"
date: 2010-02-10
forum: General Help
---

### Post by andreas99 on 2010-02-10
Hello World!

I am trying to convert my single drive system to a bootable Raid-1 system. But i got a few problems. 
First i looked at this guide: [http://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](http://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

My system disk is /dev/sda and i inserted a new disk /dev/sdb
This is how it looks
**I have no clue what sda3 is, maybe someone knows?**```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040408+  82  Linux swap / Solaris
/dev/sda3           29650       30401     6040440    5  Extended
```So i did as follow:

*To copy the first partition layout to second disk*
```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```*Change partition typ to "Linux raid autodetect"*```
fdisk /dev/sdb
t, 1 , fd, w
```*Create the single-disk RAID-1 array*```
mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb1
```*Make a ext4 filesystem on the new disk*```
mkfs.ext4 /dev/md0
```*Make a swap partition*```
mkswap /dev/sdb2
```*Mount the Raid-1 and copy all the data*```
mkdir /mnt/new-raid
mount /dev/md0 /mnt/new-raid
cd /mnt/new-raid
rsync -avH --delete --progress -x / /mnt/new-raid
```I then altered fstab:```
blkid
/dev/sda1: UUID="0b67d7c3-7e32-4f65-809a-7ebc4138a7bb" TYPE="ext4"
/dev/sda2: UUID="b33109b7-b76b-4bae-b1fd-6cab2a98eb35" TYPE="swap"
```I then changed the UUID in fstab using nano```
nano /etc/fstab
```So far so good. Now it comes to GRUB, this is where i think i'm having problems.
Chroot, and update GRUB```
mount --bind /sys /mnt/new-raid/sys
mount --bind /proc /mnt/new-raid/proc
mount --bind /dev /mnt/new-raid/dev
chroot /mnt/new-raid/
mdadm --detail --scan >> /etc/mdadm/mdadm.conf 
update-initramfs -k `uname -r` -c -t

update-grub2 /dev/sdb
```I then shutdown my computer and removed /dev/sda. Changed my BIOS to boot from my new disk.
GRUB started to load, and i could see the Ubuntu logo started. And then it said something about not finding /dev/md0 and some other stuff?

What am i doing wrong?

---

