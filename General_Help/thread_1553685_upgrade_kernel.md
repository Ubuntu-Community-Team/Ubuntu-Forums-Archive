---
title: "upgrade kernel"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Either I am incredibly stupid, or the rest or the people that upgrade kernels are incredibly clever... anyway,

I tried to upgrade to 2.6.35 (in lucid btw), because that might solve the never ending issues of alsa 1.0.23 in combination with HDMI.

```

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-headers-2.6.35.15
sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

```

1) I expected 2.6.35 to pop up in the update-grub output.
2) I have linux-headers-alsa drivers installed. they also go with a version number like "2.6.32". Is that going to give me trouble? Should I find a matching linux-headers-alsa version with my kernel version?
3) I have proprietary drivers for nvidia gt 220 and broadcom wireless driver. Am I going to get trouble for those proprietary drivers? Are the depending on a certain linux kernel?

If anybody has answers on 1 of those questions, highly appreciated!

Thanks.

In the meanwhile, i'm trying to figure out what to do here.

---

### Post by User-007 on 2010-08-15
You should also install linux-image-2.6.35.15. After that update grub and you should find a new row in the grub.

User JB

---

### Post by bprins on 2010-08-15
Yeah ran into linuxkernels.com, they had a section for ubuntu as well. 

So now I've got 2.6.35 kernel. After boot I found that my wireless wasn't working. I opened hardware-drivers to check the status of my proprietary driver which was unloaded. I tried to activate, but I got an error doing so.

Do I need to find a new proprietary driver that matches the 2.6.35 kernel? If so, where and how can I find that driver?

If you guys need the error I can reboot back into the new kernel and post it back here.

Lots of thanks in advance.

PS: any kind of information related to kernels and proprietary drivers that you can throw at me is appreciated. If I can learn something out of all this; would be great.

---

### Post by User-007 on 2010-08-15
Hmm. I think you would make the troubleshooting much easier if you told us the detailed information of your wireless device.

User JB

---

### Post by bprins on 2010-08-15
Broadcom driver from lshw:
```

product: NetLink BCM57780 Gigabit Ethernet PCIe
vendor: Broadcom Corporation

```

after pressing "activate" in hardware drivers to re-activate broadcom STA driver:
```

2010-08-15 20:29:32,437 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-08-15 20:29:32,483 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-15 20:29:34,590 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-15 20:29:34,794 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-15 20:29:34,829 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

Thanks!

---

