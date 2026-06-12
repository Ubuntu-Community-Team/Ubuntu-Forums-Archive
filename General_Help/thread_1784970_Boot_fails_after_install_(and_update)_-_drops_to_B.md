---
title: "Boot fails after install (and update) - drops to BusyBox with &quot;ALERT! /dev/disk/..."
date: 2011-06-17
forum: General Help
---

### Post by dwigyit on 2011-06-17
I've just reinstalled Ubuntu to fix a problem with sound that I had caused myself :(

I had to install grub manually after the install, but I've had to do that a few times before and there's been no problem. GRUB loads fine and I can select the Ubuntu option, but it simply stays on a purple screen with no HDD activity. When I go into recovery, it falls to a busybox command-line and says "ALERT! /dev/disk/by-uuid/(string of letters and numbers) does not exist". I use a RAID array which causes me loads of problems, but I'm fairly sure, from what I've read of similar problems, that this is due to the update it did during installation. I suppose I could try installing it without internet connection, but then presumably the same thing would happen as soon as I ran update-manager? I have actually tried the reinstall several times as well as reinstalling GRUB. Please help me if you can :)

---

### Post by dwigyit on 2011-06-17
Ok I think the kernel update is the issue - or at least the update of something. I've reinstalled Ubuntu without internet connection (so no updates) and it works perfectly (apart from GRUB install, but nothing new there). 

I'm going to avoid updating the kernel though, until I have a fix for the error I described in my first post, or unless one of you thinks it's unlikely to repeat if the update is installed by update manager as opposed to the installer.

EDIT - it worked fine when I installed without the update, and then when I updated using Synaptic (update manager would probably work too), the system still booted fine. So problem solved ;)

---

