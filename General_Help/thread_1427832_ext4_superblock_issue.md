---
title: "ext4 superblock issue"
date: 2010-03-12
forum: General Help
---

### Post by Laharl01 on 2010-03-12
I've installed Karmic on an ext4 partition (mount point /, no other partitions on the drive other than swap). This afternoon, I decided I wanted to shrink that partition to make space for a try-it-out install of Debian. This seems to have screwed with the superblocks (yes, all of them) of the partition. The field for the number of blocks in each inode seems to have been unchanged, despite the partition shrinking. I used sg_dd to copy the primary superblock into a file and then [this]("http://pastebin.com/K0TBZNpa") C program to change the field (see below for a link to the superblock format, at least circa ext2) to the correct value. Unfortunately, this didn't work properly, as after using sg_dd to move the superblock back, e2fsck reports that the primary superblock is invalid. Naturally, this means the partition also can't be mounted, nor can I boot normally. I'm currently using a System Rescue CD to try and fix this problem.

As far as I can tell from [http://www.nongnu.org/ext2-doc/ext2.html#SUPERBLOCK](http://www.nongnu.org/ext2-doc/ext2.html#SUPERBLOCK) there's no checksums that would also need updating or anything and I've confirmed that my code puts the right value in the right place by running it a second time on the changed file and the correct value is output. Googling has not produced anything particularly useful about, say, the ext4 superblock format as opposed to the ext2 one.

The commands I used to transfer the superblock back and forth are

```
sg_dd if=/dev/sda5 of=out bs=512 count=8 skip=2 # HD-to-file
```and
```
sg_dd if=out of=dev/sda5 bs=512 count=8 seek=2 # file-to-HD
```I confirmed the commands worked (probably) by backing up the original superblock file and moving it back when e2fsck claimed that the new superblock was invalid. Moving the backup back to the HD caused the original error to reappear.

I'm using a Lenovo Thinkpad T61 with a Hitachi HTS54161.

Any and all help (possibly including a less hackish solution) would be greatly appreciated. Thanks in advance!

---

