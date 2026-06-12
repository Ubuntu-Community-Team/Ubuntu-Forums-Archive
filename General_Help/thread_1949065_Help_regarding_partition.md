---
title: "Help regarding partition"
date: 2012-03-29
forum: General Help
---

### Post by neophyte02 on 2012-03-29
Frens, I've recently bought a laptop. It has got only one partition where there's Windows OS. I want to remove that OS, create 5 partition in my harddisk then install ubuntu and windows 7.

What is the best way to do that? Can you guys please help me. Looking forward to get some help

---

### Post by oldfred on 2012-03-29
Welcome to the forums.

Be sure to back up whatever data and maybe even the entire system you are deleting just in case. If it is a new laptop are you sure you have not used all 4 primary partitions? If so make recovery disks and backup any vendor partitions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

You can use gparted to repartition. Make sda1 or the first partition a primary NTFS partition with the boot flag. Windows 7 if installing to a blank drive uses two partitions. One is a small 100MB hidden boot/repair partition and the main install. The boot partition is to allow you to encrypt the main partition or make repairs to main partition, but you do not have to have it separate. Just make a Windows repairCD right away though.

You can leave one or two partitions as primaries that are not used in case you need them later and all the rest can be inside the extended partition as logical partitions. I would suggest keeping system partitions smaller including Windows and using a shared NTFS formated partition for all data you might want in both systems. I have my Firefox & Thunderbird profiles in the shared so I have all the same bookmarks & email in both systems.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by neophyte02 on 2012-03-30
thanx alot for the quick reply. i wanted to create 5 drives where 2 will be used to install linux and windows. and regarding other 3 partition, will i be able to access those drives from both OS? and which OS do I need to install first? I am bit confused in these things

---

### Post by oldfred on 2012-03-30
Install Windows first, then install Ubuntu. If you make the other partitions NTFS then both systems will be able to use them. Windows will not see any partitions formated for Linux.

---

### Post by neophyte02 on 2012-03-30
thanx alot mate. i'll do it as you suggested. if i face any problem i'll surely post here.

---

### Post by neophyte02 on 2012-03-30
> **oldfred said:**
> Install Windows first, then install Ubuntu. If you make the other partitions NTFS then both systems will be able to use them. Windows will not see any partitions formated for Linux.

one more query. i already have windows installed in it on single drive. so i guess i don't need to remove it. is there any way to break that drive into 5 drives? i guess the drive partitioned using shrink function of windows will not be detected by linux

---

### Post by neophyte02 on 2012-04-01
no reply yet?

---

### Post by oldfred on 2012-04-01
If Windows 7 use that to shrink the Windows partition, but not create new partitions. If you use Windows to create partitions it converts to dynamic which does not work with anything including some Windows tools.

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Best to make Windows repairCD also. If you have spent a lot of time housecleaning Windows and updating it, then you should do a full backup.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

