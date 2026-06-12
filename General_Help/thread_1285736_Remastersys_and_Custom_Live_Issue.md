---
title: "Remastersys and Custom Live Issue"
date: 2009-10-08
forum: General Help
---

### Post by slice16 on 2009-10-08
Morning All,

I was hoping you guys could shed some light on an issue I am having with my own custom ISO created in remastersys. Here is the basic setup:

USB hard drive with grub and a basic menu.lst. I have copied both the ubuntu desktop iso and the custom one created in remastersys to the /

In menu.lst, I have the following lines:

```
Ubuntu Live CD 
map /ubuntu-9.04-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-9.04-desktop-i386.iso quiet splash locale=en.UTF-8 --
initrd /casper/initrd.gz


title Custom 
find --set-root /bootbteit/bteit-live.iso
map /bteit-live.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/bteit-live.iso  locale=en.UTF-8 --
initrd /casper/initrd.gz
```

The basic ubuntu.iso loads up without issue on a variety of machines. However, when I try booting from the custom iso, I get a large number of the following messages:

```
kjournald starting. Commit interval 5 Seconds
EXT3-fs: mounted filesystem with ordered data mode.
```

After around 5 minutes, ubuntu drops into the Busybox shell. I'm not a linux expert, but from what I can gather linux can't correctly mount the intramfs image? 

At first I thought it was a faulty ISO, but I have created a few now, and made them contigous. 

Your help would be much appreciated, I have spent a few days on this now, and realised my linux knowledge isn't where I hoped it was :)

Cheers all,

Paul

---

### Post by slice16 on 2009-10-08
bump :)

---

