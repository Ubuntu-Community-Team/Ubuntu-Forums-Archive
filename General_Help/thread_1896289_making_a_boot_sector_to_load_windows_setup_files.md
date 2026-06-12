---
title: "making a boot sector to load windows setup files?"
date: 2011-12-16
forum: General Help
---

### Post by heartcore on 2011-12-16
I have an acer aspire laptop 5732z which refuses to boot the recovery disks. the (hotkey doesn't work)

I have tried booting from usb but with no luck yet. I tried making copies of the disks with no luck either.

I was wondering if it is possible to boot a live cd, make a boot sector and place the files from the recovery disks in order to boot directly to the setup. Is this possible? what kind of filesystem to choose etc.

Any other simpler recommendations would be highly appreciated.

---

### Post by DawieS on 2011-12-16
I just had a similar experience with a used laptop that I bought specifically for car diagnostics. The laptop was loaded with Win XP, but also with a trojan virus in the boot sector.

This virus disabled the hot key to the extent that I was unable to enter the BIOS, in order to change the boot sequence to boot from CD. This happened without exception when doing a normal restart for about 20 times. It would just boot without delay into XP, ignoring the pressed button.

I then made a full shut-down, and waited a while before retrying. After turning on the power, I kept the hot button depressed. The third time I was lucky, and entered the BIOS. I then booted from a live CD, wiped the hard drive, and did a clean install.

If you are unable to enter the BIOS and adjust the boot sequence due to a virus, your only other option to re-use the hard drive would be to:
1) remove the hard drive and install in an external casing.
2) boot from a Live CD.
3) mount the external drive and recover any usable data.
4) delete all partitions and re-format in preparation for a clean install.

---

### Post by heartcore on 2011-12-16
hey dawies thanx for the reply.

I have no problem with the bios, my drive is the problem which i need to bypass

---

### Post by BC59 on 2011-12-16
Just check if you belong to this category:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

