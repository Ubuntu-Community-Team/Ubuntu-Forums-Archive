---
title: "SATA disk - root password required"
date: 2009-08-10
forum: General Help
---

### Post by whisp71 on 2009-08-10
After each logon it is necessary to enter root password once to get access to SATA HDD. How to disable this? (it messes up torrent downloads)
 
 (couldn't find answer here or on google, sorry).

---

### Post by michy99 on 2009-08-10
Do you have a line in fstab to mount the disk automatically at login?

---

### Post by whisp71 on 2009-08-10
/etc/fstab?
No, it contains only ubuntu partition and swap one.

---

### Post by michy99 on 2009-08-10
So I'm guessing this is a NTFS partition. Have a look at this page for a good way to deal with it:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by whisp71 on 2009-08-11
Thanks, but i don't want to install soft for configuring something simple like that.

After googling fstab:
i need to set ownership to my user when mounting ntfs partitions, then they will open without root pass, is that right? (i jast want to make sure before editing fstab to not screw things up)

---

### Post by whisp71 on 2009-08-11
[SOLVED] by editing fstab

---

### Post by VCoolio on 2009-08-11
Post your fstab line in case someone reads this trying to achieve the same. I guess it's something like
/dev/something /mountpoint ntfs-3g defaults,user 0 0

first part is location of the disk in /dev (or the uuid or the label), second is the mount point, usually in /media, third is the format type, here ntfs or ntfs-3g, then defaults and, most important, the user part to enable user to mount the disk (without a space between). Then 0 twice for some reason.

---

### Post by whisp71 on 2009-08-11
[SIZE=3][COLOR=lime]Solution[/COLOR][/SIZE]

1) ```
sudo fdisk -l
```and remember names of partitions needed (like /dev/sdc1 etc)

2) ```
umount /dev/sdc1
```this will unmount them and remove folders from /media (important!)

3) ```
sudo mkdir /media/MyStuff
```"MyStuff" is the name which will appear in Places in your file manager

4) ```
sudo kate /etc/fstab
```replace kate with your text editor, add at the end of file:

```
/dev/sdc1       /media/MyStuff    auto    rw 0 0
```After next reboot you won't need to enter root pass for first access to this partition.

---

