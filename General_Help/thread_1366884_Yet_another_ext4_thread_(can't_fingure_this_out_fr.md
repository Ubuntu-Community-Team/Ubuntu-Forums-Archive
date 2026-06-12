---
title: "Yet another ext4 thread (can't fingure this out from other threads)"
date: 2009-12-28
forum: General Help
---

### Post by nstgc379 on 2009-12-28
I've search googled, the launchpad bug report, and this forum, and have been unable to successfully answered the fallowing questions myself.

Was the ext4 problem in Jaunty fixed in Karmic?

If not, how do you apply the patch?

Is this different if you are using a 64bit version (worse/better?)

I know about the patch, but I don't know how to apply it. I also can't tell if the bugs have been worked out or not, just that they existed at one time.

From the descriptions I've seen of ext4 it seems more reliable then ext3, but at the same time if these bugs haven't been worked out, and I can't patch them, then all those reliability features are dwarfed.

I'm also planning on installing the 64bit version so I can test out lrzip on larger files. If I can avoid the bugs by using the 32bit version, however, then I will.

[edit] Also, this is all assuming that ext4 is better for long term storage due to better reliability. If this isn't true then the bug problems are irrelevant.

---

### Post by adbge on 2009-12-28
What bugs, precisely, are you concerned with? Please link the bug reports if possible.

---

### Post by nstgc379 on 2009-12-28
I've mostly just seen general "theres a bug". If you go to launchpad and run a bug search for "ext4" you get a long list of bug reports. The only one I can specify exactly is that in case of a crash (or more likely a power outage) you are more likely to lose an entire file in ext4 than in ext3.

---

### Post by falconindy on 2009-12-28
Filesystem reliability and performance issues are rarely (if ever) tied directly to a specific distro. Rather, they're associated with the kernel. In this case, the data corruption/loss bug that was evident pre-2.6.28 was fixed in Jaunty. This wasn't so much a bug fix as it was the end of the development cycle for Ext4 when Theodore T'so (the maintainer) declared it stable for everyday use.

Due to the way that Ext4 lazily syncs data to the hard drive, it is **still** possible to have some amount of data loss in the event of a hard crash of the OS or a kernel panic. This was curtailed somewhat in 2.6.32 but also introduced a performance regression. Since Karmic is on the 2.6.31 kernel, you still have the inherent possibility of the aforementioned data loss but not the performance regression. Understand that this is **by design** and any filesystem can suffer data loss in the event of a kernel panic.

---

### Post by nstgc379 on 2009-12-28
My understanding however was that this was due to the use of the vol_id library instead of the blkid (I think) library. It is distro specific, or at least according the kernal.org wiki it is.

---

### Post by adbge on 2009-12-28
> **nstgc379 said:**
> I've mostly just seen general "theres a bug". If you go to launchpad and run a bug search for "ext4" you get a long list of bug reports. The only one I can specify exactly is that in case of a crash (or more likely a power outage) you are more likely to lose an entire file in ext4 than in ext3.

In regards to ext4 file loss and patches:

"The new patches are expected to become part of the mainline kernel 2.6.30. Various distributions may choose to backport them to 2.6.28 or 2.6.29, for instance Ubuntu made them part of the 2.6.28 kernel in version 9.04—Jaunty Jackalope."

ext4 should be fine.

---

### Post by nstgc379 on 2009-12-28
> **adbge said:**
> In regards to ext4 file loss and patches:

"The new patches are expected to become part of the mainline kernel 2.6.30. Various distributions may choose to backport them to 2.6.28 or 2.6.29, for instance Ubuntu made them part of the 2.6.28 kernel in version 9.04&#8212;Jaunty Jackalope."

ext4 should be fine.

If thats the case, whats with all the bug reports? Karmic uses 31, but the problem isn't the kernal, but rather the library.

Well, I'm not sure if all Karmic releases us 2.6.31, but I know mine does.

---

### Post by sbsbessa on 2009-12-29
As the original subject of this thread, I '[B]can't fingure this out from other threads'.
[/B]Since yesterday I started noticing my disk space to fly away, ending up with 0bytes free on my EXT4 partition, mounted on /.
I'm using EXT4 for / and EXT3 for /home and this happened during my regular backup configured with 'Simple Backup' on Ubuntu 9.10, which has been running fine for a few months now.

The backup did not finish and the only way I could get the system to start X again was to increase EXT4 partition size.
However today the same thing happened again... suddenly the extra 10Gb of space gained through partition resizing disappeared...
I noticed gzip was running at the time and I suppose it was trying to do the backup to the external usb drive, so I stopped it and could keep 390Mb free, that's why I'm still able to use the system.

Could this be related with EXT4 pre-allocation not being released?
This is the result of df -h

/dev/sda3              29G   27G  390M  99% /
udev                  1.5G  252K  1.5G   1% /dev
none                  1.5G  876K  1.5G   1% /dev/shm
none                  1.5G  108K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda1             130G  105G   18G  86% /home

sda3 is EXT4 and sda1 is EXT3

'Disk Usage Analyzer' only shows a total of 110.5Gb used so where did the remaining 12Gb go?

---

### Post by sbsbessa on 2009-12-29
Just found an answer to my problem here: [http://ubuntuforums.org/showthread.php?t=1367320](http://ubuntuforums.org/showthread.php?t=1367320)

---

