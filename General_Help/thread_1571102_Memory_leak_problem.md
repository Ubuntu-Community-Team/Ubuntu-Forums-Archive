---
title: "Memory leak problem"
date: 2010-09-09
forum: General Help
---

### Post by MARAUDER2003 on 2010-09-09
Hi,

I have a memory leak in 10.04 when I try to update grub2, I'm on a raid 0 set up (fakeraid). This does not happen in 9.10. Does any body have any suggestions to fix this problem? BTW, I'm triple booting but that's not a problem at all. I have an ATI HD 4670 video card but that does not seen to be the problem since the problems manifests right after a fresh install, no video drivers installed. AMD 770/SB710 chipsets. Thanks is advance.

x@x-desktop:~$ sudo update-grub
[sudo] password for x: 
Generating grub.cfg ...
You have a memory leak (not released memory pool):
 [0x9b2a6a0]
You have a memory leak (not released memory pool):
 [0x812b6a0]
You have a memory leak (not released memory pool):
 [0x9e598e0]
You have a memory leak (not released memory pool):
 [0x8e3f6a0]
You have a memory leak (not released memory pool):
 [0x85106a0]
You have a memory leak (not released memory pool):
 [0x9f548e0]
You have a memory leak (not released memory pool):
 [0x9e7a6a0]
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
You have a memory leak (not released memory pool):
 [0x82666a0]
You have a memory leak (not released memory pool):
 [0x9e906a0]
You have a memory leak (not released memory pool):
 [0x99f68e0]
Found memtest86+ image: /boot/memtest86+.bin
You have a memory leak (not released memory pool):
 [0x85496a0]
You have a memory leak (not released memory pool):
 [0x93d36a0]
You have a memory leak (not released memory pool):
 [0x9cfb8e0]
Found Windows 7 (loader) on /dev/mapper/pdc_baajjdaeh2
You have a memory leak (not released memory pool):
 [0x9de86a0]
You have a memory leak (not released memory pool):
 [0x86e66a0]
You have a memory leak (not released memory pool):
 [0x94778e0]
done

---

### Post by TeoBigusGeekus on 2010-09-09
See [this.]("https://answers.launchpad.net/ubuntu/+question/108185")

---

### Post by ronparent on 2010-09-09
I've been noting the same thing with both 10.04 and 10.10 and ignoring it. It probably should be fixed but bigger concerns have been overshadowing it. It doesn't seem to affect anything that I can tell. Would you consider a bug report appropriate?

---

