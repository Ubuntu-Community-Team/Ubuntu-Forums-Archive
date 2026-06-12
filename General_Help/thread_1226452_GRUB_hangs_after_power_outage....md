---
title: "GRUB hangs after power outage..."
date: 2009-07-29
forum: General Help
---

### Post by jgoney on 2009-07-29
Hi everybody!

We recently had a power outage which messed up my disks a little bit. After the incident, it booted with no problem but my RAID was missing. I got that working again and then didn't think twice about it.

Well, then I moved the whole system into a new case, and now it hangs on the GRUB screen (it takes literally several minutes even for it to display 'GRUB' on the screen). I've removed all unnecessary peripherals for testing, and I ran an 'e2fsck -fv' on my boot disk (from the installer CD) and it came back clean. I also reinstalled GRUB from the rescue disk, and that didn't help either.

In order to rule out any hardware problems, I installed Ubuntu (server) on a different disk. It installed and ran 100% normally. So I'm pretty sure there's something funky going on with my boot drive.

Anyone have any ideas as to what might be causing this and how to fix it? If all else fails, would I be able to clone my system disk's data, reformat the disk (including the MBR) and add it again? I would rather not have to configure all those programs again.

Any advice is appreciated. Thanks!

 - Justin

---

