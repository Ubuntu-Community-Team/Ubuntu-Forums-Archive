---
title: "Can't boot, strange symptoms"
date: 2011-02-13
forum: General Help
---

### Post by Zeike on 2011-02-13
I'm having trouble booting my Ubuntu partition. When I select Ubuntu in grub, it loads the kernel, & initrd, then hangs with a blinking cursor in the upper right of the screen.

Windows 7 & Gentoo both boot fine from the same drive.

the UUID of the root drive in grub.cfg is correct, and matches the output of blkid. Replacing it with the block device does no better either.

Attempting to boot the kernel with the debug option produces no output.

Examining the drive shows that the kernel is writing no logs.

The drive does not appear to be corrupted, as it can be accessed by my Gentoo install just fine, and multiple fscks deem it clean.

Attempting to run the grub commands manually (going into the grub cmd-line and running "linux /boot/linux-image-2.6.35-25-generic ro debug", etc) produce no errors, but when "boot" is executed, I get the blinking cursor.

Remove all USB devices (other than keyboard & mouse) doesn't help.

Reinstalling grub, and regenerating the initrd do nothing.

Any suggestions would be appreciated.

---

