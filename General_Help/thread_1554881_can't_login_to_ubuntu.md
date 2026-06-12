---
title: "can't login to ubuntu"
date: 2010-08-17
forum: General Help
---

### Post by andresefe on 2010-08-17
I have got a very similar issue to the guy of this thread [http://ubuntuforums.org/showthread.php?t=1553663&highlight=login](http://ubuntuforums.org/showthread.php?t=1553663&highlight=login). I type in my password and it logs on for a second but then the login screen comes up again. I tried what was suggested on the previous link and didn't work. The last thing I installed was the startup manager, though i did no changes at all, AT ALL! After I restarted and boot up windows, next time I tried to boot Ubuntu 10.04, this issue came up. I will appreciate your help as I have no idea what's going on, I'm kinda new with Linux

---

### Post by sydbat on 2010-08-17
> **andresefe said:**
> I have got a very similar issue to the guy of this thread [http://ubuntuforums.org/showthread.php?t=1553663&highlight=login](http://ubuntuforums.org/showthread.php?t=1553663&highlight=login). I type in my password and it logs on for a second but then the login screen comes up again. I tried what was suggested on the previous link and didn't work. The last thing I installed was the startup manager, though i did no changes at all, AT ALL! After I restarted and boot up windows, next time I tried to boot Ubuntu 10.04, this issue came up. I will appreciate your help as I have no idea what's going on, I'm kinda new with LinuxHow have you installed Ubuntu? Was it via wubi (as a program inside Windows)? Or did you create a separate partition for it?

Wubi is fine for testing Ubuntu, but not for long term use, as it relies on the Windows file system (it runs as a virtual OS) and can become unstable/unusable if the Windows file system becomes corrupted in any way (usually though fragmentation).

When you boot up, there is a series of options in the GRUB menu. The first starts Ubuntu normally. The second is a "recovery" option.

Go into the recovery option and run "fix dpkg" (or whatever it is called) and that *might* fix the problem.

---

### Post by andresefe on 2010-08-18
Yes, actually i've installed it via wubi. Now you mentioned it, I removed the /windows driver from the /etc/fstab file because it was driving me nuts every time I was booting up Ubuntu warning me about /windows drive couldn't be mounted. So you think that should be the problem?

---

