---
title: "Ubuntu and openSUSE kernels difference"
date: 2010-06-16
forum: General Help
---

### Post by wirate on 2010-06-16
I dont know much about kernels and their commands. To boot Ubuntu livecd from iso using grub2, the following entry is used

```
menuentry "Lucid ISO on /dev/sda1" {
loopback loop (hd0,1)/home/drs305/Desktop/ubuntu-10.04-beta2-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/drs305/Desktop/ubuntu-10.04-beta2-desktop-amd64.iso noprompt
initrd (loop)/casper/initrd.lz
}

```

Here /casper/vmlinuz (kernel or loader?) uses iso-scan/filename but the kernel with opensuse livecd (/boot/i386/loader/linux) does not recognize it.

I want to know what command (kinda) the opensuse kernel uses in place of iso-scan/filename so that i can boot the iso image through grub.

thank you

---

### Post by wirate on 2010-06-17
bump?

---

