---
title: "Where to put 'insmod raid' in Grub2 config?"
date: 2011-10-06
forum: General Help
---

### Post by scotausborn on 2011-10-06
I recently setup Raid 1 on a running 10.04 system using falko's excellent guide, which can be found here:

[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

However, after successfully booting from the degraded RAID array, then adding the old /dev/sda to the array and syncing it, then updating mdadm.conf, and finally removing the temporary Grub2 boot option and running both update-grub and update-initramfs -u, I get dropped to a grub rescue prompt at reboot.

Grub2 doesn't see the arrays using the ls command until I type 'insmod raid'.  Then I can set the prefix and root, and boot up just fine.  My question is this:  where can I put the 'insmod raid' command in the grub2 config so that I don't have to keep doing this?

Thanks.

---

### Post by drs305 on 2011-10-06
I can't comment on RAID, but specific modules that the user wants loaded as a kernel instruction are added to the /etc/default/grub file. Add this line:

> GRUB_PRELOAD_MODULES="raid"

It should appear near the top of the /boot/grub/grub.cfg file after you run "sudo update-grub".

---

