---
title: "how to create more than 4 partitions?"
date: 2010-08-23
forum: General Help
---

### Post by superarthur on 2010-08-23
I bought a new notebook, and am trying to dual boot windows 7 and ubuntu
So I am trying to format my D drive partition into swap and ext4.
However, I am not allowed to do so because there are already 3 partitions;
PQSERVICE (which is a spare copy of windows 7), Windows 7 recovery environment, and the main ntfs data drive.
I believe that I require at least 2 partitions for swap and the main ubuntu partition. That makes 5 partitions in total. (in fact, I wanted to have one partition for root, and one for everything else, which makes 6 in total)
What should I do?

---

### Post by LowSky on 2010-08-23
You need to first make a Extended partition first, then you can formate the ther partitions within the extended one.

---

### Post by pastalavista on 2010-08-23
Create an extended primary partition and in it you can have as many logical partitions as you like.

---

### Post by superarthur on 2010-08-23
how to do that? can i do that with GParted?

---

### Post by anirudhtomer on 2010-08-23
your MBR structure has 4 "16 byte entries" each corresponding to a partition...so u can have 4 partitions at the max...to create more u can make one of them extended partition...haven't tried GParted for that...google it man

---

### Post by superarthur on 2010-08-23
I can't find the button for extended partition in GParted :'(

---

### Post by superarthur on 2010-08-23
I found the button now.
I couldn't just format the partition into an extended one. I had to delete the old partition first,  start a new partition, and then I have the option to make it an extended one.

---

### Post by indytim on 2010-08-23
A couple of items:

1.  It can be done quite easily within GParted.
2.  The extended partition that you are going to create will be your 4th.
3.  You will need to create unallocated space within your hard drive where the extended partition will live.
4.  If you are going to reduce the size of a windows partition(s), the conventional wisdom is to do that within a Windows utility vs doing it from GParted.  This applies to the later vintage windows ops in particular.
5.  Generally speaking, to resize partitions expect it to take a fair amount of time in GParted.
6.  When doing things in GParted, it is my **strong** recommendation to do one task at a time.  Do not gang operations together.
7.  Run GParted in a LiveCD vs from a booted Linux ops.  You can do this either by downloading and burning the GParted LiveCD from their site or booting into your Ubuntu LiveCD.

Hope this helps clarify things.

IndyTim / DataMan

---

### Post by imbjr on 2010-08-23
"A note of caution: XP appeared to refuse to install under an extended partition - it wanted a primary partition. I've not idea if Windows 7 has changed in this regard."

Actually, I just noticed that's not what you are attempting to do. Yes, the 4th partition should be an extended one, with the Linux-related partitions under it.

---

### Post by WorMzy on 2010-08-23
Very good advice.

> **indytim said:**
> 
4. If you are going to reduce the size of a windows partition(s), the conventional wisdom is to do that within a Windows utility vs doing it from GParted. This applies to the later vintage windows ops in particular.

6.  When doing things in GParted, it is my **strong** recommendation to do one task at a time.  Do not gang operations together.

These two points in particular I can't stress enough.

I've personally had no trouble installing Windows XP (and other varieties) to an extended partition, but I use OEM disks, rather than recovery disks, so that may be the reason why.

---

