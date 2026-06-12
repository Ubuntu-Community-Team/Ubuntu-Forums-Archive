---
title: "Editing fstab - added swap partition"
date: 2010-05-09
forum: General Help
---

### Post by UKseagull on 2010-05-09
Can anyone help me understand just what to do please? 
I have UNR 9.10 installed on an O2 Joggler and am making use of the extra space on a USB HDD, I'm having difficulty understanding what's to be done is section 4b in the post linked below.  I've added a swap partition to the drive and need to edit the fstab accordingly.

I'm following instructions [here ]("http://www.joggler.info/forum/viewtopic.php?f=33&t=465&start=20#p5435")

The instructions:-
> Step 4b - copy the line with "swap" in it, the line starts with a hash  (#) character which means Linux is currently ignoring that line.  Paste  the same line below the line that starts /dev/sda2, change the first  field (the first field is all characters before the first space) of the  line you just pasted to read /dev/sda3.My fstab currently looks like this:-
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
/dev/sda2    /                   ext2    noatime,errors=remount-ro 0       0
/dev/mmcblk0p2    /media/mmcblk0p2    auto    noauto    0    0
/dev/mmcblk0p3  /media/mmcblk0p3        auto    noauto  0       0
/dev/mmcblk0p4  /media/mmcblk0p4        auto    noauto  0       0
# swap was on /dev/sda5 during installation
#UUID=c0f30c05-7e47-4986-b301-155ea0fa33c2 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


This is the line that I'm supposed to copy and paste, I just can't get my head round what the line is meant to look like after doing as the instructions say.
> # swap was on /dev/sda5 during installation

---

