---
title: "Ubuntu 10.04 not booting anymore all of a sudden"
date: 2010-09-10
forum: General Help
---

### Post by DeadMetal on 2010-09-10
Hi,

My computer had been running just fine a couple of days in a row. I had a problem and decided to reboot. But all of a sudden Ubuntu does not boot anymore!

The error shown is:
Target filesystem doesn't have /sbin/init. No init found Try passing init=bootarg

Under it it shows
Busybox v13.3
(initramfs) [etc])
[then a couple of rows mentioning removable disks which is my card reader.

And finally just a blinking _ sign.

_Please see the screenshot_

What should I do?

---

### Post by dcstar on 2010-09-11
> **DeadMetal said:**
> Hi,

My computer had been running just fine a couple of days in a row. I had a problem and decided to reboot. But all of a sudden Ubuntu does not boot anymore!

The error shown is:
Target filesystem doesn't have /sbin/init. No init found Try passing init=bootarg
...........
And finally just a blinking _ sign.

_Please see the screenshot_

What should I do?

Boot off the Install/Live CD and do a manual fsck on your hard drive partition.

Do a search for detailed instructions.

---

### Post by 23dornot23d on 2010-09-11
Is the card reader a plugin device ..... if so try unplugging it and reboot .....

if you need it plug it in after boot-up ...... 

(some usb's seem to change the priority of the boot order - depending on a warm or cold start)

I had it happen with mine .... and always cold start now to keep the boot order the same.
I think this is more to do with the machines bios ..... so yours may be different but its worth a go first,

Although having a quick look again ..... yours look to be in the correct order and 

sda I guess is your only main drive ......

(The next set being the card reader)
sdb sdc sdd sde

So seems to be another problem ..... ignore this post .........

---

