---
title: "Grub2 &quot;speed&quot;"
date: 2011-06-16
forum: General Help
---

### Post by EgoGratis on 2011-06-16
With Grub time to get from "BIOS Check" to Grub menu is instant.  With Grub2 there is about one or two extra seconds to get to the Grub 2 menu or too start loading OS! Is it possible to speed up Grub 2 in the way that the time between "BIOS Check" and Grub 2 menu would be reduced?

Please don't post answers on how to set "GRUB_TIMEOUT" to 0... This is different question!

---

### Post by oldfred on 2011-06-16
I do not necessarily recommend it.

But the boot stanza does not need much to work. If booting from a hard drive where drive does not change you do not need the search line. It may save time searching for the UUID which is a backup to the set root line where drives change drive number -  externals, usbs, even some BIOS do not boot mixed IDE/SATA consistently.

Some of the .mod that it may mount are already defaults, you can try editing some out.

You can totally simplify your grub.cfg.

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

And then in your 06_custom:

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

But grub2 is larger to accommodate more type of systems, that I do not think you can work around.

---

### Post by EgoGratis on 2011-06-18
First of all, thank you for your answer!

The "problem" is i am not wiling to spend few weeks discovering that Grub 2 can't "load" faster. If somebody did make Grub2 "load" faster and can tell me exactly what he did and that it works that i would try. I don't think "trying" out things when i know very little about Grub2 (under the hood) would get me far.

---

