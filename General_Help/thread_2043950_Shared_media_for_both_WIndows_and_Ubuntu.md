---
title: "Shared media for both WIndows and Ubuntu"
date: 2012-08-17
forum: General Help
---

### Post by GJ1234 on 2012-08-17
Hello fellow-Linuxusers!
(running Windows 7 and Ubuntu 12.04 dualboot 750 GB 7200 RPM Hard drive with 40 GB for Ubuntu and all the other for Windows, Dell XPS 17:KS

I would like to aks you guys a question, here is the situation:
I really like Ubuntu and Windows 7 running alongside each other.
So I have plenty of space to download music and stuff, but the only problem now is that the files (music et cetera) that I download on Windows are not available on Ubuntu and vica versa.
Would it be smart to create a 100 GB partition and let both systems access it or something?
Or is there a more simple way?

Thank y'all!

---

### Post by Deepak J on 2012-08-17
Install NTFS-3g driver using the software centre which will enable you to access your NTFS partitions of windows from Ubuntu.

---

### Post by oldfred on 2012-08-17
You should have the NTFS-3g driver by default in all new installs.

Windows typically does not like too many writes from outside. Also the Linux NTFS driver exposes all the hidden Windows files & folders that Windows normally hides, which can lead to accidents. Often best to set Windows system partition as read-only and use the shared NTFS data partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Set windows boot partition Read only - Morbius1:
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 

Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by GJ1234 on 2012-08-17
> **Deepak J said:**
> Install NTFS-3g driver using the software centre which will enable you to access your NTFS partitions of windows from Ubuntu.

Yeah I can access them but they do not show automatically...

---

### Post by GJ1234 on 2012-08-17
> **oldfred said:**
> You should have the NTFS-3g driver by default in all new installs.

Windows typically does not like too many writes from outside. Also the Linux NTFS driver exposes all the hidden Windows files & folders that Windows normally hides, which can lead to accidents. Often best to set Windows system partition as read-only and use the shared NTFS data partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Set windows boot partition Read only - Morbius1:
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 

Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

Mm I'll read it, but seems pretty hard for a beginner :(

---

### Post by xianbei on 2012-08-17
if you just keep the files on a windows data partition you can mount from ubuntu without much trouble. at least in my experience...

---

### Post by GJ1234 on 2012-08-18
Mm okay I read quite a lot now, I think I just want to make a new partition with 75 GB Space.
But which file-system should I choose so both Windows 7 and Ubuntu can read and write it without problems. (so downloading from Ubuntu straight to that partition and from Windows also)
And how exactly do I let the partition mount at boot, I know it's something with /fstab but there it ends..

So this is what I'd like to know:
Which filesystem should I choose?
Could anybody give me a step by step guide to make that partition mount at boot?

---

### Post by oldfred on 2012-08-18
You want NTFS to share with Windows & Linux.

See post #6, link posted above.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

You create a mount or name to use for your partition, you edit fstab with the examples shown and always run this before rebooting. IF no errors you edited correctly, or it will tell you something is wrong.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

If you want details post this and what name you want for your Windows partition. I have use "shared" but it can be anything.

Post this in code tags (highlight like a copy and click on # n edit panel)  to preserve formating:
sudo blkid -c /dev/null -o list

---

### Post by GJ1234 on 2012-08-20
Mm I think I´ll look at the auto-mount later, at this moment it is a little bit to hard for an absolute beginner ;)

But the biggest problem right now is that Windows 7 won't let me make a partition because I already have the maximum of 5 on my disk..
I know Windows does not like things from outside so I already shrank the volume so there is unallocated space for a (logical it has to be?) partition?
I'm sure Linux has a way to create a partition and not render Windows unbootable ;)

---

### Post by oldfred on 2012-08-20
If you create partitions with Windows it may convert to dynamic partitions which does not work with Linux and even some Windows repair tools.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by GJ1234 on 2012-08-21
> **oldfred said:**
> If you create partitions with Windows it may convert to dynamic partitions which does not work with Linux and even some Windows repair tools.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Thanks for being so helpful!
But I see in the Gparted tutorial that Gparted can make a 6th extended partition while Windows cannot, if I use Gparted to make my 50 GB unallocated space an extended partition will it render Windows unbootable?

And I read about removing a partition, but I'm not sure if that works on my Dell XPS 17.
Various sources on Internet state that my OEM partition should never be deleted so 1 option is lost
The disk with Recovery should also not be deleted I read.
The OS C: is where Windows is so that one neither.
And I have a 33 GB and a 5,89 GB partition which are both primary and I guess that is where Ubuntu is installed.

Here a screenshot: [IMG]http://i46.tinypic.com/14ni9me.png[/IMG]

---

### Post by oldfred on 2012-08-21
You do have to delete either the Dell or the recovery partition. The other two are Windows and the hidden boot or main install are essential for Windows.

You should be able to recreate a set of recovery DVDs which then let you recover from a hard drive failure. Having the image on a drive, may work if drive still works but if drive fails, how are you going to reinstall the system to a new drive. But that only restores to as purchased so also best to have a full backup.

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

Dell restore partition.
[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

---

### Post by GJ1234 on 2012-08-21
Mm I dont trust myself with this so I'll look at other options, is it possible to just enlarge my Ubuntu partition without problems?
Thanks for all the help anyway guys!

---

### Post by GJ1234 on 2012-08-22
I read a bit and if I want to resize my primary Ubuntu partition I could do this:

Boot from USB and use Gparted to resize the partition with the 50 GB already unallocated space?

---

### Post by oldfred on 2012-08-22
Post screen shot from gparted and this:
```

sudo fdisk -lu
```

---

### Post by GJ1234 on 2012-08-22
Here the ```
sudo fsdisk -lu
```
[IMG]http://i45.tinypic.com/250165e.png[/IMG]

And the screenshot from Gparted
[IMG]http://i45.tinypic.com/s2a82d.png[/IMG]

Hope you could help me!

---

### Post by oldfred on 2012-08-22
You can post screenshots with the paperclip icon in the edit panel. Then they are not overwhelming. Also text output can just be copy & pasted. But if long, use code tags which you highlight text like copy & click on # in edit panel.

You have used all 4 primary partitions, so you cannot create another primary. But luckily your unallocated is next the the extended partition. You can in gparted move extended partition left to include the unallocated and either create another logical or expand/move the LInux partition. You can only expand right, so you have to move it left then expand right, it that is what you want.

You have to use gparted from a liveCD as you cannot edit mounted partitions (the little key icon says it is mounted). LIveCDs usually mount the swap partition which may also mount the extended, so from liveCD click on swap and right click swap off to unmount it. Then you can edit partitions.

Before any editing of partitions make sure you have good backups. Any power failure in the middle will corrupt system and require a re-install. But I have edited partitions many times without issue.

Some other suggestions or alternatives. I generally prefer smaller system partitions for both Windows & Linux. And have most or all data in other partition(s). For newer users I often suggest a separate /home and if dual booting with Windows a separate NTFS shared data partition. I do not recommend many writes into the Windows system partition as Windows sometimes complains and you have to run chkdsk. Best to have the shared NTFS partition. You then can set the Windows system partition as read-only.  If most data is in the shared data partition, you probably do not need a separate /home. Windows will read and use a shared NTFS partition that is logical inside the extended partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

