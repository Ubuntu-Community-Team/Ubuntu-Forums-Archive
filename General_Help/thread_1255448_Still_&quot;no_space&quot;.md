---
title: "Still &quot;no space&quot;?"
date: 2009-09-01
forum: General Help
---

### Post by mimitam on 2009-09-01
I Gparted Vista and in Ubuntu OS Properties, I saw used and **free space on the pie chart and text. There is plenty of space.**

However, I still cannot run anything in Ubuntu due to "not enough free disk space". 

When I used 'df' to look at the disk, the partition was shown as **100% Used.** I also looked at the System Monitor, it also said **available disk space: 0 bytes**.

I thought I did not have to repartition Ubuntu after I repartitioned Vista and that Ubuntu knows to use the free space. Is this true?

Any ideas and suggestions will be very much appreciated.

Thanks...Mimi

---

### Post by mimitam on 2009-09-01
I Gparted Vista and in Ubuntu OS Properties, I saw used and **free space on the pie chart and text. There is plenty of space.**

However, I still cannot run anything in Ubuntu due to "not enough free disk space". 

When I used 'df' to look at the disk, the partition was shown as **100% Used.** I also looked at the System Monitor, it also said **available disk space: 0 bytes**.

I thought I did not have to repartition Ubuntu after I repartitioned Vista and that Ubuntu knows to use the free space. Is this true?

Any ideas and suggestions will be very much appreciated.

Thanks...Mimi

---

### Post by LowSky on 2009-09-01
Ubuntu is as dumb as Vista (actaually no OS knows to do anytihng with a user telling it what to do). You need to use Gparted to increase the size of the partition. Use a LiveCd to do so... you can not do it from a regular ubuntu session.

---

### Post by running_rabbit07 on 2009-09-01
How big is your Ubuntu partition?

In Terminal can you enter ```
fdisk -l
``` then paste the outcome?

---

### Post by earthpigg on 2009-09-01
hi,

can you show us the exact output of this command, please, and put it in [ CODE ] tags?

