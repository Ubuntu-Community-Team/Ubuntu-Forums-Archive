---
title: "NTFS-related random system freezes"
date: 2009-09-11
forum: General Help
---

### Post by pveurshout on 2009-09-11
A little while back I started a thread ([http://ubuntuforums.org/showthread.php?t=1258664](http://ubuntuforums.org/showthread.php?t=1258664)) because I was experiencing seemingly random system freezes. Sometimes I was able to use REISUB and read something in the logs (which didn't make any sense to me, by the way), but most of the time a hard reboot was required so there was nothing to be seen. I've been trying some things out in order to rule out possible causes, but eventually it all seems to add up to my Jaunty entirely locking up after a while when intensively reading/writing from/to my NTFS-partition. That's why I'm starting a new thread about this, hoping to find someone who can help finding out what exactly is wrong and how to fix it.

I'm sharing an NTFS partition between Jaunty and Vista which I, amongst other things, use for bittorrenting. First, I started to experience some random lockups, which all seemed to be related to using Vuze. I changed my bittorrent client (by now I've used 3 different ones) but the problem persisted. At some point I started to suspect that the frequency of the lockups increased with the intensity of usage. This effect came to my attention when the system froze three times in just a couple of hours when trying to download a torrent containing six 2.1 GB files. (up to that point the individual files I downloaded were much smaller in size)
When I'm only seeding a couple of files it's generally fine for several hours, but when downloading something (at about a couple hundred kB/s or more) it'll lockup the system in half an hour.

On the NTFS-3G website I read a couple of things that may have been related, but, eventually, each of them seemed to be unlikely to be the cause:

[QUOTE="[http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)"]
STABLE Version 2009.4.4 (April 2, 2009)

    * (...)
    * (...)
    * Fix: The driver could crash handling highly fragmented files. 
[/QUOTE]
I completely defragmented the partition, but the problem persisted (also when only seeding, so not adding any fragmentation!).

[QUOTE="[http://ntfs-3g.org/support.html#questions](http://ntfs-3g.org/support.html#questions)"]
**Why does the driver have high CPU utilization?**
    The most common explanations are

        * (...)
        * (...)
        * (...)
        * A highly sparse file is being regularly written or updated. 

(...)

**Why is writing huge files slowing down?**
    Either you don't use at least NTFS-3G Version 2009.3.8 or your disk space is highly fragmented in a close to full cluster allocation zone, or a highly sparse file is being updated (e.g. a bittorent file, VMware image file).

    Workaround: Use a software which can compact the disk space (e.g. the free, open source ntfsresize: shrink then enlarge after making a backup). Please note, file level defragmentation, what the built-in Windows defragmenter is only capable, does not help usually.
[/QUOTE]
These two problems seemed to be not too unrealistic as I'm using sparse files to allocate disk space when starting a new torrent, but unlike the NTFS-3G FAQ, I've never experienced a slowdown or high CPU usage: in my case the complete system simply freezes at times when everything seems to be perfectly fine. In addition, the system also freezes when only reading from the drive, thereby not writing/updating sparse files. (Also: when I complete a torrent, so all the file data is written, the file is no sparse file anymore but "turns into" a regular file..or does it work in a different way?)

The latter bug should be fixed in version 2009.4.4, to which I updated today. After remounting the partition using the new driver, the system froze a while after starting to download one of those 2.1 GB files again. This update should also have fixed any problems with highly fragmented files mentioned in the first bug (although this shouldn't be the problem since I defragged).

Apart from bittorrenting, I also experience lockups when copying (large) files over my home network (samba) *from* an NTFS partition (ext3 is fine) (although this may not be statistically significant as today I did it once for the first time in a while and it froze exactly once) and two times the system froze while writing to an external USB (NTFS formatted) drive (out of about 10 times; I don't have an external device regularly attached for daily use but just use one for backup).

**One important remark to conclude: none of this happens when using an ext3 partition.**

I used the Vista built-in tool to check the disk and I also performed the long smartctl selftest, which both showed up no errors. Also, the system freezes are not related to any specific file and in addition I've been moving around some stuff (to external harddrives, to my ext3-partition, etc.) and all was fine, so I doubt it's a physical harddisk error (but I'm no expert).

I'm using Jaunty amd64, kernel 2.6.28-15-generic (it also happened on the -14 kernel), and I've tried NTFS-3G versions 2009.2.1 (comes standard with Jaunty) and 2009.4.4.

Has anyone ever encountered similar problems or would otherwise know what could be causing this? (and, preferably, how to solve it ;-)) If more information is necessary: please let me know and thanks in advance for any help!

---

### Post by pveurshout on 2009-09-12
I reformatted the drive as ext3, so (hopefully..) this thread isn't relevant anymore. I'll therefore mark it as solved, although it actually isn't. If this is not appropriate, please let me know and I'll remove the [SOLVED] prefix!

---

### Post by P4man on 2009-09-12
If it does solve it for you, then I guess [solved] is appropriate, but Im still intrigued by your findings. I've had my share of performance problems on ntfs volumes, but ive never seen it lockup. If its true, it certainly warrants a bug report.

BTW, Im kinda miffed looking at that ntfs-3G site. They blame any performance problems on anything but their driver, but then they do link to their commercial solution that provides "up to 30-50 times more file system performance". Its as if they are handicapping the opensource driver deliberately, I can't say i like that very much :s

---

### Post by pveurshout on 2009-09-12
I'm currently setting up the partition as ext3 and once I'm sure it works like it should (automounting, user privileges - I should know that the next time I reboot) I'll try out and see what happens when I start bittorrenting again. If it works fine the next few days the problem was definately NTFS-3G related and if it starts showing the same kind of lockups then I'll be back where I started. Today I spent 2 hours regaining 1 MB of free disk space by moving an entire (but empty) 115 GB file system 1 MB 'to the left' in gparted. Don't mention my stupidity (I should've done this in another way lol), but at least I know the harddrive should be OK as it encountered no problems reading and writing every part of the HDD.

NTFS-3G: Yeah, that actually surprised me as well. Oh well, I guess it's just another reason not to use Windows (and thereby eliminating the need for NTFS-partitions/drives) ;)

---

