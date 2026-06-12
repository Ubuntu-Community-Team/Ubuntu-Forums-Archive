---
title: "e2fsck badblocks doubt."
date: 2012-09-28
forum: General Help
---

### Post by melrokz on 2012-09-28
Will the changes made to the bad block inode table be permanent? Will it survive a disk format?

1. # e2fsck -c /dev/sda1
where /dev/sda1 is an ext4 partition on an old hdd with bad sectors.

2. Install Ubuntu (the partition will be formatted with ext4 file system)

3. Will the bad blocks still be marked as such? If not, how do I install Ubuntu on a disk with bad sectors?

---

