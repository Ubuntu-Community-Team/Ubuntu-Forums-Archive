---
title: "WUBI error message"
date: 2011-01-21
forum: General Help
---

### Post by tommo43 on 2011-01-21
Hi, I now use open office instead of windows office, andwould like to get away from windows gradually. When I try to install ubuntu using wubi I get the following error message, which I have also been getting in recently in other apps.
It may have something to do with downloading, trying and then un-installing apps.

The message is: pyrun.exe-No Disk.
"there is no disk in he drive. Please insert a disk into drive \Device\Harddisk1DR1

I had previously installed Ubuntu and was able to boot it up in boot options, although I did not know how to use it having booted up.
Whatever happened subsequently stopped me doing this and that is why I tried to re-install it through wubi today and got the above error message. I cannot get rid of the error message except by re-booting.

---

### Post by bcbc on 2011-01-21
Remove all unnecessary peripherals e.g. card readers, phones etc. Wubi uses python and it doesn't like drives that are assigned, but empty.

When you use Wubi, please avoid updating packages grub-pc and grub-common. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Blue Dolphin on 2011-01-21
I encountered the same error message.
Here is my thread for this issue:
[http://ubuntuforums.org/showthread.php?t=1671857](http://ubuntuforums.org/showthread.php?t=1671857)

My query has been resolved. Hope you find it useful.

---

