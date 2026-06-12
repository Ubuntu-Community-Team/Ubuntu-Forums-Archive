---
title: "How to rebuild /boot?"
date: 2010-07-22
forum: General Help
---

### Post by plalloni on 2010-07-22
I've lost the disk that contained the /boot directory of a 9.10 installation.

All other important partitions/directories are on a raid0 and working ok.

So, I started trying to repair the system by booting from Ubuntu 9.10 live cd, creating a new partition on a new disk for /boot, mounting all partitions in its place for a chroot environment, doing the chroot, and then trying several reinstalls of packages which I supposed where enough for rebuilding /boot (linux kernel & grub), then I ran something like grub-setup which installed a new MBR on the new disk.

Everything went ok, but when I reboot the new installation it gets me to a text mode login screen and of course I want to recover the previous configuration which ran gdm and auto login into GNOME I had before.

After that I tried reinstalling some other packages like gdm but now the boot process "hangs" on the boot splash screen.

Any pointer on what I need to do or reinstall would be appreciated a lot.

---

### Post by plalloni on 2010-07-23
Being a new user in this forum, maybe I've missed some forum protocol when I posted this?

---

