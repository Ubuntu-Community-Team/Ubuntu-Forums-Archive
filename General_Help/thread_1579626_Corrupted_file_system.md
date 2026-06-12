---
title: "Corrupted file system"
date: 2010-09-22
forum: General Help
---

### Post by raccoonone on 2010-09-22
Somehow the file system on my computer seems to have become corrupted, and I'm trying to troubleshoot it.

I have 3 drives in raid5 (using mdadm) for /
and 2 drives in raid1 (also through mdadm) for /home

I'm getting error messages from GNOME, and can't boot to the desktop. Additionally, switching to another terminal and trying to use vim gives a seg fault.

I suspected a hardware problem at first, but neither raid is degraded, so that seems to rule out hdd/sata controller problems, and the fact that it doesn't crash seems to rule out cpu/ram.

Does anyone know of edge case software problems that could have caused this kind of data loss? I'm running Ubuntu 10.04 x64, ext4, and grub2.

Or anyone have ideas?

---

