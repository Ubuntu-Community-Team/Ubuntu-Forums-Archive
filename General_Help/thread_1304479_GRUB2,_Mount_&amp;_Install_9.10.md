---
title: "GRUB2, Mount &amp; Install 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Legace on 2009-10-29
Hello focus,

I've got Ubuntu 9.04 with GRUB2 currently installed. Would it be possible to mount the Ubuntu 9.10 ISO via GRUB2, and actually install Ubuntu from there?

I was thinking of something like this: (ISO on Windows partition sda5, located in **\Misc\ISO** folder)

```
menuentry "Karmic Live CD (sda5)" {
loopback loop (hd0,5)/my-ISO/ubuntu-9.10-beta-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/Misc/ISO/ubuntu-9.10-desktop-amd64.iso
initrd (loop)/casper/initrd.lz
}
```

---

