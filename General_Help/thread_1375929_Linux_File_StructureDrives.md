---
title: "Linux File Structure/Drives"
date: 2010-01-08
forum: General Help
---

### Post by carbonbased on 2010-01-08
I'm just learning about the intelligent file system for Linux. Under Windows I learned long ago to run Windows on a separate drive, if possible, and a separate partition, at a minimum, with all of my data files, whether text or multi-media files, on another partition or drive. This was for safety to the data and the system files, since Windows crashes and the file system fragments so often.

Even though the Linux FS isn't prone to fragmentation, I am still wondering whether it would be more functional for any reason to place the Linux folders, like /Home, on another partition, or another drive, since they're more prone to being modified, written, erased, etc.?

Also, would it allow the system to run faster if the system files were on a separate disk from, e.g. media files?

I have Ubuntu 9.10 installed now under a dual-boot system. It's working out so well, I might go to Linux totally, soon. If there are advantages to the ideas above, can I move the Linux folders to a new disk without totally reinstalling everything from scratch?

Thanks.

---

### Post by xtjacob on 2010-01-08
I have a /home partition on my computer so if something happens I can reinstall it with everything still there. This came into use the other day when my computer got corrupted from a power outage. All I had to do was reinstall ubuntu (which took like 10 minutes) then when I was back the theme and everything was the same. The way I did it was I made a copy of all my /home folders on an external hard drive, and reinstalled ubuntu with a /home partition, then copied them back.

---

### Post by gsmanners on 2010-01-08
If you use different formats (like ext4 along with ntfs or reiser, etc.) then it obviously makes sense to have different partitions. Any time you can put a different partition on a different drive, it should make transfers more efficient.

If you use media files while also starting applications a lot (which could cause serious drive thrashing), then it would make sense to keep them on separate drives. It's really all a matter of what you're doing with your computer, though.

One nice thing about having an easily installed OS is that reinstalling really isn't a big deal, especially if you keep your /home folder in a different partition or drive.

---

### Post by carbonbased on 2010-01-08
How does one tell the system that folders are located on another partition or drive? I guess that's the way I should have asked the question originally.

---

### Post by gsmanners on 2010-01-09
Those are mount points. By default, those are all laid out in /etc/fstab.

See:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://manpages.ubuntu.com/manpages/karmic/en/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/karmic/en/man5/fstab.5.html)

---

### Post by lostinxlation on 2010-01-09
df helps.

---

