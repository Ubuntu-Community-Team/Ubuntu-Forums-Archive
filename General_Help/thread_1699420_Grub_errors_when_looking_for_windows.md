---
title: "Grub errors when looking for windows"
date: 2011-03-03
forum: General Help
---

### Post by linux noooob on 2011-03-03
So recently I installed Ubuntu 10.10 so that I could run a minecraft server for my friends. When installing I installed ubuntu to my drive (sdb) and I installed the bootloader on to sda. When loading ubuntu grup doesn't even come up and the bootloader doesn't recognize sda. When trying to update-grub I get this:```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: nvidia: wrong # of devices in RAID set "nvidia_aabjaicf" [1/2] on /dev/sda

```

---

### Post by Quackers on 2011-03-03
The output of grub.cfg seems to think that you have (or had) a raid array.
Are you using raid, or has the hard drive ever been part of a raid array?

---

### Post by linux noooob on 2011-03-03
I do believe the person I got the HDD from used it in a home server so I'm going to say yes. But that's only the HDD the rest of the computer has never been in a computer with raid.

---

