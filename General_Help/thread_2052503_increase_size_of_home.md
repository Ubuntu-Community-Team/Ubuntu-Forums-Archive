---
title: "increase size of home"
date: 2012-09-03
forum: General Help
---

### Post by VISHAL PANWAR on 2012-09-03
how to increase the size of /home directory as i am unable to install new softwares

---

### Post by mikewhatever on 2012-09-03
Generally, to change the size of a partition, you'd need to use Gparted from a live CD/USB. That said, new software is usually not installed into home.

---

### Post by VISHAL PANWAR on 2012-09-03
i am new user of ubuntu and trying to install ruby on rails using rvm,and when i am trying to install its showing not enough space in home

---

### Post by ajgreeny on 2012-09-03
Can we see the output of the command ```
sudo fdisk -lu
```and ```
df -hT
```please.

---

### Post by VISHAL PANWAR on 2012-09-04
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x139eec58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63488879    31744408+   c  W95 FAT32 (LBA)
/dev/sda2        63490048   188337955    62423954    7  HPFS/NTFS
/dev/sda3       188338174   220153855    15907841    5  Extended
/dev/sda4       220154760   234436544     7140892+   7  HPFS/NTFS
/dev/sda5       188338176   217634815    14648320   83  Linux
/dev/sda6       217636864   220153855     1258496   83  Linux

df -ht  value is 

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4     14G  4.5G  8.6G  35% /
none      devtmpfs    491M  264K  491M   1% /dev
none         tmpfs    497M  1.5M  495M   1% /dev/shm
none         tmpfs    497M   92K  497M   1% /var/run
none         tmpfs    497M     0  497M   0% /var/lock
/dev/sda6     ext4    1.2G  959M  191M  84% /home
/dev/sda2  fuseblk     60G   45G   16G  75% /media/6894B1F994B1CA38

---

### Post by ajgreeny on 2012-09-04
Your problem is that you have made the /home partition far too small.  It would have been better to have no separate /home partition (keep /home in the root partition) if you only have 15GB to play with, rather than only 1.2GB for /home which is never going to be enough for anything worthwhile.
```
/dev/sda6     ext4    1.2G  959M  191M  84% /home
``` from your fdisk output.

Your root partition sda5 is about the correct size, but you could perhaps reduce it slightly to maybe 10GB, using gparted on a live CD, by grabbing the right hand end of sda5 and moving it to the left.  You can then increase the size of /home to take up the spare, now unallocated space.

However the best way to deal with this properly if you really want to use ubuntu for more than just a "look-see" will involve shrinking your windows partitions and making more space for ubuntu.  How best to do that will depend on the windows partitions you already have and what is in them, which is impossible to tell from the fdisk output.

A screenshot of gparted window would help as it will show all the partitions including windows, and may help with further recommendations.

---

### Post by VISHAL PANWAR on 2012-09-05
hey i am posting u the screenshot of gparted window please have a look and tell me what to do

---

### Post by ajgreeny on 2012-09-05
It is difficult to know what to tell you to do for the best.

I assume sda1 is not your Windows OS.  Do you know what it is?  As a fat 32 partition it could be just storage space, but it would be good to know for certain, as that is where most of your free space is.  However, it is much too far away from your ubuntu partitions to make life simple for you.  If you reduced the size of sda1 the space will not be available for ubuntu, as your Windows OS partition at sda2 is still in the way.  I also suspect that you will be unable to shrink that any more, and if you did so with gparted rather than windows own disk management, you could have big problems in windows.

I am not suggesting you start again with a reinstallation of windows, but your partition layout at present is difficult to deal with sensibly.

One possible but maybe slightly risky answer is to backup all the contents of your current /home partition to a DVD-R, then comment out the line in /etc/fstab that relates to /home, and then reboot.  I assume a new /home/user folder in the root partition will be made, and you can then restore everything from the DVD back to your new /home/user folder.

Finally using gparted in a live session you can delete that 1.2GB old home partition and resize the root partition into the now free 1.2GB free space.

I think all this shows how important it is when installing Ubuntu in the first place to think ahead about the sizes of partitions you need, or will need in future.

---

### Post by oldfred on 2012-09-05
Another possibility.

Have you made the set of DVDs from the HP recovery partition? Many suggest making that set and then just deleting the recovery partition. You then could expand extended partition right to use the unallocated that was sda4 and then expand your /home. It only adds a few GB but better than nothing.

Many also suggest only saving recovery partition for when you sell system and new user wants Windows. Recovery erases system and restores to like new, so it is better to have a full backup of Windows to restore that.

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

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by newb85 on 2012-09-05
> **ajgreeny said:**
> I assume sda1 is not your Windows OS.  Do you know what it is? 
I'd be really interested to know this, as well.  It seems really odd to me.

By the way, wouldn't it be possible to shrink the FAT32 partition and use the freed space to create a new partition, and then use that for /home?  I don't know how--it's just a half-baked brainstorm.

---

### Post by ajgreeny on 2012-09-06
> **newb85 said:**
> I'd be really interested to know this, as well.  It seems really odd to me.

By the way, wouldn't it be possible to shrink the FAT32 partition and use the freed space to create a new partition, and then use that for /home?  I don't know how--it's just a half-baked brainstorm.
No there is no chance of another partition as there is already the maximum of 4 allowed in a BIOS system.  I looked at that as well but if you look more closely you will see that sda4 is not a logical partition in the extended sda3 partition as it first appears.  That is why it is so important to know what is in that sda1 partition; most of the space is being wasted at the moment.

---

### Post by VISHAL PANWAR on 2012-09-06
yup sda1 is windows os which is not working right now
and what about sda2 can it be shrink and used for home

---

### Post by oldfred on 2012-09-06
Your sda1 only has 2.79GB used so it cannot be much, but it has boot flag. Windows only boots thru the partition with the boot flag, so was this a very old install with most deleted, but with boot flag Windows will still put its boot files into that partition. If it has the boot files for your Windows you may want to move to the Windows partition, move boot flag and possibly make some repairs to sda2, so you do not need sda1 to boot.

---

