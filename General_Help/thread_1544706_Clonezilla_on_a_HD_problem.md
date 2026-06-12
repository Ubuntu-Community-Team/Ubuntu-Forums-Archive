---
title: "Clonezilla on a HD problem"
date: 2010-08-02
forum: General Help
---

### Post by vnv on 2010-08-02
Hi,

I am trying to put clonezilla on my hard drive so I can boot it from grub menu.

Problem is that it works with version 1.2.2-31 but it doesn't work with version 1.2.5-35-i686 and 1.2.5-35-484.

Computer is Intel platform.

Old version boots normally but new ones report that initramfs is missing, failing as debian boot problem.

What could be the problem, why the older version works and new one doesn't ??? :confused:

Here is my grub menu.lst.

```

title        Clonezilla backup system
root        (hd0,3)
kernel        /clonezilla/live-hd/vmlinuz boot=live union=aufs vga=791 ip=frommedia live-media-path=/clonezilla/live-hd bootfrom=/dev/sda4 toram=filesystem.squashfs
initrd        /clonezilla/live-hd/initrd.img


```

---

