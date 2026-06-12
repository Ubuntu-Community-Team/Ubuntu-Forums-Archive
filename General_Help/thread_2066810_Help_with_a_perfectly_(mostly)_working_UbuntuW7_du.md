---
title: "Help with a perfectly (mostly) working Ubuntu/W7 dual-boot installation."
date: 2012-10-05
forum: General Help
---

### Post by AgentIX on 2012-10-05
Hey Y'all. 

SO I managed to install Ubuntu alongside Windows 7 as a dual boot option. I even switched it do that Ubuntu is the default boot. 

BUT! 

My partitions, they are a mess.

Heres the output from:

mount
gnomatic@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda5 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda6 on /media/storage type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/gnomatic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gnomatic)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

And from:

sudo parted /dev/sda unit s print
Model: ATA WDC WD5000BEVT-8 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         45062324s   45062262s   primary   fat32        hidden, lba
 2      45062325s   289249253s  244186929s  primary   ntfs         boot
 3      289249280s  976771071s  687521792s  extended               lba
 5      289251328s  526209023s  236957696s  logical   ntfs
 6      526211072s  976769023s  450557952s  logical   ntfs

SO confused. I thought one could only have 4 partitions?

I'd ideally like to have a 100 gb windows7 partition (for windows os, games, etc.), an Ubuntu root partition and then a large partition for storage of media, music, and movies which i can access from both OS's. is this possible? 

Or should I just count myself lucky that the clusterf*&% is working at all.


Any help/explanation is much appreciated.


Thanks!!

---

### Post by AgentIX on 2012-10-05
Did I do something wrong? I must have, since no one has even bothered to look at this thread. :(

---

### Post by oldfred on 2012-10-05
Please allow up to 24 hours before bumping. We are all volunteers and only those who think they may help based on what you have posted may offer to help. 

It looks like you have installed wubi. Wubi is a install inside the Windows NTFS partition. But you also have created an extended partition. And extended partition is one of the allowed 4 primary but can hold many logical partitions. The listing with /loop is wubi mounted inside another partition and /host is the NTFS partition that wubi is installed into. 

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Windows has to boot from a primary partition, but is your main install in one of the logical partitions? It looks like it might be sda5 which is logical. 

If you have not saved a lot of data in wubi, you can just delete it, shrink Windows with Windows tools and use gparted to create new partitions for Ubuntu. 

If you have a lot of data or configuration in wubi, you can create partitions and move it to the new partitions.
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by AgentIX on 2012-10-05
Whoops, thanks very much oldfred. I just saw that it wasn't gettign ANY views, but that seems to have changed.

WHen I boot, it gives me the option of ubuntu and windows7. could i still be booting into wubi if i am selecting ubuntu at the boot menu? if no, the wubi install is old and no longer used. can i just simply delete it? how would i go about that?

---

### Post by AgentIX on 2012-10-05
and so if windows ifs the primary partiton that'd be sda1, yes? and the loop is wubi?  How does that relate to what im seeign in gparted?

When i open gparted, i get:

---

### Post by oldfred on 2012-10-05
Gparted is only showing NTFS partitions. Linux (other than wubi) does not run from NTFS formated partitions as it does not support ownership & permissions.

You are booting with Windows, and the BCD has a second entry for wubi to boot into the wubi install inside the NTFS partition.

The only Ubuntu install shown is the wubi one. If you have anything you want to save be sure to back that up including the hidden files in /home. And you should make a Windows repairCD, backup Windows before any major partitioning changes, just in case.

Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

