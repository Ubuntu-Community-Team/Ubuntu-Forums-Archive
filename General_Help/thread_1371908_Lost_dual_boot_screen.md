---
title: "Lost dual boot screen?"
date: 2010-01-03
forum: General Help
---

### Post by charon2112 on 2010-01-03
Hello, I was running a dual boot Ubuntu 9.10/Windows XP.  I reformatted just the windows partition and re-installed it, and now I don't get the option at boot time of what OS I'd like to use...it just boots straight into Windows.  Can anyone help?  Thanks...

---

### Post by charon2112 on 2010-01-04
bump...?

> **charon2112 said:**
> Hello, I was running a dual boot Ubuntu 9.10/Windows XP.  I reformatted just the windows partition and re-installed it, and now I don't get the option at boot time of what OS I'd like to use...it just boots straight into Windows.  Can anyone help?  Thanks...

---

### Post by theturbanator on 2010-01-04
I had a problem similar to this: you have to restore Grub since you lost it to the Windows reinstall.

I had this problem with Ubuntu 9.04, which uses grub-legacy (the default bootloader in 9.04), and the commands to fix the problem can be found here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

However, since 9.10 uses a new bootloader, I am not sure if the same can be done to fix the problem.  You might want to try it?  Or search for how to restore grub in Ubuntu 9.10?

---

