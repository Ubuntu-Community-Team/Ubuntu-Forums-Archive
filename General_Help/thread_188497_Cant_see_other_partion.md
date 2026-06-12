---
title: "Cant see other partion"
date: 2006-06-04
forum: General Help
---

### Post by slimdog360 on 2006-06-04
Today I just bought a new 60Gb hdd for my laptop. When I was choosing how to partion my hdd in gparted, via the ubuntu install, I chose to create a 14GB space for ubuntu, another 14GB space for winxp, aabout 800MB as a linux swap file and the reat as a fat32 partion so I could share file between windows and ubuntu.
I havent installed windows yet but using ubuntu I cant see the fat32 partion.
Can anyone help me out here
thanks

---

### Post by MaX on 2006-06-04
[QUOTE=slimdog360]Today I just bought a new 60Gb hdd for my laptop. When I was choosing how to partion my hdd in gparted, via the ubuntu install, I chose to create a 14GB space for ubuntu, another 14GB space for winxp, aabout 800MB as a linux swap file and the reat as a fat32 partion so I could share file between windows and ubuntu.
I havent installed windows yet but using ubuntu I cant see the fat32 partion.
Can anyone help me out here
thanks[/QUOTE]
Check out bug 337244 at bugzilla.gnome.org
maybe you have the same problem

---

### Post by givré on 2006-06-04
let check first the result of ```
sudo fdisk -l
```
and compare it to your /etc/fstab (which list the partition mount at boot time)

---

