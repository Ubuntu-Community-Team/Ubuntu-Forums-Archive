---
title: "Natty 11.04. Problem with grub2."
date: 2012-01-17
forum: General Help
---

### Post by waterlink on 2012-01-17
I have installed ubuntu natty 11.04 server, i have 3 hdd and my installation ubuntu on /dev/sdc

grub can't boot, only grub-rescue shows up
command set gives:
prefix=(ubuntu-root)/boot/grub
root=ubuntu-root

ls gives:
(hd0) (hd0,msdos1) (hd1) (hd1,msdos1) (hd1,msdos2) (hd1,msdos5)

this commands make my system to boot:
prefix=(hd1,1)/boot/grub
root=hd1,1
insmod normal
normal

and it goes, but i want it to boot normally

so the question goes: how to change prefix and root, which are recorded in MBR ?

--------------

reinstall of grub2 did not help at all, still it looks for ubuntu-root, "ubuntu" is name of computer for this system (default from installation)

---

