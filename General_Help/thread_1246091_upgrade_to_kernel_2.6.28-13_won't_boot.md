---
title: "upgrade to kernel 2.6.28-13 won't boot"
date: 2009-08-21
forum: General Help
---

### Post by CryptiniteDemon on 2009-08-21
So I downloaded updates yesterday and I rebooted to find this message:

udevadm trigger not permitted while udev is unconfigured
AlERT /dev/disk/by-uuid... does not exist


I'm able to boot into my old kernel just fine in the grub menu.  Both menu options even have the same UUid, so I don't understand the error.

```

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=52f2e69c-484b-42fd-91e7-0ff60ddce862 ro quiet splash vga=0x369
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=52f2e69c-484b-42fd-91e7-0ff60ddce862 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=52f2e69c-484b-42fd-91e7-0ff60ddce862 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=52f2e69c-484b-42fd-91e7-0ff60ddce862 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

---

### Post by fooman on 2009-08-21
open a terminal and try this command:

```
sudo aptitude reinstall udev
```

then this one:

```
sudo update-initramfs -u -k all
```

see if that helps.

---

### Post by CryptiniteDemon on 2009-08-21
Perfect.  Thank you much sir.

---

