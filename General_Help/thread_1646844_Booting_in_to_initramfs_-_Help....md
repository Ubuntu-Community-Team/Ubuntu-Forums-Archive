---
title: "Booting in to initramfs - Help..."
date: 2010-12-16
forum: General Help
---

### Post by NibbleG on 2010-12-16
Ok, so I am aware that I am an idiot.  I wanted to move 80 or so gigs of movies and music from my desktop to my netbook, both have Ubuntu 10.10 on them.  I didn't think about the fact that my netbook was in suspend mode.  When I slapped the HDD back in I get dropped in to initramfs.
Holding shift while selecting my most current kernel if get,

recordfail
insmod part_msdos
isnmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7b512a84-di69-4e54-8aed-38228337a/3ab
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7b512a84-di69-4e54-8aed-38228337a3ab ro   quiet splash
initrd /boot/initrd.img-2.6.35-23-generic

For the most part my system is pretty vanilla, 10.1' gateway netbook, 2gb ddr667, 160gb hd, Intel graphics, only one Ubuntu install, no XP or 7 or whatever...

Anyone know how I can fix this without booting from a livedisc or thumb drive.  I only ask that because I don't have one on me and I'm waiting for the bus to NYC (which has wifi)

If i have to I can reinstall Ubuntu later tonight and move all the stuff back over, I was just hoping for a "easier" fix.

Nibble G

All was needed to move the hdd back in to the desktop and shutdown without unmounting it.

---

