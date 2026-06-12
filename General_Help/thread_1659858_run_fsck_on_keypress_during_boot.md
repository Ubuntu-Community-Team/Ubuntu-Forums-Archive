---
title: "run fsck on keypress during boot"
date: 2011-01-04
forum: General Help
---

### Post by awp2513_ on 2011-01-04
Hi,

I am wondering if there is a way to manually trigger a file system check during boot by pressing/holding a key. Maybe there is already a keyboard shortcut built in to do this?

I know that using tune2fs you can modify the number of boots (mounts)  between file system checks, or even use "shutdown -rF" to reboot the  system and force a file system check.

Also, I do not want to force the user to choose to run/skip the file system check during boot. For example, prompting the user with, "Do you want to run a file system check [y/n]?" each boot (or even each time the system thinks it should run a file system check), is not desirable.

I know this might seem odd, but any information would be appreciated.

Thanks!

---

### Post by tredegar on 2011-01-04
> I am wondering if there is a way to manually trigger a file system check during boot by pressing/holding a key. Maybe there is already a keyboard shortcut built in to do this?
No, AFAIK there isn't. What would be the need for this?

> I know that using tune2fs you can modify the number of boots (mounts) between file system checks, or even use "shutdown -rF" to reboot the system and force a file system check.

**shutdown -rF** is deprecated (and on my 10.04 system, doesn't work). The "correct" way to force a fsck at the next boot is
**sudo touch forcefsck** in the root directory of the partition you wish to be fsck'd at the next boot.

---

