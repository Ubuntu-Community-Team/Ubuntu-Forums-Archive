---
title: "Grub problems after raid failure"
date: 2010-09-11
forum: General Help
---

### Post by raccoonone on 2010-09-11
I had a drive fail on my raid5 (created with mdadm), and am now having trouble getting my computer to boot. I've put in a new drive, and rebuilt the array. Although there may have been some problems, as fsck said it fixed a ton of errors.

All the files appear to be on the array, and I can mount it just fine.

However I'm getting a kernel panic that says "VFS: Unable to mount root fs unknown-block(0,0)".

I did some research and it seems that this is due to GRUB being messed up. But while following the directions at: <https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD>. I get a seg fault when trying to run chroot.

Any suggestions?

---

