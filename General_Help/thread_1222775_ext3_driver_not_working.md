---
title: "ext3 driver not working"
date: 2009-07-25
forum: General Help
---

### Post by the2ndgenesis on 2009-07-25
Hey everyone. I'm trying to get a fresh install of 9.04 working but have had some issues along the way (most of which are for another thread)... but the most vexing problem I've had so far is that I can't seem to get the Windows ext3 driver to work on my Vista x64 partition.

For those of you who aren't familiar with the driver, here's a link:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I've re-installed Ubuntu three separate times trying to get this to work, but have reached the same result every time: after the installation I can see the ext3 partition and the swap partition in "My Computer," but I can't look into the former or even see how much of it is being used without being asked to format it (second pic).

If it helps, I've noticed that during the driver installation process there seems to be one slight deviation from the installation as presented on the website. As you can see here
[http://www.fs-driver.org/images/ScreenSetup5.gif](http://www.fs-driver.org/images/ScreenSetup5.gif)
all the ext2 partitions are shown with their filesystem name during the installation, whereas when *I* try to install it, my ext3 partition is marked only as "Linux" (first pic).
I'm not sure whether that actually matters, but I figured it'd be worth it to mention it anyway.

At any rate, thanks to those who could offer their opinion on this and help me get my installation back on the right track! I'll be watching this thread and will respond to questions as soon as I'm able to do so.

---

### Post by Whiffle on 2009-07-25
Its probably the inode size.  fs-driver only supports a size of 128, but the default on ubuntu is 256 now.  There is another driver that supports it though, although I can't remember it off the top of my head.  If ya search the forum you might find it, it was posted recently.

---

### Post by the2ndgenesis on 2009-07-25
> **Whiffle said:**
> Its probably the inode size.  fs-driver only supports a size of 128, but the default on ubuntu is 256 now.  There is another driver that supports it though, although I can't remember it off the top of my head.  If ya search the forum you might find it, it was posted recently.

I found the ext2fsd Volume Manager at
[http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.46/Ext2Fsd-0.46.exe/download](http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.46/Ext2Fsd-0.46.exe/download)
from an earlier thread, as you hinted at. There doesn't seem to be much you can do with it, though, other than observe the partitions themselves and change the drive letters. Unless I'm using it incorrectly, of course.

In any case, thanks for the advice Whiffle. Hopefully they'll end up fixing the first driver, I really liked how well it worked.

---

