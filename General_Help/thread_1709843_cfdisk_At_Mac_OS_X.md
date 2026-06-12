---
title: "cfdisk At Mac OS X"
date: 2011-03-18
forum: General Help
---

### Post by nathanpc on 2011-03-18
Hello,
 Since Mac OS X, runs a BSD Linux at the core I think that this is the correct place to ask about this, but I need cfdisk to make some ext2 and swap partitions on some Compact Flash and old HDs without needing to download any LiveCD. There is any cfdisk that I can use on my Mac?

Best Regards,
 Nathan Paulino Campos

---

### Post by nathanpc on 2011-03-19
Anyone?

---

### Post by srs5694 on 2011-03-19
You should wait at least 24 hours before "bumping" a thread.

Mac OS X does not use "a BSD Linux at the core," and in fact that's a bit of an oxymoron. The BSD kernels and the Linux kernels are separate and mostly unrelated. OS X uses neither of those kernels; it uses a XNU kernel that's derived from Mach. Atop that, OS X uses a bunch of utilities from the BSD family (mostly FreeBSD), along with a bunch of proprietary Apple software. AFAIK, there are no tools to run Linux binaries on OS X -- at least, nothing short of an emulator like VirtualBox or VMWare.

AFAIK, Linux's cfdisk has never been ported to OS X; however, I might be mistaken in that. OS X does have its own native partitioning tools, though, such as fdisk (for MBR), gpt (for GPT), and diskutil (for either MBR or GPT). Note that OS X's fdisk bears little resemblance to Linux's fdisk in operational details. Also, my GPT fdisk (gdisk/sgdisk) works on OS X as well as Linux, FreeBSD, and Windows.

In case you don't know, MBR is the partitioning scheme used on most PCs. It's widely supported and so is generally the best choice for USB flash drives and other removable media, as well as for BIOS-based computers that boot Windows. GPT is a newer partitioning scheme that's most commonly found on Intel-based Macs. It's also, IMHO, a superior choice for a Linux-only PC. It's necessary for any disk with more than 2^32 sectors (2 TiB, given 512-byte sectors).

---

