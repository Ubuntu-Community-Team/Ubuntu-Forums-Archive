---
title: "Change USplash for Ubuntu Custom LiveCD"
date: 2010-02-01
forum: General Help
---

### Post by Clownox on 2010-02-01
Hi all, im in progress create custom livecd for my university, i want to change usplash for livecd, but i never success yet, when i replace the *.so file or install it from .deb file usplash never change, coz when i try 

```
# update-initramfs -u
```

i got this error message

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
cryptsetup: WARNING: could not determine root device from /etc/fstab
```

i thougt its because the emptyness of my /etc/fstab, then i try to put / (/root) into this blanks /etc/fstab, then try update-initramfs again, it success but after package into ISO and try it,its not change the usplash

really need help..sorry for my really bad english.. :(

---

