---
title: "Help With Deleted Partition"
date: 2012-01-17
forum: General Help
---

### Post by moore.bryan on 2012-01-17
Need some help, folks...

I was cleaning-up my hd by deleting partitions I don't use any more--I dual-booted with MeeGo, OpenSUSE, Fedora, etc. for a while--and came across a btrfs partition. "Hmm," I said in my head, "I don't ever remember creating a partition with *that* file system; must not need it." After all my deletions were done and I rebooted, I figured-out what that partition was for: it was my /boot partition. When I was clean-installing Oneiric a while back I decided to "test-drive" btrfs for my /boot partition. Now, I'm a wee bit screwed because testdrive--and it's off-shoot--don't work with btrfs.

Long story short, I need to find a way to *just* get back my /boot partition and/or create a new one and then reinstall all the boot files/folders onto it; I'm just not sure where to start. Is it as simple as creating a new /boot partition and reinstalling grub?

TL;DR: I'm an idiot.

Thanks for any help you fine folks can provide.

EDIT
Would it be in my best interest to simply follow [this]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall") guide?

---

### Post by TeoBigusGeekus on 2012-01-17
The boot partition holds the kernel - so, if I understand correctly, you've nuked the most important part of your system.
The guide you've linked is for creating a separate boot partition after installation, not generating a new one.
I think you can't escape from a fresh installation...

---

### Post by sudodus on 2012-01-17
But I think the good thing is that your configuration and private files are elsewhere, so it is not too hard to make a fresh install :-)

---

### Post by moore.bryan on 2012-01-17
> **TeoBigusGeekus said:**
> The boot partition holds the kernel - so, if I understand correctly, you've nuked the most important part of your system.
The guide you've linked is for creating a separate boot partition after installation, not generating a new one.
I think you can't escape from a fresh installation...
Makes sense...

> **sudodus said:**
> But I think the good thing is that your configuration and private files are elsewhere, so it is not too hard to make a fresh install :-)
I just was hoping--perhaps beyond hope--I would be able to salvage it somehow...

---

### Post by pbrane on 2012-01-17
If you happen to have a printout of **fdisk -l** or **fdisk -u -l** *before* you deleted the partition you can simply run fdisk to re-create that partition using the same parameters. The only way I know of to "get back" a deleted partition is to know what the parameters were originally. You may be able to figure out what the partition should be by looking at **fdisk -l** and maybe filling in the blanks. It shouldn't be too hard if it was the first partition.

All the data on the lost partition should be fine at this point. Good luck.

---

### Post by moore.bryan on 2012-01-18
> **pbrane said:**
> If you happen to have a printout of **fdisk -l** or **fdisk -u -l** *before* you deleted the partition you can simply run fdisk to re-create that partition using the same parameters. The only way I know of to "get back" a deleted partition is to know what the parameters were originally. You may be able to figure out what the partition should be by looking at **fdisk -l** and maybe filling in the blanks. It shouldn't be too hard if it was the first partition.

All the data on the lost partition should be fine at this point. Good luck.
Would have been helpful to have made one of these things... :redface:

I've reinstalled and am now in the process of trying to replace my setup... it's a shame Ubuntu doesn't have a Nandroid-like program; hmm...

---

