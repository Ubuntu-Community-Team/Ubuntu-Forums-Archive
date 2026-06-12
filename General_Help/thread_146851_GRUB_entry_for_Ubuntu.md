---
title: "GRUB entry for Ubuntu"
date: 2006-03-19
forum: General Help
---

### Post by ffi on 2006-03-19
Hi my grub bootloader was on another partition which I reformatted, could someone tell me what the GRUB entry should be for kernel 2.6.15-18 ?

---

### Post by mwaddoups on 2006-03-19
For normal mode and recovery mode, mine looks like this:
```

title		Ubuntu, kernel 2.6.15-18-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-18-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-18-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-18-386
boot

```

---

### Post by ffi on 2006-03-19
thanks, do you have the memtest entry too? (although I have no idea what it does :s )

---

### Post by ffi on 2006-03-19
The first entry doesn't seem to work, the recovery mode does, I get error 15 file not found, is there a typo there somewhere?

---

### Post by chettyk on 2006-03-19
Simply changing the GRUB file 'menu.lst' isn't going to solve your problem. You need to reset GRUB so that it looks to your current boot partition, not the earlier partition.  Have a look at the following:

[http://ubuntuos.com/2006/03/howto-restore-grub.html]("http://ubuntuos.com/2006/03/howto-restore-grub.html")

[Recovering Grub manually ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8")

If you search this forum, you'll find other threads dealing with GRUB recovery.

---

### Post by ffi on 2006-03-19
It's one of the options which is giving a problem like "safedefault"  or "ro quiet splash"  because when I delete those the kernel boots....

---

