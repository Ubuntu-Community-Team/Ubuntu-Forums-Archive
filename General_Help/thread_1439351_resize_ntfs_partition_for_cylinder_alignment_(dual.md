---
title: "resize ntfs partition for cylinder alignment (dual-boot)??"
date: 2010-03-26
forum: General Help
---

### Post by rookworm on 2010-03-26
Hello, I have a dual boot configuration with 9.10 and XP on a Transcend ts32gssd25-m SSD. My performance on XP is sluggish, to say the least, although it is perfect on Ubuntu. It was also fine on a previous installation on a hard disk drive under XP. I tried some basic SSD optimizations, but I'm wondering if there might be a problem with the disk layout. I saw a bunch of websites that suggestion that the ntfs partition should have an initial offset of "128" (Am I correct in assuming any multiple of 128 would also work?). My ntfs partition starts with an offset that is congruent to 32 mod 128. Ideally, I would like to move it over to one that starts at an even multiple of 128. Gparted only seems to let me move things to the nearest megabyte. Is there an easy way to do what I have described without losing any of the partitions on my disk? Thanks.

---

### Post by rookworm on 2010-03-27
could this possibly be effected by using "dd" and and external hard drive? (i.e. back up, repartition, then restore) or would there be some loss of information, or something wrong with the filesystem (I don't really understand how files relate to filesystems and bits on the physical device)

---

### Post by rookworm on 2010-03-29
any ideas??? anybody?  Bueller?

---

