---
title: "NAS Storage Server - mdadm | Suggestions"
date: 2011-01-20
forum: General Help
---

### Post by fishingkid on 2011-01-20
Hey Everyone,

I am trying to decide on how to create a storage server (NAS) at home for my media. 

My Requirements
[LIST]
[*]One Disk Redundancy (Similar to Raid-5)
[*]Ability To Expand (Grow) aka Add another disk in the future
[*]Share with Microsoft Windows PC's (SMB)
[*]Reliability
[/LIST]

My original plan was to use FreeNas but there is no real way of expanding an array. Also I would like the ability of a full desktop install so I may configure other services and such.



From what I have researched mdadm seems pretty simple from the cli and has the ability to add a disk in the future. 

I have breifly tested this in VMWare and it seems to work ok.
Here are the steps I have done. 

[LIST]
[*]In VMWare I added 4*10GB SCSI Drives.
[*]mdadm --create /dev/md1 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
[*]mkfs.ext3 /dev/md1
[*]mkdir /video
[*]mount /dev/md1 /video (Added a line to fstab as well)
[/LIST]

Now I am going to add the fourth disk.
[LIST]
[*]mdadm --add /dev/md1 /dev/sde
[*]mdadm --grow /dev/md1 --raid-devices=4
[*]Watched the Process complete with cat /proc/mdstat
[*]Then resize2fs /dev/md1
[*]Last but not least df -h
[/LIST]

Please tell me if I did anything wrong or not suggested.

_Questions_
[LIST]
[*]Is ext3 the right file system to be using?
[INDENT]I will be storing media files. Some as big as 20GB and as small as a couple megabytes etc picture music.[/INDENT]
[*]Should I be using LVM's to?
[INDENT]I'm planning on starting with three 2 TB drives then expanding one at a time as needed.[/INDENT]
[*]After I added the fourth disk I shutdown the system removed the disk and powered it back on. As it was booting I noticed an error regarding RAID.
[INDENT]Is there a possible way of setting up an alarm that would notify me if a disk fails? Otherwise there is no real way of knowing unless you check your logs.[/INDENT] 
[/LIST]

Thanks Everyone for reading,
Replies are greatly appreciated.
Also a special thanks to jmandawg for this awesome [_**post**_]("http://ubuntuforums.org/showthread.php?t=713936")

---

### Post by fishingkid on 2011-01-20
bump

---

### Post by fishingkid on 2011-01-24
bump

---

