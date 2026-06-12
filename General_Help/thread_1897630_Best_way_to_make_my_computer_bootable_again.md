---
title: "Best way to make my computer bootable again"
date: 2011-12-19
forum: General Help
---

### Post by dempa on 2011-12-19
On my computer, I have winXP, Ubuntu, and MintOS installed. I keep the linux distros for fun, but mainly use winxp. I noticed some drives in "My Computer", many with large sizes (~50GB). I didn't know what it was, so i right-clicked and hit format on one of them. I didn't touch any of the other ones, but now when I try to boot, I get:

```

GRUB loading.
error: no such disk
grub rescue>

```
I'm not sure if I no longer have GRUB, but I have at least one Linux distro still installed.
Is it easier/possible to use GRUB from that, or to burn a ubuntu live cd and reinstall Grub from there?

---

### Post by kanikilu on 2011-12-19
Assuming you didn't blow away your entire partition (although it kind of sounds like it), I think you could try reinstalling Grub from the Ubuntu CD/USB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dempa on 2011-12-19
> **kanikilu said:**
> Assuming you didn't blow away your entire partition (although it kind of sounds like it), I think you could try reinstalling Grub from the Ubuntu CD/USB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Assuming I did, how do I ensure that I remove all previous forms of Linux when reinstalling a fresh copy of Ubuntu? Will the space released by doing this be forced into the new Ubuntu partition, or is there a way to format it in NTFS and utilize it with my current Windows XP installation?

---

### Post by kanikilu on 2011-12-19
To just remove all previous linux partitions, you can choose to manually partition during a new Ubuntu installation. Just remove any existing non-NTFS/Fat32 partitions on the disk (probably ext4, Swap or raw/unformatted if they were deleted from Windows) and then create new ext4 and swap partitions to install to.

If you wanted to use some space for Windows, you could probably use a GParted Live CD/USB to expand the current Windows partition if there is free space before or after that partition. As always, make sure to back up any important data before changing the partitions.

---

### Post by piratebill on 2011-12-19
You might be able to use testdisk to restore that partition.  I'd boot off a live cd, install testdisk and cross your fingers

---

### Post by dempa on 2011-12-19
I'll try that tomorrow and get back to you on how it went. Thanks so much.

---

### Post by dempa on 2011-12-20
I just installed Ubuntu, removed all but fat16/fat32/ntfs/swap partitions, and restarted. I am still getting:

```

error: no such disk
grub rescue>

```

---

### Post by mastablasta on 2011-12-20
assuming you didn't install Linux using wubi you need to repair/restore grub
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
if oyu installed Ubuntu using wubi (windows installer) then you need to look here: 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

