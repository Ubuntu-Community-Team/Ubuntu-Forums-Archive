---
title: "How to get grub to launch isolinux/syslinux boot menu."
date: 2010-03-20
forum: General Help
---

### Post by narnie on 2010-03-20
Hello,

I'm trying to get a multi-boot setup going for a USB.

I have different vfat-32 partitions I have copied ISOs of several linux distros.

The first one I installed using unetbootin, which works great and uses syslinux, but syslinux can't boot other partitions. So, I have grub installed.

I have gotten so far as to be able to get the grub menu up, but trying to load the partition's isolinux (which is how the Linux Mint LDXE distro boots) gives me an grub error 13.

Here is my menu.1st:

```
default		0

gfxmenu=/boot/gfxmenu/linuxmint.message

timeout		5

color cyan/blue white/blue


title 		Linux
root		(hd0,5)
kernel		/isolinux/vesamenu.c32
```

Not exactly sure what to call for the kernel.

I have also tried the isolinux.bin, but still get the grub error 13.

Can anyone help me figure how to get grub to boot an isolinux menu?

Here is the listing of the /isolinux directory:
```
$ ls isolinux/
boot.cat  isolinux.bin  isolinux.cfg  memtest  splash.jpg  vesamenu.c32
```
And the /boot/grub/:
```
$ ls boot/grub/
default        fat_stage1_5       jfs_stage1_5    reiserfs_stage1_5  xfs_stage1_5
device.map     installed-version  menu.lst        stage1
e2fs_stage1_5  iso9660_stage1_5   minix_stage1_5  stage2
```

Thanks,
Narnie

---

