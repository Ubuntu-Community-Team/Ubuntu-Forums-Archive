---
title: "Adding a third OS to GRUB?"
date: 2009-08-02
forum: General Help
---

### Post by ron3090 on 2009-08-02
Hello! This will probably be pretty quick. I've successfully added Windows 2000 to GRUB along with Xubuntu, and now I want to add my Windows XP installation. It's on my third hard drive (sdc1). Here's my menu.lst file:
> default 0
timeout 10
hiddenmenu

title Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=12613613-f773-4c00-ad19-01d539d5872d ro quiet splash
initrd /boot/initrd.img-2.6.24-24-generic
quiet

(lots of older kernels)


title Ubuntu 8.04.3 LTS, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title=Windows 2000
map	(hd1)	(hd0)
rootnoverify	(hd1,0)
chainloader	+1 
makeactive
boot



---

### Post by nikhilbhardwaj on 2009-08-02
perhaps this'll help

title=Windows XP
map (hd2) (hd0)
rootnoverify (hd2,0)
chainloader +1 
makeactive
boot

---