(minus the space between the [ and C, and E and ]... so, ```
 with UPPERCASE letters.)

[CODE]df -Th -x tmpfs
```

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

### Post by oldos2er on 2009-09-01
> **mimitam said:**
> After I GParted Vista to shrink the partition, on my Visa-Ubuntu dual boot laptop, I looked at the Ubuntu OS Properties and found plenty of space (according to the pie chart).

However, I still could not run anything in Ubuntu due to "not enough free disk space".

When I used 'df' to look at the disk, the partition was shown as 100% Used. I also looked at the System Monitor, it also said available disk space: 0 bytes. Then, I used "fdisk -l /dev/sda" to look at the Partition Table.

It had 2 msgs: "Partition 2 does not end on cylinder boundary" and "Partition table entries are not in disk order"

I thought I did not have to repartition Ubuntu after I repartitioned Vista and that Ubuntu knows to use the free space. Is this true? I must have corrupted my partition table. How can I fix this?

Couldn't use "TestDisk", it looked like it doesn't support Vista or Ubuntu.

Any ideas and suggestions will be very much appreciated.

Thanks...Mimi

 Once you shrink one partition, you then need to expand the next partition into the free space. Other Vista users on this forum have stated that one should use Vista's own disk maintenance tools, not gparted, to do shrink Vista. Once you've done that, use gparted to expand the other partition into the free space.

 If you're running the Ubuntu LiveCD can you please post the output from this command:
```
sudo fdisk -l
```

---

### Post by presence1960 on 2009-09-01
> **mimitam said:**
> After I GParted Vista to shrink the partition, on my Visa-Ubuntu dual boot laptop, I looked at the Ubuntu OS Properties and found plenty of space (according to the pie chart).

However, I still could not run anything in Ubuntu due to "not enough free disk space".

When I used 'df' to look at the disk, the partition was shown as 100% Used. I also looked at the System Monitor, it also said available disk space: 0 bytes. Then, I used "fdisk -l /dev/sda" to look at the Partition Table.

It had 2 msgs: "Partition 2 does not end on cylinder boundary" and "Partition table entries are not in disk order"

I thought I did not have to repartition Ubuntu after I repartitioned Vista and that Ubuntu knows to use the free space. Is this true? I must have corrupted my partition table. How can I fix this?

Couldn't use "TestDisk", it looked like it doesn't support Vista or Ubuntu.

Any ideas and suggestions will be very much appreciated.

Thanks...Mimi

A couple of points. First it is advisable to use Vista's disk management utility to shrink Vista's partition due to a well documented bug in gparted concerning Vista. 

Secondly once you create that space for Ubuntu you have to resize Ubuntu's partition to include that space, it is not automatic. That you can use gparted from the gparted Live Cd or the Ubuntu Live CD to do that.

P.S. here is the link to that bug report in reference to resizing Vista with gparted: [http://bugzilla.gnome.org/show_bug.cgi?id=379482](http://bugzilla.gnome.org/show_bug.cgi?id=379482)

---

### Post by mimitam on 2009-09-01
Thanks very much for the suggestion.

I wish I could use Vista Shrink, it showed zero for shrink size and zero for one other size and made it impossible to use. Then, I resorted to GParted.

I'll use it to repartition Ubuntu as well.

Thanks...Mimi

---

### Post by presence1960 on 2009-09-01
> **mimitam said:**
> Thanks very much for the suggestion.

I wish I could use Vista Shrink, it showed zero for shrink size and zero for one other size and made it impossible to use. Then, I resorted to GParted.

I'll use it to repartition Ubuntu as well.

Thanks...Mimi

Yes, you will have to use gparted to grow the ubuntu partition with the free or unallocated space.

---

### Post by mimitam on 2009-09-01
Thanks very much for the bug link. I really appreciate it.

I could not expand /dev/sda6, ext3 where Ubuntu is. I could only shrink it. It didn't even take a higher MiB number if greater then what's displayed.

I could shrink and expand /dev/sda3 nfs where Vista is, however.

Am I using GParted incorrectly?

Please help.

Thanks...Mimi

---

### Post by aysiu on 2009-09-01
Have you considered using FileLight? It's in the repositories (which I guess you'd have to run off a live CD, since you have no space to install it) and breaks down exactly what is taking up space and how much:
[http://www.methylblue.com/filelight/](http://www.methylblue.com/filelight/)

---

### Post by mimitam on 2009-09-01
Thanks for the link.

From its website, Filelight can create nice charts to show disk consumption data but not able to expand a partition, correct?

---

### Post by aysiu on 2009-09-01
> **mimitam said:**
> Thanks for the link.

From its website, Filelight can create nice charts to show disk consumption data but not able to expand a partition, correct?
Yes, that's correct.

---

### Post by mimitam on 2009-09-01
Thanks very much for the info.

I could not use the Vista Partition Tool because it wouldn't let me (with new size=0). I therefore resorted to using GParted.

I have no free space on any partition but two chunks of "unallocated" space, one very small, the other very big and sandwiched between nfs and ext3.

I could shrink and expand nfs due to its unused space but my ext3 is filled to the max. I could not increase the new size even by one.

I cannot paste "fdisk -l" here (no comm btwn machines at the moment) but it has the error "partition 2 not the end of the cylinder boundary" and the rest correlates to what GParted shows.

Please help. Your thoughts of possibilities of fixing this? I am totally stuck in Ubuntu.

Many Thanks...Mimi

---

### Post by mimitam on 2009-09-01
I cannot paste "df" or "fdisk -l" here (no comm btwn machines at the moment) but it has the error [COLOR=Red]"partition 2 not the end of the cylinder boundary" [/COLOR]and the rest correlates to what GParted shows.

I have no free space on any partition but two chunks of "unallocated" spaces, one very small, the other very big and sandwiched between nfs and ext3.

I could shrink and expand nfs due to its unused space but my ext3 is filled to the max. I could not increase the new size even by one.

Any suggestions? I am so stuck in Ubuntu.

Many Thanks...Mimi

---

### Post by mimitam on 2009-09-01
I tried using GParted to expand Ubuntu (/dev/sda3, nfs).

The Resize/Move of this Ubuntu partition didn't even take a higher MiB number if my input is greater then what's displayed which made sense. I have two chunks of "unallocated space", but not "free space". The Ubuntu partition has no room to grow anywhere.

The "unallocated space" Resize/Move button is grayed out.

I could shrink and expand /dev/sda3 nfs where Vista is, however. This will increase or decrease the big "unallocated" chunk space also next to ext3.

However, I have no free space on any partition but two chunks of "unallocated" spaces, one very small, the other very big and sandwiched between nfs and ext3.

I could shrink and expand nfs due to its unused space but my ext3 is filled to the max. I could not increase the new size even by one.

I cannot paste "df" or "fdisk -l" here (no comm btwn machines at the moment) but it has the error "[COLOR=Red]partition 2 not the end of the cylinder boundary" [/COLOR]and the rest correlates to what GParted shows.

Thoughts on how to fix it?

Many Thanks...Mimi

---

### Post by P4man on 2009-09-01
have a look at this excellent how to:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by mimitam on 2009-09-01
This link is indeed very helpful. Thank you very much.

I did as instructed but could have messed things up already. I have 3 pending operations in GParted (shrink Windows, expand the 'light blue' container box and expand ext3. I hit APPLY once and a few seconds later, I canceled the operations.

This is because I realized that I needed to allocate Ubuntu with more space. I re-dragged the 3 items properly and hit APPLY the 2nd time. The 3 revised pending operations are running now.

I knew I needed to reboot Windows using the Vista OS boot CD and then repair it before I can bring Vista up again. How about Ubuntu, same things?

Thanks again very much...Mimi

---

### Post by oldos2er on 2009-09-01
A word of friendly advice, next time please only start one thread per subject. It'll make things easier both for you and those who answer you.

---

### Post by mimitam on 2009-09-01
Yes, I will take that to heart the next time. Sorry for the extra noise.

My problem is solved! Thanks very much to the help that I got from folks in this Forum.

Much Obliged...Mimi

---

### Post by mimitam on 2009-09-01
I have to apologize for my multiple postings on this topic in this Forum. I  did not think my original posts took because I couldn't see it and in desperation, I repeated the thread. My bad.

Problem solved! Thanks very much to all your help!

Much Obliged...Mimi

---

### Post by mimitam on 2009-09-01
My problem has been solved! Thanks so very much for all your help!

Much Obliged...Mimi

---

### Post by mimitam on 2009-09-01
I have to apologize for the multiple postings that I put up here. Not intentional but still my bad!

My problem has been solved. Thanks so very much for all your help.

Much Obliged...Mimi

---

### Post by presence1960 on 2009-09-01
Great! Enjoy Ubuntu.

---

### Post by bapoumba on 2009-09-02
All 4 threads merged in here.

---

