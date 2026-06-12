---
title: "Multi-HDD GRUB problems"
date: 2010-01-06
forum: General Help
---

### Post by Irihapeti on 2010-01-06
My desktop computer's original HDD has Ubuntu 8.04 on one partition and 9.10 on another. I'm using Grub legacy in Hardy as the boot manager, with no problems.

That is, until I acquired another HDD from a family member. After I installed this, I've found that I can still boot up just fine in Hardy, but Karmic has been doing weird things.

Specifically, Hardy still thinks that the original drive is /dev/sda, but Karmic has this idea that it's /dev/sdb. Not sure why, as the original drive is the default boot drive in the BIOS, but there it is.

So, here's a good reason for using UUIDs, I guess - except that Karmic won't recognise them. I get a message to the effect that the partition doesn't exist and the (initramfs) prompt. Running update-initramfs fixed some other problems (other partitions not mounting) but not this one.

Anyone got any ideas as to what's going on - and how to fix it?

---

### Post by wkulecz on 2010-01-06
> So, here's a good reason for using UUIDs, I guess

Still not worth the hassles UUID mounts cause when restoring from backups.  Anything that hinders getting back up quickly after a hardware failure is a too negative to contemplate any alledged pluses.

The 9.10 grub2 install may not honor your BIOS' idea of which is the first drive.  I had this issue initially, system wouldn't boot.  If I swapped drive order in the BIOS then it would boot,  The solution was to edit the /boot/grub/device.map file to make the drive order match the order I wanted in the BIOS.  Then run grub-update again (or was it update-grub?)  A return to the bad old days of "don't forget to run lilo" when making boot changes.  So far grub2 is all pain, no gain for me.  Step backwards as far as I'm concerned at this point.

--wally.

---

### Post by Irihapeti on 2010-01-06
Actually, I've never liked UUIDs very much myself, because when I format a drive, they change. But I thought they were supposed to handle precisely this kind of situation where the /dev/sdX definitions were liable to change. Seems like they don't.

Also, I didn't make it clear that I'm using Grub legacy. I've got no grub installed in 9.10 at all.

---

