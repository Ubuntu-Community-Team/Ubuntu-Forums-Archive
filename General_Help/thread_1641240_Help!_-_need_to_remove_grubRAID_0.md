---
title: "Help! - need to remove grub/RAID 0"
date: 2010-12-08
forum: General Help
---

### Post by steelman2202 on 2010-12-08
EDIT - SOLUTION in last post. 

Hi all! 

I have run into an issue with my PC. When I installed ubuntu to a partition on one of my hard drives it seems to have installed grub somewhere onto my raid array. I have two 74gb raptors running in raid 0 on an Asus A8N-SLI Deluxe. The ubuntu install is elsewhere, on a partition on a separate, single sata drive. 

The windows 7 loader, (W7 is my primary OS) is intact. However, there are certain things that do not work anymore with grub installed. (Like the num lock light always boots off, no matter what I do, and my Win7 system can no longer hibernate)

Rather than trying to sort out the issues, I am hoping just for now, to simply remove the grub loader - but I've been unable to do so. 

I've booted from my Win7 DVD, loaded appropriate raid drivers - and done the bootrec /fixboot and /fixmbr commands. - No change. The grub loader always comes before my Win 7 loader, and the windows loader is simply piggy-backed on top of it.

Please help!

Thank you!

-K

P.S. The raid and all other partitions on my system, sans the Ubuntu one, are NTFS. The ubuntu one is some shape of EXT something...

Ubuntu can't even see the raid array, since I've never installed the appropriate drivers. It just sees the drives as two, and not formatted. 

Reinstalling windows would be a massive nuisance, and is to be avoided unless absolutely necessary.

AFAIK - when I installed, it was a basic full install of ubuntu on a blank partition.

---

### Post by dcstar on 2010-12-08
> **steelman2202 said:**
> Hi all! 

I have run into an issue with my PC. When I installed ubuntu to a partition on one of my hard drives it seems to have installed grub somewhere onto my raid array. I have two 74gb raptors running in raid 0 on an Asus A8N-SLI Deluxe. The ubuntu install is elsewhere, on a partition on a separate, single sata drive. 

The windows 7 loader, (W7 is my primary OS) is intact. However, there are certain things that do not work anymore with grub installed. (Like the num lock light always boots off, no matter what I do, and my Win7 system can no longer hibernate)

Rather than trying to sort out the issues, I am hoping just for now, to simply remove the grub loader - but I've been unable to do so. 

I've booted from my Win7 DVD, loaded appropriate raid drivers - and done the bootrec /fixboot and /fixmbr commands. - No change. The grub loader always comes before my Win 7 loader, and the windows loader is simply piggy-backed on top of it.

Please help!

Thank you!

-K

P.S. The raid and all other partitions on my system, sans the Ubuntu one, are NTFS. The ubuntu one is some shape of EXT something...

Ubuntu can't even see the raid array, since I've never installed the appropriate drivers. It just sees the drives as two, and not formatted. 

Reinstalling windows would be a massive nuisance, and is to be avoided unless absolutely necessary.

AFAIK - when I installed, it was a basic full install of ubuntu on a blank partition.
This will allow you to put the Grub bootloader somewhere else:
```
sudo dpkg-reconfigure grub-pc
```
You BIOS is booting Grub from wherever you installed it, if Windows is not booting then that may be a BIOS issue.

---

### Post by steelman2202 on 2010-12-09
that is a marvelous tool! thank you.

I've got it now where none of the grub options are checked - it basically means grub is uninstalled, i guess. However, it is still there, on bootup.

It did give me a couple of errors in regards to having the wrong number of pieces in my raid array. (I think it thought that each drive was one part of a pair, but with two completely separate pairs)

Any ideas?

Thanks again!

---

### Post by steelman2202 on 2010-12-09
solved by:

deleting the ubuntu partition in windows.
then running the Win7 startup repair without loading the raid drivers.

---

