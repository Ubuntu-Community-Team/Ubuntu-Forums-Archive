---
title: "HIdden System reserved"
date: 2011-09-03
forum: General Help
---

### Post by pedro_kangkong007 on 2011-09-03
good day.., if this is a repost im sorry pls delete. thnx
i would appreciate your help very much

recently i installed my pc with ubuntu 10.04 in my 500GB HDD (deleted all my partition with windows and formatted it with Ubuntu set up)

but i wanted to dual boot it with win xp.., so i deleted my partition it with gparted and to my 
surpise i only have 465 GB HDD now...:confused::confused:
and then i tried win xp utility to delete my partition but still it was 465 GB:(

i tried using seagate tools the makers of my HDD and write zeros on it
but still it was 465 GB HDD:mad:
no bad sector was found  ](*,):evil:

has someone encountered this thing before? is there a hidden partition like a system reserved perhaps, and what i can i do to regain my 35GB space..

---

### Post by Consecrated on 2011-09-17
From: [http://uk.answers.yahoo.com/question/index?qid=20090522072623AAp4EfL](http://uk.answers.yahoo.com/question/index?qid=20090522072623AAp4EfL)

"Actually, the 1000 vs. 1024 thing does not *really* apply to hard drives, only memory.

When discussing memory, a "gig," is really a Gibibyte (1024^3 bytes, abbreviated GiB), not a Gigabyte (1000^3 bytes, abbreviated GB). Computers "think" in binary, so everything is numbers that can be factored only by 2.

This is *not* the case with storage. Manufacturers can make storage in any size -- not just sizes factorable only by 2. So, a 500 GB hard drive is 500 Gigabytes (500 x 1000^3 bytes).

In theory -- in practice, hard drives are rated by "size class." So a 500 GB hard drive is in the 500 GB size class, which means *pretty close to* 500 GB.

To add to the confusion, most operating systems use the JEDEC standard definition of GB, in which a GB is 1024^3 bytes! 

So, your 500 GB hard drive should have a size of 

500,000,000,000 bytes.

Your OS will recognize it as a 465.7 GB drive, but, by that, it means

500,000,000,000 bytes

Because when your OS says GB, it really means GiB.

Hope this helps!"

---

