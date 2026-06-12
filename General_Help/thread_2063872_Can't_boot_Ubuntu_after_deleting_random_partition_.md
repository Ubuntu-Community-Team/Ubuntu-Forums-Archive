---
title: "Can't boot Ubuntu after deleting random partition on other HDD"
date: 2012-09-28
forum: General Help
---

### Post by Pithikos on 2012-09-28
I got a new laptop(Samsung NP530U3C) which comes with 24GB of  a SSD and a 500GB hard disk. I installed Ubuntu on the SSD and made a  ext4 partition on the hard disk for saving media files. Boot loader got  installed on the hard disk as BIOS doesn't let me to boot from the SSD.


  Everything worked fine until I deleted the ext4 partition on the hard  disk. Since then I cannot boot Ubuntu and I am not sure how to fix the  problem without having to reinstall Ubuntu.


  How can I revert the boot loader to the hdd? Would really appreciate some help :)

---

### Post by agillator on 2012-09-28
By deleting that partition you changed the structure as GRUB knew it and, even though it was not the boot partition, GRUB now cannot find what it needs. You need to reinstall GRUB (not Ubuntu, just GRUB). See the section on 'Reinstalling Grub 2' at [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing). Hang on to the directions and keep good notes. This can happen anytime you make a change to partitions or drives that affect the boot process. For example deleting a partition can change the partition numbers which will make it impossible for GRUB to boot until updated/repaired.

---

### Post by Pithikos on 2012-09-28
Ok, I finally solved it by booting with a Live CD and using the tool **boot-repair** :P

---

