---
title: "sreadahead/ureadahead updates"
date: 2009-12-01
forum: General Help
---

### Post by timzak on 2009-12-01
I received an update notification for sreadahead and ureadahead, but noticed in the description that it says:
> This requires the kernel package also found in karmic-proposed.

Since I don't have karmic-proposed repositories enabled, why am I even getting this update as an option?  It seems if I install it without the kernel version in karmic-proposed, I may break my system.  I'm tempted by the promise of faster boots, but have held off on this update due to the quote above.  Any insight?

Thanks,
Tim

---

### Post by dcstar on 2009-12-02
> **timzak said:**
> I received an update notification for sreadahead and ureadahead, but noticed in the description that it says:


Since I don't have karmic-proposed repositories enabled, why am I even getting this update as an option?  It seems if I install it without the kernel version in karmic-proposed, I may break my system.  I'm tempted by the promise of faster boots, but have held off on this update due to the quote above.  Any insight?

Thanks,
Tim

A package will not install if any of its dependencies are not also available, so if you try to install it and it installs successfully then it obviously has found those dependencies.

Please do not "quote" information, that is for previous posts.

---

### Post by timzak on 2009-12-03
Well, I tried to install, and it installed.  So apparently all dependencies were satisfied.  However, now I'm noticing weirdness in my system.  During bootup I see a brief message with "ureadahead" in it, but it disappears too fast to read it.  I then briefly see the login window, then it goes to a black screen with a message about one of my hard drives have problems (swap) and to hit ESC to go to a shell.  I hit escape and it takes me back to the login window.  I log in and the system seems to be normal, except every once in awhile, the video will disappear, as if the monitor was shut off.  After a second, the video reappears.

Not quite sure what to make of this.  Any suggestions?  How do I revert back?

---

### Post by timzak on 2009-12-05
Seems like I fixed this problem.  This morning there was a kernel update that I hoped would fix the problem.  It did not.

So, I did some googling and took a peek in /etc/fstab.  I noticed there were two lines for my swap partition, one with UUID and the other with drive path.  I read somewhere that commenting out the UUID line might fix this problem, so I tried.  It did not.  I took another look in /etc/fstab, and noticed something I missed the first time.  The line with the swap drive path was somehow changed from /dev/sdb1 to /media/sdb1.  I'm not sure if it's been that way since install, or if some update along the way changed that, but once I corrected that to /dev/sdb1, I no longer have the messages during bootup, nor the message to hit ESC to go to the shell.

Hopefully this helps someone else with the same problem.

Regards.

---

