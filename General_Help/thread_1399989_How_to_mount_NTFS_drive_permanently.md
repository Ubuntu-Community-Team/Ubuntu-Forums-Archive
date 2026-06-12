---
title: "How to mount NTFS drive permanently?"
date: 2010-02-06
forum: General Help
---

### Post by karthick87 on 2010-02-06
Can anyone tell me the procedure to mount an NTFS drive permanently?

---

### Post by darthmob on 2010-02-06
I think you can do that with *ntfs-config*. It's in the repos. :)

---

### Post by karthick87 on 2010-02-06
Thank you,but how to do it manually using fstab..

---

### Post by theozzlives on 2010-02-06
First you create a mount point well say /media/ntfs
```
sudo mkdir /media/ntfs
```
Now the fstab, well say it's sdb
```
/dev/sdb /media/ntfs ntfs defaults 0 0
```
to try it out do:
```
sudo mount -a
```

This is off the top of my head, if it don't work PM me and I'll look how I got it done on my server.

---

### Post by pastalavista on 2010-02-06
The easiest way to manage drives is with 'pysdm' storage device manager.

```
sudo apt-get install pysdm
```

It will appear in the System | Administration menu

---

### Post by karthick87 on 2010-02-06
I used ntfs-config and i receive the error..

---

### Post by theozzlives on 2010-02-06
> **getyourkarthick said:**
> I used ntfs-config and i receive the error..

I know people insist on installing ntfs-config, but I never have and had no problems. They will also tell you to use ntfs-3g for the file system, but ntfs works fine for me.

---

### Post by Morbius1 on 2010-02-06
[I][B]Step 1: Find out what partitions are available
[/B][/I] 
Open **Terminal**
Type **sudo blkid -c /dev/null**

You'll get an output that looks something like this:
> [COLOR=Black]/dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs" [/COLOR]
/dev/sda2: UUID="DA9056C19056A3B3" LABEL="WinXP2" TYPE="ntfs" 
/dev/sda4: SEC_TYPE="msdos" LABEL="BOOTIT EMBR" UUID="CD32-0200" TYPE="vfat" 
/dev/sda5: UUID="1EF42FA9F42F81DF" LABEL="VMOS" TYPE="ntfs" 
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat" [I][B]Step 2: Create a home for the partition to live in:

[/B][/I]Open **Terminal**
Type** sudo mkdir /media/WindowsXP**

*** Step 3: Create the fstab line. It has the following form:***

[Device] [Mount Point] [File_system_type] [Options] [dump] [fsck] 

It can be as simple as this. I'm showing all variations on how you can specify the "[COLOR=Blue]Device[/COLOR]":

```

[COLOR=Blue]/dev/sda1[/COLOR] /media/WindowsXP ntfs defaults 0 0
[COLOR=Blue]UUID=DA9056C19056A3B3[/COLOR] /media/WindowsXP ntfs defaults 0 0
[COLOR=Blue]LABEL=WinXP[/COLOR] /media/WindowsXP ntfs defaults 0 0

```This will produce a mount that will be owned by root with read / write permissions to everyone.

I prefer something a little more explicit in permissions:

```
/dev/sda1 /media/WindowsXP ntfs defaults,umask=007,uid=1000,gid=46 0 0

```**umask=007** User Mask

Each digit represent a type of user. The first digit is owner, the second is group, and the third is everyone else. A 0 allows read / write. A 7 allows nothing. So 007 allows owner and group to read and write to that partition and no one else.

**uid=1000** User Identifier

The user specified will be the owner of the mount point. uid=1000 is me. To make sure 1000 is the correct number for you type **id** in a terminal.

**gid=46** Group Identifier

All users on your box are members of group=46 (plugdev). So together with umask=007 it means that all local users will be able to read and write to that partition.

The uid=1000 is somewhat redundant here because I am also a member of group=46. I add it here so that I can use Nautilus-share ( "Sharing Options" in Nautilus ) to share that partition across my network. By default Nautilus-share will allow a user to share only those directories he owns.

---

### Post by Morbius1 on 2010-02-06
theozzlives, My apologies. It seems I said the same thing you did but I tend to go on forever so by the time I finished and hit submit I didn't bother to read any of the other posts.:redface:

---

