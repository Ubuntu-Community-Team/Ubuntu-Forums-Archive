---
title: "can I unmount my boot partition?"
date: 2010-07-29
forum: General Help
---

### Post by dgw on 2010-07-29
This probably sounds silly, but can I unmount my boot partition after the computer's booted?

edit: it seems I can, since I just did. I guess I should have tried before asking. :D

---

### Post by Ocxic on 2010-07-29
it will mess up any updates that are applied to the kernel/grub tho.

---

### Post by munkyeetr on 2010-07-29
Yeah, after reading your question, I realized that I'd never tried doing it before, so I tried and all seems well.

Not sure *why* I'd ever want to do it...but it seems to be okay.

> **Ocxic said:**
> it will mess up any updates that are applied to the kernel/grub tho.
Good call.

---

### Post by dgw on 2010-07-29
> **Ocxic said:**
> it will mess up any updates that are applied to the kernel/grub tho.
Good point. I'll make sure to have it mounted when I do updates.

The reason why I want to is because I put my unencrypted boot partition on a little flash drive that I can keep with me all the time, and everything on my hard drive is encrypted. If I step away from the computer, I want to take the flash drive with me.

---

### Post by jlparsons on 2011-02-07
Did you try this?  I'd be worried about the flash drive corrupting but I guess you could clone it and keep a backup.

I've been thinking about doing something similar - I'd like to do exactly what you said but also keen an encryption passkey file in the /boot partition too so that the disk is perfectly inaccessible without the usbkey.  Sure you can use brute force but from what I've heard a long and random passkey is effectively unbreakable. (I stand by to be corrected!)

---

### Post by srs5694 on 2011-02-07
I'd like to point out that there are several types of "boot" partition:


[list]
[*]The partition that Linux boots, aka the root (/) partition
[*]The Linux /boot partition
[*]The BIOS Boot Partition, which is used to hold boot loader files on BIOS-based computers that boot using GRUB on GUID Partition Table (GPT) disks
[*]The EFI System Partition (ESP; referred to as an "EFI boot partition" in the Ubuntu 11.04 alpha on EFI-based systems), which holds boot loader files and is required to boot any OS on an EFI-based computer
[*]The boot partition for a non-Linux OS, such as a Windows C: partition
[/list]


It's obvious from the contents of this thread that a Linux /boot partition is under discussion. Some of the other partition types (such as a BIOS Boot Partition or some non-Linux boot partitions) would never be booted; the Linux root (/) partition can't be unmounted; and the ESP, like /boot, can be unmounted.

Unmounting /boot, if it's a separate partition, can be a useful security/safety measure; if the partition isn't mounted, it's hard to accidentally (or maliciously) modify it, so it's hard to accidentally make changes to the kernel or boot loader configuration that might cause problems when you reboot. Likewise, you minimize the risk of filesystem corruption that might damage the kernel in case of a kernel bug, power failure, or whatnot. OTOH, as others have pointed out, if you rely on automatic kernel updates, unmounting /boot might make it possible to accidentally store kernel updates in a useless place. What happens depends on how the package's scripts are written, though. If they're smart enough to try to mount /boot before extracting files and updating GRUB, everything would be fine; if not, the scripts would probably fail and you'd reboot into your old kernel. I've not tested this, though, so I don't know what would actually happen.

---

