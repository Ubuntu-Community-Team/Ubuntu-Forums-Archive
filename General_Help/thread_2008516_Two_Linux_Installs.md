---
title: "Two Linux Installs"
date: 2012-06-22
forum: General Help
---

### Post by sandyd on 2012-06-22
I currently have Ubuntu installed in a LVM setup, with /boot on a seperate partition.

I want to add gentoo into the mix (I have space in the LVM), but I want to keep the grub in Ubuntu.


I made this up theoretically, but would it work?

1. Install Gentoo in the LVM, without grub
2. Setup the Ubuntu Chroot in Gentoo by binding the /dev /proc /sys dirs and mounting the Ubuntu root.
3. Mount the boot partition to the Ubuntu Chroot
4. Symlink Ubuntu's /boot to gentoo's /boot so that the kernels that gentoo installs will land in the right place.
5. Setup a update-grub script on gentoo to run update-grub in the chroot.

Perhaps something like
```

#!/bin/bash
chroot /mnt/ubuntu /usr/sbin/update-grub
```

Thanks for looking! :)

---

