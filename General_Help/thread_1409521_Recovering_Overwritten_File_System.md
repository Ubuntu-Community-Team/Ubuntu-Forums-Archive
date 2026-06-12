---
title: "Recovering Overwritten File System"
date: 2010-02-17
forum: General Help
---

### Post by Zone117x on 2010-02-17
Alright so I was trying to decrease the size of my main partition so I could create a secondary and install Windows 7 to.

I was using Norton's partition software. My computer had to reboot and before reaching Windows XP it started doing the resizing. For some reason it failed in shrinking my main partition. I'm not sure if any harm was done while it was trying to do this.

I proceeded to run the Windows 7 installer, under the impression I could just install Win 7 to the same drive and leave all my personal files alone. Right when the installation started during the "Copying files" stage I hard reset the computer after getting nervous and changing my mind..

I booted up Ubuntu Live and found that my main file system had been cleared, and only a few tiny temp Windows 7 installation files where there.

I am sure there were no deep formatting done, only a quick format by the win 7 installer.


So I am posting this to ask if there is any software I can run in Ubuntu to scan the drive for files to recover them, because the new file system overwrote the old one.

---

### Post by jamesisin on 2010-02-17
In the future I recommend using GParted for repartitioning living partitions.  You can get it as a Live CD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

or it is included as a utility in the Ubuntu installation/Live CD.

As to your issue, there are some recovery tools you can try.  I had pretty good luck with this Windows utility once (slow but effective):

[http://www.soundunreason.com/InkWell/?p=33](http://www.soundunreason.com/InkWell/?p=33)

In Ubuntu, I was able to recover a partition enough to mount it and recover files.  The first two pages of comments relate to your issue:

[http://ubuntuforums.org/showthread.php?t=1396158](http://ubuntuforums.org/showthread.php?t=1396158)

---

