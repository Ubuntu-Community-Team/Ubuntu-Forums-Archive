---
title: "grub2 much slower than legacy on USB stick"
date: 2011-12-04
forum: General Help
---

### Post by xerces8 on 2011-12-04
Hi!


As described here [http://lists.gnu.org/archive/html/help-grub/2011-11/msg00042.html](http://lists.gnu.org/archive/html/help-grub/2011-11/msg00042.html) and here [http://lists.gnu.org/archive/html/help-grub/2011-12/msg00006.html](http://lists.gnu.org/archive/html/help-grub/2011-12/msg00006.html) , I see much worse load performance with grub2 than with grub 1 (aka grub legacy).

I formatted an USB key and installed grub2 as described here: [http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)
(I did this under Ubuntu 11.10)

Then I added RIPLinux 13.5 to the boot menu. Booting it takes 3-4 minutes. (tried 2 different PCs).
Then I mirrored over to the test USB stick an older USB stick I had that has grub4dos 0.4.4. This also had RIPLinux 13.5 on it, and now it boots in 30-40 seconds.

I tried FAT32 and NTFS, but in both cases grub2 is very slow.

Anyone else had such experience?
Any idea what to do?

If no solution, I'll just use grub4DOS (with NTFS), which works.

Thanks for any help,
David

PS: Even the grub4dos values are bad, as the USB key can read at 30 MB/s, so the riplinux image with its 120 MB should be loaded  in 4-5 seconds.

---

