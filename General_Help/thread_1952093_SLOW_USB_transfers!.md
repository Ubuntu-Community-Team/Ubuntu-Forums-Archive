---
title: "SLOW USB transfers!?"
date: 2012-04-03
forum: General Help
---

### Post by petermg on 2012-04-03
For some reason I'm getting around 1megabyte a second sometimes half that on my USB transfers, it's connected to a USB 2.0 controller external SATA drive.  It literally takes over two hours to copy about 5 gigs of data, something like that.  I've been reading and found others with similar issues but I can't seem to find a solution.  Any help is greatly appreciated!  Thank you!

Peter

Oh and I'm running Ubuntu 11.10

EDIT: I see using disk utility that it's mounting the drive at 12MBPS (USB 1.0) rather than 480MBPS (USB 2.0)!?

---

### Post by QIII on 2012-04-03
A perennial problem and still unanswered.

It's been a while since I did any reading on this, but there was some discussion some time ago that the issue was related to disk spinup time and that the transfer speed during spinup is reported as USB (or interpreted that way) before the disk is at speed and should show USB 2.  Not sure if that is still the current speculation.

It is one of those "things somebody really should fix because it sucks" things as far as I can tell.

People report similar problems with flash drives while moving large files.

---

### Post by mutex023 on 2012-04-22
This problem is indeed extremely frustrating and I've seen it since Ubuntu 10.04.
I've a workaround for this. Please check this thread and let me know if it works - 
[http://ubuntuforums.org/showthread.php?t=1963360](http://ubuntuforums.org/showthread.php?t=1963360)

---

