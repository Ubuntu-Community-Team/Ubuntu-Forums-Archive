---
title: "Booting a ISO from GRUB2"
date: 2010-04-05
forum: General Help
---

### Post by besweeet on 2010-04-05
I need help booting a ISO in GRUB2. I don't have access to a USB drive or a blank CD. So, under those circumstances, please help me out here.

The ISO is a Windows 7 recovery ISO, because I need to do a startup repair (BOOTMGR is missing).

Here's my GRUB2 entry:
```
menuentry "Windows 7 x64 Recovery ISO" {
	loopback loop (hd0,3)/boot/win7x64recoveryiso.iso
	linux	(loop)/boot/vmlinuz-2.6.31-20-generic root=UUID=d0cfc3c6-fce9-4c24-a443-2ca8452727ad ro   quiet splash
	initrd	(loop)/boot/initrd.img-2.6.31-20-generic
}
```

I'm getting a "you need to load the kernel first" error.

Any ideas?

---

