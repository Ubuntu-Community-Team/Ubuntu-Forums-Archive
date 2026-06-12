---
title: "Need 2 check USB HD for errors..."
date: 2009-12-11
forum: General Help
---

### Post by Deist on 2009-12-11
Hello there!

First of all, I apologize for posting this in the /General Help/ section! Prolly not the most appropriate but I couldn't find a more suitable one.
Second, I'm still a total newbie under Ubuntu. ;)
Thrid, I'm currently on holiday at a friend's place and therefore no access to my real Ubuntu! All I have with me is my old Ubuntu 9.04 live disk.

My problem is with an external USB hard-drive, in NTFS format, but don't run screaming just yet, it's not about mounting the damn thing or anything like that. Here's what happens:
I was watching a movie (from my USB NTFS hard-drive) on my friend's laptop (running Vista :?), when the video started to freeze, and kept doing so on my several attempts to just disconnect/reconnect the HD and relaunch the video, until eventually Vista started reporting errors on another video file. At my next attempt to disconnect/reconnect the drive, I was told that the drive wasn't formatted and couldn't therefore be accessed.

I figure the partition table was somehow ****** up (hardware problem :cry:).
Of course I can't check the HD under Vista since it won't access to it, and I can't mount it under Ubuntu either. My request is: is there a way to make like a surface check or sth, I mean any way to check the disk without actually mounting it under Ubuntu? And more generally, can anyone suggest a way to try and recover as much data as possible from the drive? I have very important stuff on it...



Thank you very much if you took the time to read all this, and I'm (eagerly ;)) awaiting your answers/ideas/more details requests/etc.
-- DeisT

---

### Post by Deist on 2009-12-12
I should also precise that the external HD seems to work fine physically (even though the error was probably made by the hardware), so the problem is really one of more errors on the disk. But how can I check it for errors since I cannot mount it?

---

### Post by Deist on 2009-12-12
Nobody has any suggestion about my issue? Can someone at least tell me wether it is actually possible or not to check a hard-disk without mounting it?

---

### Post by kgas on 2009-12-12
-initially you could read the files from the HD
- then vista says hard disk can not be accessed.

sudo fdisk -l   : list all the disks (or use gparted)

use chkdsk under windowsxp to find bad sectors if any

Sometimes harddisk formated in NTFS under ubuntu gets failed to read under Windows, specially vista.

Try to recover your partition with tools like testdisk.

The final thing is your hard disk may be reaching end of life.

---

### Post by Deist on 2009-12-12
Thank you for your suggestions kgas!

My HD is recognized, as fdisk -l states:

Disk /dev/sdb: 300.0 GB, 300090727936 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fb57b97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    7  HPFS/NTFS

Unfortunately I'm unable to check the disk under Windows since it tells me that the drive is not formatted and therefore cannot be accessed. Trying to launch a scandisk on it is unavailable...
For the same reason I believe Testdisk would be just as useless to me.
I should also precise that this HD was indeed formatted under Windows and hasn't had any trouble until today.

Basically it seems to me that it's all a problem with an error appearing in the partition table or sth, but since my datas are still on the disk, I'm looking for any possible solution to get check the drive for errors and get my datas back (at least partially) if possible...

---

### Post by bumanie on 2009-12-12
To do a filesystem check, boot a live cd and try this is terminal > sudo e2fsck -C0 -p -f -v /dev/sdxx
Obviously you have to change the /dev/sdxx to you own drive designations and do this with the drives unmounted - you will have to do them separately. The code comes [from here]("http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem") if you want to check further details.

---

### Post by Deist on 2009-12-12
> sudo e2fsck -C0 -p -f -v /dev/sdx 			 		
Thanks, this command is what I'm willing to do, except it applies only to ext* partitions, and my disk is NTFS.
Any way I can do this for a NTFS filesystem?

---

### Post by efflandt on 2009-12-12
Attempting to disconnect/reconnect repeatedly without "Safely Removing" may have messed it up, but it is also possible that it was already failing and trashing itself.

I tried to recover info from a failing laptop hard drive using gparted-live CD after WinXP refused to boot it even in safe mode to protect against further damage.  And gparted refused to touch it until Windows fixed it.  In the end I could only copy some directories from the user's home dir, and none of "My Documents".  I tried an external USB enclosure, but not sure it that is working properly, recognized as usb mass storage, but would not mount the drive in Windows or Linux.  Maybe it is simply too far gone.

A replacement drive works fine.

---

### Post by Deist on 2009-12-12
Well, my HD is already old and it is indeed quite likely that there are many bad sectors on it and that the HD is reaching its lifeterm (even though I must say I never had any trouble with it, not even one alarm message about anything when read/writing on it, until today).
I'd still like to know wether I can possibly check it unmounted and maybe recover if only a few stuff from it? I tried to force mount it (sudo mount -t ntfs-3g /dev/sdb1 /media/ExtDrive -o force) but to no avail...

---

