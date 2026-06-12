---
title: "Kernel custom compilation"
date: 2010-06-29
forum: General Help
---

### Post by Shalaby on 2010-06-29
I've downloaded the latest kernel from kernel.org, extracted, configured, then
$make
$sudo make modules_install
$sudo make install
then i rebooted, i v found the new kernel in the menu,pressed on it,and it gave me this error
kernel panic - not syncing: vfs: unable to mount root fs on unknown-block (0,0)

i think it's related to building ram disk image, i dont know how to do it.

---

### Post by kalistona on 2010-06-29
the new is very instable and not finished.
i do not say that your errors come from that fact.

---

### Post by Shalaby on 2010-06-29
it's been solved :), i used this command to generate initramfs kernel image :
```
sudo update-initramfs -c -k 2.6.34
```
thn i've updated the grub using :
```
sudo update-grub
```
that's it.

---

