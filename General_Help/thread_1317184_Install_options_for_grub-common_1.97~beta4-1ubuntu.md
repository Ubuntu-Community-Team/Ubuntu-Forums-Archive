---
title: "Install options for: grub-common 1.97~beta4-1ubuntu3"
date: 2009-11-06
forum: General Help
---

### Post by sldavid on 2009-11-06
When the grub-common 1.97~beta4-1ubuntu3 update was being installed I was prompted by an install wizard to choose how I wanted the update applied. The options were meaningless to me. I just accepted the default.

What option should a novice user choose to 'just keep things the same'?


Here's a copy of the install log for the update:

```
Log started: 2009-11-06  10:42:04
(Reading database ... 45%
(Reading database ... 90%
(Reading database ... 115626 files and directories currently installed.)
Preparing to replace grub-pc 1.97~beta4-1ubuntu3 (using .../grub-pc_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-common 1.97~beta4-1ubuntu3 (using .../grub-common_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Setting up grub-common (1.97~beta4-1ubuntu4) ...
Installing new version of config file /etc/grub.d/30_os-prober ...

Setting up grub-pc (1.97~beta4-1ubuntu4) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

```

---

### Post by bertmanphx on 2009-11-06
sldavid,
See the link [here.]("https://help.ubuntu.com/community/Grub2")

I recently had to look it up as well.

bertmanphx

---

### Post by sldavid on 2009-11-06
bertmanphx

Thanks for the quick reply. Haven't read through all the info yet but it looks like it will answer all my questions.

Scott

---

