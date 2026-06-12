---
title: "Routine drive check?"
date: 2009-08-05
forum: General Help
---

### Post by Messyhair42 on 2009-08-05
so about every 30 or so mountings, durring boot, Ubuntu checks my HD partitions. today it checked my /home partition, a whopping 877 GB, I knew it would take a while, but it stalled for quite a bit around 6200 of 7500 (disk sectors? cylinders? i dont know) anyway i left it to run and when i came back it had booted just fine but is something like this normal?

---

### Post by ubudog on 2009-08-05
> **Messyhair42 said:**
> so about every 30 or so mountings, durring boot, Ubuntu checks my HD partitions. today it checked my /home partition, a whopping 877 GB, I knew it would take a while, but it stalled for quite a bit around 6200 of 7500 (disk sectors? cylinders? i dont know) anyway i left it to run and when i came back it had booted just fine but is something like this normal?

I believe it is :D

---

### Post by ubudog on 2009-08-05
It is routine. :D

---

### Post by synapsys on 2009-08-05
Yea it's normal. Ubuntu runs fsck against your filesystem every 30 boots by default. Fsck checks your root filesystem for consistency, it does not check your physical hard drive for defects.

---

### Post by ubudog on 2009-08-05
> **synapsys said:**
> Yea it's normal. Ubuntu runs fsck against your filesystem every 30 boots by default. Fsck checks your root filesystem for consistency, it does not check your physical hard drive for defects.

What happens if it finds a defect?

---

### Post by synapsys on 2009-08-05
> **ubudog said:**
> What happens if it finds a defect?

Fsck will fix most filesystem errors. If it can not, it will give you an error message. 
To check your hard drive for physical defects, you need to run a program like badblocks.

---

### Post by ubudog on 2009-08-05
> **synapsys said:**
> Fsck will fix most filesystem errors. If it can not, it will give you an error message. 
To check your hard drive for physical defects, you need to run a program like badblocks.

Ok.  Thanks! :)

---

### Post by lensman3 on 2009-08-06
You can use tune2fs to change the number of boots between a fsck.  Look at the -c command.  If you are using ext3 or ext4, the journaling file system, I really don't think you have to do a fsck.

---

