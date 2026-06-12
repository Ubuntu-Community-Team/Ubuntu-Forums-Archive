---
title: "fsck fails status 8, but OK on next boot"
date: 2010-01-18
forum: General Help
---

### Post by Irihapeti on 2010-01-18
I've been messing around with Lucid alpha on a second partition on my desktop computer's main drive, and I also installed a second hard drive that was given to me. 

I've started getting some fsck errors occasionally when I boot into my main (Hardy) installation. I'll get the message "fsck failed with status 8" (or similar wording) and then a root shell appears. If I continue with the boot, I then get the message that my home directory doesn't exist and the option to log into a different directory.

If I then reboot, the next bootup is fine. In one case, it even went into a routine check which it completed with no errors.

I found out that Hardy and Lucid have different ways of detecting the two drives, as noted in this thread: [http://ubuntuforums.org/showthread.php?t=1374197](http://ubuntuforums.org/showthread.php?t=1374197)

Could this be related to the issue? Or is it something more serious such as the health of my main hard drive? And yes, it's backed up regularly. :)

---

