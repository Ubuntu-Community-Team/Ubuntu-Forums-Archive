---
title: "Hang on fschk, general error mounting filesystems"
date: 2009-12-16
forum: General Help
---

### Post by johann_p on 2009-12-16
I have Ubuntu 9.10 on a Thinkpad T500.
The boot process does a disk check but always after about 89% the system hangs - Esc does not work any more, nothing can be done but holding the power button to turn the system off.

When I interrupt the disk check before it hangs, I get the error: 
"General error mounting filesystems" and I am thrown  into a maintainance shell. In that shell, all the file systems and files seem to be intact, however I cannot change any file (I tried to disable the disk check in /etc/fstab).

After a while a text menu with some recovery options appears, but I was unable to use that because red messages from the boot process messed up the screen.

I ended up starting a live CD and using that to disable the disk check and now the boot worked fine.

However, this is just a workaround, not a solution: how can I figure out why the disk check hanged and why does aborting the disk check throw me into a maintainance shell with that error?

---

### Post by quixote on 2009-12-17
I've had that weird business with red messages overwriting the recovery options screen.  (I wound up reinstalling instead of solving it, so that's no help here.)  The fact that fsck isn't working is Not Good, and you're lucky it still boots.  I wouldn't use it until you get it sorted out because every disk access increases the likelihood that garbage will be written to a critical area, and then it really will be dead.  If you have data you must have, boot up, get the data, and then leave it alone until fixed.

The only suggestion I have for fixing is to try [testdisk]("http://www.howtoforge.com/data_recovery_with_testdisk").  

If the only hard drive is the one that's failing, then you can try the following method:  boot with LiveCD, go to software sources and enable all repositories.  Reload repository info.  Go to synaptic and install testdisk.  This won't be a permanent install, of course, but it will install it for that session.  Then run it like it says in that testdisk link.  

It's a kind of ugly, text-based, command line program, but if it's possible to recover a filesystem or a partition table, it'll do it.  When it tells you which other blocks have filesystem info, write them down!  Tedious, but later when you tell it to recover, you can give it one of those backup blocks to rewrite the faulty ones at the beginning which are probably what's giving you grief.

Hope this helps.

---

### Post by johann_p on 2009-12-18
Thank you for the pointer to testdisk, I will try that just to be safe.

I think there are actually several Ubuntu bugs involved here: 
* when I started the LiveCD I did a fschk of the disk and no error was detected. So that hang probably was caused by some other issue.
* aborting an fschk with Esc should not throw you into the recovery console
* at least in safe mode, booting should be linear so that one does not get boot messages while in the recovery options screen. Or some other solution should be found.

---

