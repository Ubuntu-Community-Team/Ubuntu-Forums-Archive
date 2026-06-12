---
title: "Access fakeRaid in 11.4 Live Distro"
date: 2011-08-03
forum: General Help
---

### Post by Allubz on 2011-08-03
Dear all,

I recently replaced my old motherboard (Gigabyte GA-MA785GMT-UD2H) with a new one (Gigabyte GA-990FXA-UD7). I expected my RAID-0 with OS to be working flawless but it turns out that it doesn't and I need to access some files before formatting and reinstalling the OS.

In order to get access I thought of getting a Live CD/DVD, like Ubuntu's. It doesn't automatically detect the array so I went on and installed 'mdadm' through a terminal.

Upon entering: mdadm -As
I get: No arrays found in config file or automatically

Facts:
- New motherboard has been configured for RAID
- New motherboard detects array
- The OS can load up to a specific point but then BSOD's (yes, it's that kind of OS)
- Ubuntu 11.4 live detects all hard drives (2x Single, 2x the array disks)
-- I can only access the single disks. The array disks only show up in GParted

What I need is to access the array somehow, to backup some files and then get a proper OS running on it (I'm strongly tending to a Linux alternative).

Any help on this would be much appreciated!
2x Western Digital Caviar SE16 250GB

---

