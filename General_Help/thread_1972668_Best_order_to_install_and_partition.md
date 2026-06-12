---
title: "Best order to install and partition?"
date: 2012-05-03
forum: General Help
---

### Post by robinzxp on 2012-05-03
Hi, I got this new 2tb hard drive which I wanted to use for media PC. I'm trying to duel boot but ran into issue with number of partions in windows. So here were my partitions

42gb Ubuntu
1Gb Swap
65GB Windows 7
100MB(?) Parition Windows force to make
1700GB For media.

But when I tried to format and mount 1700GB windows complained it can only allow 4 paritions. So I look into it and if I converted to Dynamic disks it would let me have more than 4! So without furture research I converted to dynamic and to my horror I found only some version of windows support dynamic and Linux doesn't suuport it. I think I'm going to format and start from beginning again so here are my questions

1. If delete all the partitions will it become basic partition again?
2. Is it possible to have 5 Partitions and all me mounted on windows? (Quite sure Ubuntu won't have this annoying issue)
3. What is order to partition and install?
E.g 1. Parition Windows + Media and install Window. 2. Parition Linux and install Ubuntu?
4. Is it better to have exFat or NTFS for media parition for compatiblity purpose? I'm going to be having large movie files so Fat32 isn't good enough any more.

Many thanks!

---

### Post by zvacet on 2012-05-03
>  If delete all the partitions will it become basic partition again?

You will have unallocated space (entire disc).
If you want to delete all partitions and start with new installation then first install Windows.After that install Ubuntu.WHen you install ubuntu maybe it is good idea to have separate home partition.That way all your files & setings will be safe in case you choose to reinstall,fresh install...You can Install Ubuntu on logical partition and that way you will avoid 4 primary partition limit.For ubuntu install 

1. root=10-15GB                                 mountpoint /
2. swap=~2GB
2. home= rest of space you want to give to ubuntu    mountpoint /home

Format partitions as ext4.
Partition for media format as fat32 because ubuntu doesn´t see exfat.

---

### Post by 2ta8gdfte on 2012-05-03
If your not using Windows encryption you can avoid its boot partition if you want, just put an ntfs as sda1 with a bootflag with gparted, then choose the custom install in windows and install to that partition.

Next you might be relieved to know that a ntfs in a extended is seen by windows and will become the D drive there, put as many ntfs in the extended you want. 

Then install the ubuntu in the extended as well with a swap and have fun.

Don't forget to make images of all the installs it will save a huge amount of time to reload, especially for windows, regarding their update speed. This also gives you a clean windows image saved in case something happens.

Clonezilla is a excellent cloner, and all windows releases have a imager I believe even XP home does you just have to pull it off a XP disc.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2012-05-03
You can convert back. But Windows offical policy is to back up, erase disk and repartition.

Best to use Windows to shrink a Windows partition but then use gparted to create Linux partitions. Windows can read logical partitions, but has to have a primary NTFS partition with the boot flag to boot from.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

After you get Windows installed & updated and everything the way you want back it up.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Also make a Windows repairCD or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Now you can use gparted to make new extended and logical partitions for Ubuntu.With a 2TB drive I might make / (root) 25GB.

---

### Post by IparryU on 2012-05-07
> **zvacet said:**
> You will have unallocated space (entire disc).
If you want to delete all partitions and start with new installation then first install Windows.After that install Ubuntu.WHen you install ubuntu maybe it is good idea to have separate home partition.That way all your files & setings will be safe in case you choose to reinstall,fresh install...You can Install Ubuntu on logical partition and that way you will avoid 4 primary partition limit.For ubuntu install 

1. root=10-15GB                                 mountpoint /
2. swap=~2GB
2. home= rest of space you want to give to ubuntu    mountpoint /home

Format partitions as ext4.
Partition for media format as fat32 because ubuntu doesn´t see exfat.
OK... making the /home was something i did not do. i did install XP first, made a separate NTFS partition for data, then installed Ubuntu and selected the auto partition option (sorry if that does not match what the install says...)

So going along with what oldfred had posted, will the partition tools work with my /  partition and not do anything damageable?

I just got Ubuntu customized to where I like it, but having /home there for future install/re-install/etc. would be nice.

---

### Post by mastablasta on 2012-05-07
> **zvacet said:**
> Partition for media format as fat32 because ubuntu doesn´t see exfat.
fat32? it's preety old and obsolete file system. why not NTFS? FAT32 has a limit on file size and is more fragmented...

---

### Post by robinzxp on 2012-05-07
Hey guys, Thanks for all the replies. Bit late but here's how it went.

I ended up using EASEUS Partition Master on different computer to divide up all the partitions (It doesn't support Ext4 or swap so I only formatted two of the partition to those formats in Ubuntu) and installing Windows than Ubuntu. It worked out great. I also used NTFS as I have media files that's well over FAT32's file size limit.

This way I can have more than 4 partitions without windows complaining about it. (Linux is on logical partition)

---

