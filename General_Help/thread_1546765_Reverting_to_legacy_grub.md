---
title: "Reverting to legacy grub"
date: 2010-08-05
forum: General Help
---

### Post by lesliek on 2010-08-05
I installed 10.04 using Wubi.

Updates to grub2 keep breaking everything, so I decided to revert to legacy grub.

I followed instructions for reverting that are in the grub2 community documentation on this site.

All worked well until the final step, running grub-install. It asked me for the device to which I wanted to install grub. I answered /dev/sda, my hard drive.

I got back a message like "/dev/loop0 has no BIOS device". (I apologise for not copying it out verbatim.)

How was I supposed to answer the question?

Leslie

---

### Post by bcbc on 2010-08-05
> **lesliek said:**
> I installed 10.04 using Wubi.

Updates to grub2 keep breaking everything, so I decided to revert to legacy grub.

I followed instructions for reverting that are in the grub2 community documentation on this site.

All worked well until the final step, running grub-install. It asked me for the device to which I wanted to install grub. I answered /dev/sda, my hard drive.

I got back a message like "/dev/loop0 has no BIOS device". (I apologise for not copying it out verbatim.)

How was I supposed to answer the question?

Leslie

Nope - not a good idea. 

Wubi needs the windows bootloader in /dev/sda. Then there's grub4dos (wubildr) that loop mounts and loads the grub menu from the root.disk (which you've replaced with grub-legacy). There probably is a way to get grub4dos to load your grub-legacy, but I don't know this. Older versions of wubi perhaps e.g. 9.04

Anyway, to fix, first reinstall the windows bootloader. Then if you need to get your wubi back, loop mount the root.disk from a live cd. you can then chroot into it and reinstall grub-pc (grub2). Or easier, just back up your important data and reinstall.

If you need help loop mounting or chrooting let me know.

---

### Post by lesliek on 2010-08-06
Thanks for replying, bcbc.

More by good luck than good management, I seem to have recovered from my quandary.

Having uninstalled grub2 and failed in my attempt to revert to legacy grub, but not yet attempted to reboot, I reinstalled (a later version of) the grub2 package. When I was asked to which partition on my hard drive to install grub2, I said none and finished the installation process.

Then, when I rebooted, Ubuntu loaded as usual. I don't know how that happened, but all is well.

Anyway, in light of what you say, I won't attempt the reversion again.

Thanks again,

Leslie

---

### Post by bcbc on 2010-08-06
cool - that's fortunate :)

if you want to play with wubi, you can back up the root.disk first (downside is that this file can be quite big). Then if something goes wrong, you just copy the backup over the current root.disk - and you'll be back where you started. The root.disk is in the c:\ubuntu\disks\ folder (or change c: to wherever you installed wubi)

For regular backups its probably more efficient to backup your data only (/home).

---

