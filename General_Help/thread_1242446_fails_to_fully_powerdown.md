---
title: "fails to fully powerdown"
date: 2009-08-17
forum: General Help
---

### Post by bacchusmarsh on 2009-08-17
hey,
i am running 9.04 on a Toshiba Te2100, mostly loving it but....
When i shut down it sticks on the last screen where it says "40229.712878 Power down."(The numbers vary each time) and i have to force shutdown .
Having already searched the forums i have tried a few things including changing the menu.lst here: 

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32a9e899-87d5-4f51-838d-109b7eccea0e ro **acpi=force**

and here:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		32a9e899-87d5-4f51-838d-109b7eccea0e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=32a9e899-87d5-4f51-838d-109b7eccea0e ro quiet splash **acpi=force lapic**
initrd		/boot/initrd.img-2.6.28-14-generic

but to know avail.
Does anybody have any other suggestions or knowledge on this issue?

---

### Post by bacchusmarsh on 2009-08-17
i found this post useful, 
[http://ubuntuforums.org/showthread.php?t=1195684&highlight=powerdown]("http://ubuntuforums.org/showthread.php?t=1195684&highlight=powerdown")

i think i should update the bios, can any body advise how best to do this?

I have a Toshiba TE2100, running ubuntu 9.04

---

