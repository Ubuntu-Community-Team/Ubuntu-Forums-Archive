---
title: "automatically skipping fstab-listed usb-hdd during boot when absent"
date: 2010-05-18
forum: General Help
---

### Post by equaeghe on 2010-05-18
Hi,


I use my laptop at different locations.
I have a usb-hdd at one location that I use for backup purposes.
It is listed (by its specific label, not uuid because I don't want to go through the hassle of changing this when changing backup drives or adding one at a different location.

Now, since upgrading from 9.10 to 10.04, I get the following message during boot when the usb-hdd is not present and thus not attached:

The disk drive for "/media/backup" is not ready yet or not present

I need to press S to skip mounting manually, whereas 9.10 just ignored that fstab entry and continued booting. How can I get the old behavior back? Is there an option I can give in fstab that mounts the drive at bootup when present and ignores it when not?

Perhaps an even better solution would be to let the drive be mounted according to the fstab entry whenever it is attached (be it at bootup or at any other moment): is this possible? Related to that: are drives unmounted/mounted in a suspend/resume cycle?


TIA,

Erik

**Solution: the nobootwait option in the appropriate fstab line (man fstab explains it) **

---

### Post by DawieS on 2010-05-18
I recommend that you remove the entry for the **USB**-drive from **/etc/fstab**.

The default behaviour of 10.04 is to automount **USB** drives if present. External **eSata** drives are also detected when plugged in, but requires a click to be mounted.
:smile:

---

### Post by equaeghe on 2010-05-18
Dear DawieS,


Thanks for your quick reply.
It seems that usb-drives are not automounted on my end (Kubuntu amd64).
Moreover, I would not want this behavior as standard, I would like only specific drives to be automounted in specific places. In my limited knowledge, the only way to specify this is in fstab.


Best,

Erik

---

