---
title: "dosfsck refuses to fix drive /dev/sda2"
date: 2011-01-08
forum: General Help
---

### Post by AndyCanfield on 2011-01-08
Ubuntu Linux 10.04 LTS -

Partition dev/sda2 is formatted as FAT32 and mounted as /d. Boot found a problem with it; the original and backup copies of the boot sector  don't match.

dosfsck refuses to fix it. I use 'dos fsck /dev/sda2" and it offers to copy one to the other, but whatever I pick it refuses to write to the drive. I  use "dosfsck -a /dev/sda2" and again it refuses to write to the drive. How can I fix this Must I reformat the partition?

(This is being posted from another computer)

---

### Post by Rubi1200 on 2011-01-08
Hi and welcome to the forums :)

From a LiveCD, run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please as well as the specifications for the computer.

Thanks.

---

