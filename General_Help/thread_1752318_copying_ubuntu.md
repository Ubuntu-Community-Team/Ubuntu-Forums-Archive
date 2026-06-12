---
title: "copying ubuntu"
date: 2011-05-07
forum: General Help
---

### Post by TheTinyt1 on 2011-05-07
I am running ubuntu 10.10 on a drive with 3 partitions. 1 windows and 2 ubuntu partitions.

The ubuntu that I am running right now is on a partition that is too small. I need to either expand it to include the other ubuntu partition or reinstall 10.10 and copy my existing partition to it. Can this be down?

I have this version working the way I like it and have tried 11.04 and am holding of for now. Still the fact remains that my working copy is on a partition that is really too small I only have 2 gig free space on a drive that is a 500gig. 

What can I do without loosing what I have right now. 

Any help is appreciated...

TheTiny1

---

### Post by andrewthomas on 2011-05-07
Clone the partition with clonezilla

---

### Post by apollothethird on 2011-05-07
> **TheTinyt1 said:**
> I am running ubuntu 10.10 on a drive with 3 partitions. 1 windows and 2 ubuntu partitions.

The ubuntu that I am running right now is on a partition that is too small. I need to either expand it to include the other ubuntu partition or reinstall 10.10 and copy my existing partition to it. Can this be down?

I have this version working the way I like it and have tried 11.04 and am holding of for now. Still the fact remains that my working copy is on a partition that is really too small I only have 2 gig free space on a drive that is a 500gig. 

What can I do without loosing what I have right now. 

Any help is appreciated...

TheTiny1

There are a number of ways you can go.  You can use clonezilla to back up the partition, then restore it to a new larger partition size.

Alternatively you can use gparted to resize the partition.  I find both programs fairly seamless and easy to use.  With gparted you can delete or resize the other partitions to make them smaller than stretch your Ubuntu partition.

The advantage of using clonezilla to back up your current partion is the advantage of having a backup if something goes wrong.  But again, both programs are very robust and stable.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by TheTinyt1 on 2011-05-07
Thanks, I found both programs and will use clonezilla first as a back up and then I will try to use gparted and see what happens.

Again thanks..

TheTiny1

---

