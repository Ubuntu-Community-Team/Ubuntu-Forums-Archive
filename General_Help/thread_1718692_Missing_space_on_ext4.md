---
title: "Missing space on ext4"
date: 2011-03-31
forum: General Help
---

### Post by MarkTrent on 2011-03-31
Hello,

I formatted a 2TB hard drive using ext4, and disabled both the journal and block reservation at creation to maximise my storage space. This worked great and after formatting, my hdd had only 64mb used by the filesystem (half as much as if I'd formatted it as NTFS).

I then copied 1.3TB of data from a 2TB NTFS hard drive onto the fresh drive. After completion I've checked my drive and the ext4 drive has 33.7GB less space available than the NTFS drive, both containing the exact same files (apart from the lost+found directory). I dismissed myself and ran the commands to disable journaling and set the reserved blocks to 0% again, thinking I must've forgotten to do this originally, but it turns out I had indeed done this when I first formatted the drive.

Unfortunately I rebooted after the transfer before I checked the disk spaces, so I can't be sure wether the space was missing directly after the transfer, or if it occurred after the restart. Does anyone know where the space has gone?

I'm quite new to Linux, and I just want a file system that gives me the low space overheads of NTFS, but with good speed on Linux. Is there a better filesystem I should be using? It's used as a media storage drive. (Coming from Windows, I originally formatted the new drive as NTFS but found it had slow transfer speeds so switched to ext4; went from 15mb/s --> 115 mb/s)

Thanks for any info,
Mark

---

### Post by bryanl on 2011-03-31
check tune2fs - linux reserves 5% of its partition space for system emergency needs. If you don't have any system stuff such as log files on the partition, you can use 'tune2fs -m 0' to free it up.

see 'man tune2fs' for determining current allocation of reserved space.

---

### Post by dabl on 2011-03-31
If it is just data storage, you might want to look at jfs or xfs.  jfs is very low CPU usage, for example.

---

### Post by MarkTrent on 2011-04-01
> **bryanl said:**
> check tune2fs - linux reserves 5% of its partition space for system emergency needs. If you don't have any system stuff such as log files on the partition, you can use 'tune2fs -m 0' to free it up.
 
see 'man tune2fs' for determining current allocation of reserved space.
 
I performed this when I formatted the drive, and again afterwards just in case, so I know that's not the problem. The reserved space is set to 0%

---

### Post by kio_http on 2011-04-01
The ext4 filesystem does reserve some space for journaling, file information headers etc ... so yes there is a considerable loss of space using it but its not that bad.

---

