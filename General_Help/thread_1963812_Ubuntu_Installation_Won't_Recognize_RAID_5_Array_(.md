---
title: "Ubuntu Installation Won't Recognize RAID 5 Array (Setup in BIOS)"
date: 2012-04-23
forum: General Help
---

### Post by astrostu on 2012-04-23
The subject line says the basics, but I'll elaborate:

**Software Setup:**  1 120GB SSD that has a Windows 7 Enterprise 64-bit installation alongside Ubuntu v11.10 install via wubi (20GB of space allocated to it).

**Hardware Setup:**  3 1TB HHDs that were set up as a RAID 5 array through going into the BIOS, setting the SATA Mode to RAID, and then using the Intel Rapid Storage Technology Option ROM utility to set these three into a RAID 5.  After that, Windows would not boot, so I went back in the BIOS and switched the SATA Mode back to ACHI.  Windows booted fine, and it saw the drives as one ~2GB drive.  I formatted it as NTFS and loaded some stuff on it.

**The Goal:**  The purpose of this RAID 5 setup (all three HDDs) is to be seen by both Windows and Linux, and it needs to be RWX in both operating systems.  Basically a shared data "drive."

**The Problem:**  Linux won't (1) see these as a RAID array, it sees them as separate drives, and (2) mount them individually nor as the RAID array it won't see.

**What I've Tried:**  Not much 'cause I knew pretty much 0 about Linux before this morning and now know 0+epsilon about it.  Another SSD (60GB) is readable by both, but then I had to reformat it in Linux for ext4 so that I could read/write/execute from it (and use ext2explore to view it in Windows).  Since I need this to be easily read/writeable by both Linux and Windows, attempting reformats like that aren't really an option at the moment.

Please help?  And thank you for your time in helping me get a solution.

---

### Post by dcstar on 2012-04-23
> **astrostu said:**
> The subject line says the basics, but I'll elaborate:

**Software Setup:**  1 120GB SSD that has a Windows 7 Enterprise 64-bit installation alongside **Ubuntu v11.10 install via wubi** (20GB of space allocated to it).
..........

Don't expect Ubuntu to work fully when you install inside Windows.

Install it properly as dual boot.

---

### Post by astrostu on 2012-04-23
Well, after fighting with the installer for several hours, installing several times, I could not get grub to recognize the Linux partition.  I tried everything I could find online.  I finally screwed up enough that nothing would boot and I just started over from scratch.

Started with Windows in its own partition rather than re-sizing.  Recreated the RAID5 - it appears to have been somehow damaged as parts were not recognizable, but re-doing it worked.  Then installed Linux in the other partition.  It's now working and sees the RAID.

But two issues remain:

1. **grub Not Seeing Windows:**  Grub is not listing the proper Windows Boot Manager from the proper disk.  The Windows disk is on /dev/sdd1, but it's trying to go to /dev/sdda1 which is the 60GB SSD data disk.  Yes, I think there's like a 100MB Windows storage thing on there, but when it tries to boot using it, it fails and brings me back to grub.  My work-around at the moment is to keep going back to the BIOS and switching the boot order between "ubuntu" and "Windows Boot Manager."  I can do this, I suppose, but there should be a better solution?

2. **RAID 5 still changing permissions:**  The RAID5 is formatted ntfs so that Windows can read/write to it.  Linux is now mounting it, and I can copy files to it, but anything copied to it changes the permissions to [d/-]rw[x/-]------.  sudo chmod doesn't have any effect.  *Some*how, I was actually still able to run one software application from it, so it *might* be okay (I still need to do some more testing, but this seems very odd to me and I can't figure out how to make Linux just see it like a normal disk and not change permissions.

---

