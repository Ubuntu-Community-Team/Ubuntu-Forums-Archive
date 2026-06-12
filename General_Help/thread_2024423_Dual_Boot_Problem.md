---
title: "Dual Boot Problem"
date: 2012-07-13
forum: General Help
---

### Post by joruss1 on 2012-07-13
I had Ubuntu 11.04 and Fedora 16 installed as a dual boot configuration.  I downloaded Ubuntu 11.10 and installed it and the dual boot doesn't happen.  I thought 11.10 would only update 11.04 and leave the dual boot in place.
What should I have done to leave the dual boot in place?

---

### Post by Rexilion on 2012-07-14
You don't provide detail. So this will be an educated guess.

Maybe you overwrote the Fedora bootloader on the MBR of the (primary?) disk instead of the first sector of the partition you installed Ubuntu on?

---

### Post by Shadius on 2012-07-14
We do need more details. I can only guess that you downloaded the Ubuntu 11.10 image, created a LiveCD, and used that LiveCD to install Ubuntu 11.10. The Ubuntu 11.10 LiveCD should've asked you if you wanted to install alongside your current dual-boot or use the entire disk. It looks like you used the entire disk, and had Ubuntu 11.10 take over, thus, eliminating your other operating systems. Those are just my assumptions though because you haven't given details. Depending on what your primary operating system was, the install might have overwritten the MBR like the previous user suggested. In that case, try running from a Terminal in Ubuntu or Fedora:
```
sudo update-grub
```
This will update GRUB to display the other operatings systems, if any, on the GRUB menu.

---

### Post by oldfred on 2012-07-14
If you installed Fedora to its default it used LVM. Ubuntu's desktop does not include the LVM drivers as default so you need to add them. Someone also posted the os-prober only finds Fedora if it is mounted first.

Is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)

sudo apt-get install lvm2

---

