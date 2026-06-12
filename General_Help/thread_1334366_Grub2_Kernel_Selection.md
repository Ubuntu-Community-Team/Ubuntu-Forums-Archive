---
title: "Grub2 Kernel Selection"
date: 2009-11-22
forum: General Help
---

### Post by benl11235 on 2009-11-22
I always want grub2 to scan the images available and ask me which I want to boot. I boot my system by live cd, so this is a necessity.  Is there anything wrong with the one below?


# Entry 0 - Load Linux kernel
menuentry "Linux" {
insmod lvm
set root=(haven-gate)
linux /vmlinuz root=/dev/haven-gate
initrd /initrd

---

