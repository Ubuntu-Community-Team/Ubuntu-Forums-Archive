---
title: "&quot;Not enough free disk space&quot; in Ubuntu after already GParted Vista?"
date: 2009-09-01
forum: General Help
---

### Post by mimitam on 2009-09-01
After I GParted Vista to shrink the partition, on my Visa-Ubuntu dual boot laptop, I looked at the Ubuntu OS Properties and found plenty of space (according to the pie chart).

However, I still could not run anything in Ubuntu due to "not enough free disk space".

When I used 'df' to look at the disk, the partition was shown as 100% Used. I also looked at the System Monitor, it also said available disk space: 0 bytes. Then, I used "fdisk -l /dev/sda" to look at the Partition Table.

It had 2 msgs: "Partition 2 does not end on cylinder boundary" and "Partition table entries are not in disk order"

I thought I did not have to repartition Ubuntu after I repartitioned Vista and that Ubuntu knows to use the free space. Is this true? I must have corrupted my partition table. How can I fix this?

Couldn't use "TestDisk", it looked like it doesn't support Vista or Ubuntu.

Any ideas and suggestions will be very much appreciated.

Thanks...Mimi

---

### Post by P4man on 2009-09-01
You shrunk the vista partition, but did you grow the ubuntu one? Ubuntu won't use unpartitioned space automagically. also don't worry too much about those messages, both of them see warnings to me, not errors. Its okay if your partitions are not in disk order.

---

### Post by mimitam on 2009-09-01
Thanks very much for the info.

I tried using GParted to expand Ubuntu (/dev/sda3, nfs).

The Resize/Move of this Ubuntu partition didn't even take a higher MiB number if my input is greater then what's displayed which made sense. I have two chunks of "unallocated space", but not "free space". The Ubuntu partition has no room to grow anywhere.

The "unallocated space" Resize/Move button is grayed out.

I could shrink and expand /dev/sda3 nfs where Vista is, however. This will increase or decrease the big "unallocated" chunk space also next to ext3.

Your thoughts on how to fix it?

Many Thanks...Mimi

---

### Post by P4man on 2009-09-01
You dont have to grow unallocated space, that is just space;.not allocated, therefore, not used :)

You have to grow the Ext3 volume now. boot from a live cd, run partition editor, swap off the swap partitions (right click, swap off). Then you resize the ubuntu partition.

If the ubuntu partition is inside an extended partition (light blue), you will have to grow that one first. Its like a container. After that, grow the ubuntu partition (inside the extended partition).

If you dont manage, post a screenshot of the partition editor.

---

### Post by drs305 on 2009-09-01
I wrote a guide about expanding / in response to failed installs resulting in a 2.3GB / partition. Although this doesn't apply to you, the partitioning advice does and may be helpful.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by mimitam on 2009-09-01
Thank you so much to P4man. It worked and I was overjoyed. I took a 2nd look at ext3 and it was still 100% used.

So I went in again to shrink nfs and expand both ext3 and its container. Now, I think I had the space split reasonably. I hit Apply and it is now applying the 3 pending operations.

I knew Vista will not boot. I will try to boot it from CD like the last time and see what happens. On the Ubuntu side, should I boot from the Live CD as well for the 1st time?

Have I messed up things already, you think?

It will take several hours to do these 3 operations. Hopefully, I can boot both up afterwards.

What do you think?

Many Thanks...Mimi

---

### Post by mimitam on 2009-09-01
Thank you very much for the link you gave me as well, drs305. I appreciate it. It will go into my tool box.

---

### Post by mimitam on 2009-09-01
P4man, it worked! :D

Thanks so much for your brief and precise instructions.

Much obliged...Mimi

---

