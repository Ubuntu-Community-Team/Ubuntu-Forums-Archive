---
title: "Understanding DF Output"
date: 2009-08-15
forum: General Help
---

### Post by zeepal on 2009-08-15
Hello Guys,

Im wondering if you can help me understand the "DF" command's output:

**Command:** df -kh
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda2             458G  4.9G  430G   2% /**
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  340K  989M   1% /var/run
varlock               989M  4.0K  989M   1% /var/lock
udev                  989M  128K  989M   1% /dev
tmpfs                 989M     0  989M   0% /dev/shm
lrm                   989M  2.5M  987M   1% /lib/modules/2.6.28-14-server/volatile

I am guessing the following:
Size = Total HDD Size
Used = Total space used on HDD
Avail = Total free space on HDD

If the above is true why when I do:
Size - Used = 453.1GB
but 453.1GB doesn't = Avail its out by 23.1GB

I have a feeling Avail means something other than free but Google hasn't helped me in finding out.

Hopefully you guys can.

---

### Post by Slim Odds on 2009-08-15
By default, ext2 or ext3 file systems reserve 5% of the partition for root.

As I've mentioned in many threads, that was OK when drives were small. But now that they are massive, it's a huge overkill.

You can change it (no need to unmount) by using tune2fs with the -m option.

5% of 458G is 22.9G

---

### Post by blueridgedog on 2009-08-15
The root space reservation is something that is difficult to come by in searches (or so it appeared to me when trying to help another forum user with a similar question).

---

### Post by Slim Odds on 2009-08-15
> **blueridgedog said:**
> The root space reservation is something that is difficult to come by in searches (or so it appeared to me when trying to help another forum user with a similar question).

That may be true, but there are tons of posts here about this issue.

---

### Post by blueridgedog on 2009-08-15
> **Slim Odds said:**
> That may be true, but there are tons of posts here about this issue.

True, but the search here is pretty unimpressive.

---

### Post by zeepal on 2009-08-15
Hello Guys,

Thanks for your assistance with this (sorry i didnt find other threads like this).

How much should you reserve for root or what do you reserve for root? (prefer in GB as % won't help with large drives as Slim Odds pointed out)

-----
Below are just some SEO words/phrases to assist others in finding this thread:
df incorrect
df wrong
df inconsistent
missing gb
missing gigabytes
gigabytes missing
gb missing
df Avail
df doesnt look right
df doesn't look right
df showing wrong usage
-----

---

### Post by dcstar on 2009-08-16
> **zeepal said:**
> 
How much should you reserve for root or what do you reserve for root? (prefer in GB as % won't help with large drives as Slim Odds pointed out)


You can always use different filesystems like reiserfs (that make all blocks available, if you want that).

---

### Post by blueridgedog on 2009-08-16
> **zeepal said:**
> Hello Guys,

Thanks for your assistance with this (sorry i didnt find other threads like this).

How much should you reserve for root or what do you reserve for root? (prefer in GB as % won't help with large drives as Slim Odds pointed out)



A gig should be overkill.  Even if you reduce it further, in the event of a disk full scenario you could always boot from a LiveCD and delete files.

There are thousands of things that can go wrong and cause you / partition to fill up, usually due to a user goof or a process gone astray.  The reservation for root keeps the system functional and bootable in such cases.

---

### Post by zeepal on 2009-08-16
Hello Guys,

I perfer EXT3 at the moment.

Ok I will setup for 1GB for my home servers.

Thanks for your input guys/girls (im not sure which sorry).

Have a good night...

---

