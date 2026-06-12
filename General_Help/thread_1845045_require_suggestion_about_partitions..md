---
title: "require suggestion about partitions."
date: 2011-09-16
forum: General Help
---

### Post by adeee on 2011-09-16
i had dual boot..divided 40 gb of hard to ubuntu and rast of the windows xp.
The partitions i chose is something like this.
/boot 100mb
/usr       10gb
/           10gb
/home   20gb
/swap    1gb

now according to my research on net there is no reinstalling procedure of grub2 for /boot for recovering ubuntu after the instalation of windows xp.(according to last post of this thread. [http://ubuntuforums.org/showthread.php?t=1803429](http://ubuntuforums.org/showthread.php?t=1803429) and the procedure of reinstalling given on other sites. -thats not working.)
Thats why i decided to ask about the proper partitions. so that i can reinstall grub2 eaily whenever i need to install it.. 
so whats your recommendation?

---

### Post by plucky on 2011-09-16
> **adeee said:**
> i had dual boot..divided 40 gb of hard to ubuntu and rast of the windows xp.
The partitions i chose is something like this.
/boot 100mb
/usr       10gb
/           10gb
/home   20gb
/swap    1gb

now according to my research on net there is no reinstalling procedure of grub2 for /boot for recovering ubuntu after the instalation of windows xp.(according to last post of this thread. [http://ubuntuforums.org/showthread.php?t=1803429](http://ubuntuforums.org/showthread.php?t=1803429) and the procedure of reinstalling given on other sites. -thats not working.)
Thats why i decided to ask about the proper partitions. so that i can reinstall grub2 eaily whenever i need to install it.. 
so whats your recommendation?


I would use 

/  8Gb
/home  31Gb
/swap   1Gb

No need for a separate /boot partition and /usr is not the user.

See [Howto Restore Bootloader Tutorial](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub2)

Good Luck

---

