---
title: "ClusterF... of a hard drive"
date: 2010-09-14
forum: General Help
---

### Post by iamjfarrell on 2010-09-14
I am not 100% what I have done to my Hard Drive but it is cluttered with partitions. I want to know what I should eliminate and what I should keep.

I think it is from multiple different installs. I had some troubles with it before. 

[IMG]http://imgur.com/6URXz.png[/IMG]

Windows Vista I am tempted to get rid of on this computer because it doesn't even really work. I could use the space, but that is for another day. The 3 different swaps I don't think I need. I am unsure about what is going on with the Ext 4 and the extended.

---

### Post by garner_nc on 2010-09-14
Looks like you have 3 primary partitions and 1 extended partition which is divided into 3 logical partitions.

Primaries are Vista, 16GB home, and 9 GB swap.
Extended is 40GB which is broken into the 3 logicals listed under it.

You could probably delete the 2 smaller swaps and then recreate a single logical partition out of that space. Unless you have 6 Gigabytes of memory the 9gb swap is overkill.

Doing a back-up of /home then doing a clean install may be your best answer. You can merge all those partitions into one then divide as required.

All the Best,
Doug W.

---

### Post by iamjfarrell on 2010-09-14
> **garner_nc said:**
> Looks like you have 3 primary partitions and 1 extended partition which is divided into 3 logical partitions.

Primaries are Vista, 16GB home, and 9 GB swap.
Extended is 40GB which is broken into the 3 logicals listed under it.

You could probably delete the 2 smaller swaps and then recreate a single logical partition out of that space. Unless you have 6 Gigabytes of memory the 9gb swap is overkill.

Doing a back-up of /home then doing a clean install may be your best answer. You can merge all those partitions into one then divide as required.

All the Best,
Doug W.

Thanks for the great answer. I might do a fresh install soon. Only reason I won't right now is because I just got everything perfect and school is in. By the way, I live in Garner, NC. Small World.

---

