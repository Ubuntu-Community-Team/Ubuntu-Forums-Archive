---
title: "How do I upgrade from a USB"
date: 2010-11-26
forum: General Help
---

### Post by Lara_Baker on 2010-11-26
In a previous thread, I was advised to use a Live CD to fix my recent upgrade of 10.10.  I was told that when I booted from the Live CD, one of my options would be to upgrade my system.  When I boot from a Live CD [actually on a USB stick] I the only options I see are to Run Ubuntu or Install Ubuntu.

How do I go about upgrading from the USB without losing all the data and configurations I have in place?

Thanks,

Lara

---

### Post by efflandt on 2010-11-26
It depends what is wrong with your system.  If you get a grub menu when you try to boot your system normally, and can boot a (recovery) kernel, you may get some insight from this thread [http://ubuntuforums.org/showthread.php?t=1629898](http://ubuntuforums.org/showthread.php?t=1629898)

If grub does not work, then you could boot from the usb iso, but that may be more involved depending what error you get or what is not working.  You likely have grub2 unless you originally upgraded from Ubuntu 9.04 or earlier and did not update the grub version.  Grub2 would have grub.cfg instead of menu.lst in /boot/grub.  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Tobeus on 2010-11-27
I agree that having more information about the original problem would be helpful.  Maybe if you could post your previous thread link we could get a better picture of what you are trying to do.

If you need to actually BOOT into the Live CD, then Run Ubuntu is the option for that.  Not sure about upgrading since I've never used a Live CD to upgrade.  You might actually try burning an ISO to CD and see what boot options come up.  I know that some of the boot options are different depending on whether it is a USB or CD.  For example, I could not verify the image on USB when I could on CD for the same install.

---

