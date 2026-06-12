---
title: "Boot up issue. Puple screen only"
date: 2012-07-07
forum: General Help
---

### Post by thatguy93 on 2012-07-07
Hey guys,
I installed Ubuntu 12.04 LTS on my laptop yesterday, and have noticed a weird issue. When I boot my laptop up, I get a purple screen, and no matter how long I leave it nothing happens. I then need to force shutdown the laptop(press and hold power button, or pull out the battery) . Sometimes when I try to boot it again, it will work, and sometimes, I need to shut it down again.
Any ideas to what could be causing this?
Let me know if you need any info I have not provided.

thanks!

---

### Post by oldfred on 2012-07-07
Forced shutdowns do not help. Remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

So it boots sometimes, but not others? You might want to look in the log files and see if some task is taking a very long time or repeating and erring out. See Log File Viewer and demesg amount many log files.

---

### Post by thatguy93 on 2012-07-08
> **oldfred said:**
> Forced shutdowns do not help. Remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

So it boots sometimes, but not others? You might want to look in the log files and see if some task is taking a very long time or repeating and erring out. See Log File Viewer and demesg amount many log files.

That method only seems to work once the computer is booted up fully. When it is stuck in the purple screen, it does not work.
I'm not really seeing anything out of the ordinary in the log file. Should I maybe reboot and post it up?

---

### Post by oldfred on 2012-07-08
It depends on how far along in the boot process it is whether you can REISUB.

You can also use e on the grub menu and remove quiet splash. That will let you see the tasks it runs which are the one's in the log file. But sometimes it scrolls by quickly and the last task is often not the issue.

Have you used nomodeset?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by thatguy93 on 2012-07-08
> **oldfred said:**
> It depends on how far along in the boot process it is whether you can REISUB.

You can also use e on the grub menu and remove quiet splash. That will let you see the tasks it runs which are the one's in the log file. But sometimes it scrolls by quickly and the last task is often not the issue.

Have you used nomodeset?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Would it be a process causing this?
I have not tried NOMODESET, but will try that now.
The system hangs on the shutdown screen every single time now. Just shows Ubuntu with the dots.
Boot up seems to be working fine now, just takes a little longer than normal.

EDIT:
NOMODESET does not seem to help. Still freezes at shutdown. Plus it ruined the look of Gnome haha.

---

### Post by oldfred on 2012-07-08
I thought it was a boot issue.

But now it is a shutdown issue? I have not followed those, but have seen several posts with that in the title.

---

### Post by thatguy93 on 2012-07-08
> **oldfred said:**
> I thought it was a boot issue.

But now it is a shutdown issue? I have not followed those, but have seen several posts with that in the title.
Well it *was *a boot issue, not anymore though.
The boot is still odd(no splash screen), but it works, so I'm not going to worry about it. But yes now the problem is the shutdown, it just freezes.

Should I mark this thread as solved?

---

### Post by oldfred on 2012-07-08
If log files are not showing any real issue then booting must be ok? It should not be excessively long but varies mostly by RAM or hard drive speeds. My SSD is about 10sec from grub menu to working system, but BIOS takes almost 10 sec & grub a few seconds. With my hard drive total time was between 40 & 60 seconds to boot. Of course once every 40 to 60 boots it runs fsck to make sure file system is ok and that can take a bit of time.

---

### Post by thatguy93 on 2012-07-08
> **oldfred said:**
> If log files are not showing any real issue then booting must be ok? It should not be excessively long but varies mostly by RAM or hard drive speeds. My SSD is about 10sec from grub menu to working system, but BIOS takes almost 10 sec & grub a few seconds. With my hard drive total time was between 40 & 60 seconds to boot. Of course once every 40 to 60 boots it runs fsck to make sure file system is ok and that can take a bit of time.

It takes about 30-40 seconds. I'm probably to used to the 10 second boot time on my PC lol.
Thanks for the help!

---

