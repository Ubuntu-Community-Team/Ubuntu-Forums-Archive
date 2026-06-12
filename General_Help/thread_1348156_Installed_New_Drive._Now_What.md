---
title: "Installed New Drive. Now What?"
date: 2009-12-06
forum: General Help
---

### Post by snorkytheweasel on 2009-12-06
Added new drive. Now what?
My PC came with a 200 gb sata drive. I slicked the disk (to remove xp) and installed karmic koala. That works well. Partitions are sda1, sda2, sda5. I thought I installed lvm, but pysdm says that I have ext2.

Then I added a 320 gb sata (it was a refugee from Vista), and wiped the new drive clean. Now it has 1 partition - sdb1. I thought I created the file system as lvm, but using pysdm, it says that I have ext3.

My impression is that using lvm as a file system that I can create 1 volume that contains all of the disk space from both drives.

However, I'm not clear what I have for disk space. My goal is to have sd*1 and sd*2 plus 1 big partition for sd*5. sd*5 should be in the neighborhood of 500 gb.

Using my limited repertoire of tools & skills - df, ls, nautilus, dolphin - I can't tell what is where.

How do I determine if I have the desired partitions and what disk space I have available?

If I missed the mark, how do I accomplish that goal of having 1 big volume (short of buying a 3rd drive and creating a striped set)?

In the worst case scenario, I can simply reinstall karmic from scratch, but I prefer to learn to use the tools that will accomplish what I want.

---

### Post by Ocxic on 2009-12-06
LVM is a partitioning scheme, your still gonna have an ext2/3 or other type of filesystem.

try installing gparted it will help with volume management.

"df -h" is for free space and "sudo fdisk -l" will list all or your partitions

---

