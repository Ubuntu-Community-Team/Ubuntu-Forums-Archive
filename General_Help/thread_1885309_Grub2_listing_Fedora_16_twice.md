---
title: "Grub2 listing Fedora 16 twice"
date: 2011-11-22
forum: General Help
---

### Post by EvilRick on 2011-11-22
I have a triple boot setup on one drive and am only using Grub2 from Ubuntu 10.04.

When I run ```
sudo update-grub
``` I get ```
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 16 (Verne) on /dev/sda6
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
done
```

When I reboot I have two listings for Fedora.  I removed all the unused kernels from Ubuntu.  Do I need to do the same in Fedora?

---

### Post by EvilRick on 2011-12-06
For those that are interested (care) . . .

I ran ```
su -c 'package-cleanup --oldkernels --count 1'
``` from within Fedora and it removed the unused kernel.  It's back to just showing the three OS entries in GRUB2.

---

