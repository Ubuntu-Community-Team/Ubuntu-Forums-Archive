---
title: "how to choose which distro handles boot"
date: 2011-12-21
forum: General Help
---

### Post by bestron on 2011-12-21
I'm "multibooting" ubuntu with opensuse that has an older grub version and can't detect ubuntu, so I wanted ubuntu to handle the boot loading instead of opensuse.
Is that possible :confused: , how to do that?

---

### Post by d2btoo on 2011-12-21
I'm not sure but will this help:

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
- and scroll down to "Dual boot: two operating systems with GRUB legacy & GRUB 2 mix" section.

statutory warning: I'm personally never tried that, in other words, if you mess up, you can't blame me. :-P

---

### Post by Bobhuber on 2011-12-21
> **bestron said:**
> I'm "multibooting" ubuntu with opensuse that has an older grub version and can't detect ubuntu, so I wanted ubuntu to handle the boot loading instead of opensuse.
Is that possible :confused: , how to do that?
Yes - Install Ubuntu's grub2 to your primary boot partition from a live CD (Ubuntu) . There are MANY posts on how to do this. Boot into Ubuntu and run update grub. Reboot and your grub menu should then include the SUSE partition as a choice. Note that any time you update or change the Kernel in SUSE you will have to update grub in Ubuntu .

---

### Post by Dennis N on 2011-12-21
To have grub2 serve as the boot loader instead of grub, boot into the system (Ubuntu) which uses grub2. From that system, you need to install grub2 to the master boot record. If the disk these OSes are on is /dev/sda, the command would be:

```
sudo grub-install /dev/sda

```

Be sure not to have any removable USB drives plugged in when you do this. Then, run update-grub. Finally, reboot to get the new grub menu.

---

