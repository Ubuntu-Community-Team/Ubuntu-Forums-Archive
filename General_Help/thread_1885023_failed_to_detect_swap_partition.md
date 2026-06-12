---
title: "failed to detect swap partition"
date: 2011-11-22
forum: General Help
---

### Post by esteban82 on 2011-11-22
When I run this command on terminal:
[INDENT]sudo update-initramfs -u -k all
[/INDENT]appears:
[INDENT]update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda6

[/INDENT]I have no idea what to do, some suggestions?

Thanks!

---

### Post by esteban82 on 2011-11-22
forse manca da qui UUID?

[INDENT]/dev/disk/by-uuid/

[/INDENT]perhaps missing from here UUID of swap, how can I add it?

---

### Post by F.G. on 2011-11-22
i had to move my swap a while back, this thread might, should help:

[http://ubuntuforums.org/showthread.php?t=1811742](http://ubuntuforums.org/showthread.php?t=1811742)

good luck.

---

