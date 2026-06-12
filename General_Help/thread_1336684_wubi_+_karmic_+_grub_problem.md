---
title: "wubi + karmic + grub problem"
date: 2009-11-24
forum: General Help
---

### Post by aschlosberg on 2009-11-24
I have Karmic installed using Wubi. Everything was working perfectly until this morning when I ran an apt-get dist-upgrade and was told to reboot.

Upon rebooting I now get a GRUB command line interface. With some Googling and my minimal knowledge I have attempted to load the kernel and boot:

```
grub> linux /boot/vmlinuz-2.6.31-15-generic
grub> boot
```

The kernel loading gives me:
[Linux-bzImage, setup=0x3400, size=0x3bf0c0]

Ubuntu starts booting but freezes at a point:

```
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(8,1)

Pid: 1, comm: swapper Not tainted 2.6.31-15-generic #50-Ubuntu

```

I have left out the Call Trace that it prints but let me know if it would help.

Probably irrelevant but the caps and scroll lock LEDs start flashing at this point too.

I would at least like to be able to boot into Ubuntu but if possible how do I have this automated like it used to be?

Thanks for helping a relative newbie :)

---

