---
title: "Can't see harddrives (USB and SATA)"
date: 2010-04-23
forum: General Help
---

### Post by rzmnz on 2010-04-23
Hi!

I've tried to search for a sollution for my problem, but I can't find it. Bet it's just me that can't find it.

My problem is that both my sata and usb harddrive has diseappeared from the file manager and /etc/fstab.
I'm using Gnome and 9.10.
I was able to see and use them until about an hour ago, when both of them disappeared. I tried to shut down and restart my usb hdd, but nothing happened. Tried to restart the computer too, but no luck there either.

I can see both of them when I do "sudo fdisk -l"
but not when I "gedit /etc/fstab"


Here is what fdisk says:
> rzmnz@rzmnz-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x000a3452

    Enhet Start     Början        ****     Block    Id  System
/dev/sda1   *           1        1867    14996646   83  Linux
/dev/sda2            1868       19457   141291675    5  Utökad
/dev/sda5            1868       18727   135427918+  83  Linux
/dev/sda6           18728       19457     5863693+  82  Linux växling / Solaris

Disk /dev/sdb: 320,1 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x23ef23ee

    Enhet Start     Början        ****     Block    Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 slutar inte på cylindergräns.
/dev/sdb2              13       38914   312466432    7  HPFS/NTFS
Partition 2 slutar inte på cylindergräns.

Disk /dev/sdc: 250,1 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x12345678

    Enhet Start     Början        ****     Block    Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS


And here is how my /etc/fstab looks like:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=076ce33e-8fd9-4efa-af8b-d635d1379349 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=13f46fca-8275-462d-b21f-b23d6b33740d /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ed79ef85-8c9e-4988-bad4-3aaeab821d3d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Also just noticed that when I gedit /etc/fstab this message pops up in the terminal before gedit starts:
> (gedit:2325): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: *Fel vid öppning av katalogen* "/usr/share/gvfs/remote-volume-monitors": *Filen eller katalogen finns inte*


Sorry for the swedish language in my post... Was supposed to install ubuntu in english, but then clicked swedish... :/

---

