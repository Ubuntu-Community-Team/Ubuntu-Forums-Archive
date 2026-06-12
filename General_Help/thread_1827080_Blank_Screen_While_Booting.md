---
title: "Blank Screen While Booting"
date: 2011-08-17
forum: General Help
---

### Post by Thedark7 on 2011-08-17
Hi,

I recently installed Ubuntu 11.04 on my laptop. I uninstalled, now I installed again. *I used WUBI both times.* This time, every time I boot, (after I select Ubuntu in the wubi and grub bootloaders) I get a blank black screen with a flashing _ in the corner. Then I get to the login screen and it works like normal. Are there any solutions for this? I'd sort of prefer to see the ubuntu logo and flashing dots. :P

---

### Post by sanderd17 on 2011-08-17
This is probably because of your video driver. If you use the proprietary driver, it can't be loaded fast enough for you to see the boot screen. If you use the open source driver, than it can be loaded fast enough (in most cases).

This is not harmfull, and I would not care about it.

If you like to see the logs going by instead of something flashing, remove the "quiet splash" boot option from GRUB (see my signature for info about editing boot options).

---

### Post by Thedark7 on 2011-08-17
Hi, thanks for the help. I got the ATI driver ubuntu had a driver available popup for. I am using wubi, so how would I display more than the flashing underscore?

---

### Post by sanderd17 on 2011-08-17
Ow sorry,

I haven't had a wubi installation in years (I haven't had Windows in years) so I guess you should google about changing boot options in Wubi.

Deleting the quiet splash option will still work, you just have to search how to delete it.

---

### Post by sanderd17 on 2011-08-17
In any case, do not run the update-grub command. There is a problem with wubi that will break your bootloader if you do it.

---

### Post by Thedark7 on 2011-08-17
Alright, thanks. I'll leave the thread open in case anyone has any info.

---

