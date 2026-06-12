---
title: "Move /tmp onto its own partition?"
date: 2010-07-27
forum: General Help
---

### Post by L a r r y on 2010-07-27
I have run into the issue of running out of space.  I am running my filesystem (mount point /) in a 14 gig partition, ext3 filesystem, and it is 30% full, according to: 
```
df -h
```

My Home is in a separate partition, and I am using a swap partition.

I have a couple big partitions formatted to ext4, and attempted to use fstab to mount one of these as /tmp.  Upon reboot I ended up in error and had to boot from a Linux live CD to restore fstab.

I think I did the right thing, but I didn't take it far enough.

Another thread addresses this issue, in that the O.P. has already done an install of Ubuntu 9.04 with /tmp already in its own partition.  He wants to change it to another partition instead.

I multi-quoted his thread, and started a reply, then copied that reply text into here, and discarded my reply there.

My details differ, in that he is running version 9.04 and I am running 10.04, and that he is already in a different partition with his /tmp folder, and mine is still in the filesystem / partition.

I copied a line in my /etc/fstab that already works, to mount a big partition in /mnt/backups+music, and changed the details.

This is the old last line of fstab, followed with the new line to move /tmp:
```
/dev/sda1	/mnt/music+backups			ext3	relatime	0	2
/dev/sdb1	/tmp					ext4	relatime	0	2

```

The partition is labeled "tmp."

**It is at this point that I restarted the computer and could not boot up in my first attempt.**

I propose the following steps to do this right, and seek your thoughts on whether this will work as proposed.

1A. Boot into safe mode.

1.  I restore my fstab settings as described above, but do not boot yet.

2.  I mount my designated partition currently at /media/tmp, then 

3.  Perform a version of the O.P's code:
```
cd /tmp
find . -depth -print0 | cpio --null --sparse -pvd /media/tmp

```
(Replaced O.P's "/test" with "/tmp" and replaced his "/tmp" with "/media/tmp," respectively.)

4.  Perform a ```
sudo chmod 1777 /media/tmp
```

5.  Reboot.


Upon reboot, the new /tmp should take hold, as /media/tmp goes away.

[B]I would appreciate your comments.  Thank you.
 -- Larry[/B]

O.P's post titled "**[ubuntu] move /tmp to new partition:**

> **fboecom said:**
> I have created a 9.04 install with a separate /tmp partition. I changed my mind and wanted to have tmp on another partition. With some intermediate steps, the fstab is now mounting the new partition as /tmp and the old tmp partition as /test. In safe mode I copied everything out of /test into /tmp following an instruction I found in this forum (on moving the /home directory):

```
cd /test
find . -depth -print0 | cpio --null --sparse -pvd /tmp

```
that worked well, the two directories look the same. When I boot in normal mode, I can login, but immediately get an error message, of which the details are:



what do I have to do to move /tmp in the right way?

> **geirha said:**
> Have you set the correct permissions on your new /tmp?
```
sudo chmod 1777 /tmp
```

> **fboecom said:**
> ..and that was all it took to get my ubuntu desktop back again!!
Thanks geirha!

(command executed in recovery mode console)

---

### Post by Zorgoth on 2010-07-27
/tmp should be formatted as ext2 as it does not need to store persistent data and therefore does not need journalling - not that that helps you with your fstab problem.

Apart from that, I don't know much about mount options, but defaults has always been fine for me on /tmp.

---

### Post by L a r r y on 2010-07-31
> **L a r r y said:**
> 
I copied a line in my /etc/fstab that already works, to mount a big partition in /mnt/backups+music, and changed the details.

This is the old last line of fstab, followed with the new line to move /tmp:
```
/dev/sda1	/mnt/music+backups			ext3	relatime	0	2
/dev/sdb1	/tmp					ext4	relatime	0	2

```

The partition is labeled "tmp."


I propose the following steps to do this right, and seek your thoughts on whether this will work as proposed.

1A. Boot into safe mode.

1.  I restore my fstab settings as described above, but do not boot yet.

2.  I mount my designated partition currently at /media/tmp, then 

3.  Perform a version of the O.P's code:
```
cd /tmp
find . -depth -print0 | cpio --null --sparse -pvd /media/tmp

```
(Replaced O.P's "/test" with "/tmp" and replaced his "/tmp" with "/media/tmp," respectively.)

4.  Perform a ```
sudo chmod 1777 /media/tmp
```

5.  Reboot.


Upon reboot, the new /tmp should take hold, as /media/tmp goes away.



I've gone ahead with my proposed steps and had to make some adjustments, so here for the record is what I did:

I started within a normal boot, and edited my fstab to add the last line as outlined above.  


1.  I restore my fstab settings as described above, but do not boot yet.

2.  I mount my designated partition currently at /media/tmp, then 

3.  Before I do anything else, Perform a ```
sudo chmod 1777 /media/tmp
```


4.  Perform a version of the O.P's code:
```
cd /tmp
find . -depth -print0 | cpio --null --sparse -pvd /media/tmp

```
(Replaced O.P's "/test" with "/tmp" and replaced his "/tmp" with "/media/tmp," respectively.)

5.  Reboot.


Upon reboot, the new /tmp took hold, as /media/tmp went away.


Now were I to have this to do all over again, I would have formatted the future /tmp partition to ext2 per Zorgoth's suggestion (Thanks!) instead of ext4, and I would have given it maybe 10 gig instead of in excess of 40 gig.  I may follow similar procedure to move one of the larger directories in / to a new partition if need be.

Now I could set up a new tmp partition, downsized a bit and set to ext2, and just edit fstab, then follow the steps again.  Step 4 would again copy /tmp to /media/*****.

Thanks for the input.

PS:  Since /tmp is chmod 1777, I was able to create a temp folder in /tmp for a program, but it did not remain after I restarted the computer.  Hmmm.

---

### Post by worksofcraft on 2010-07-31
Does not System->Administration->Storage Device Manager
have everything you need to do this?

p.s. Also the place for temporary files that won't get cleared out every time you boot is /var/tmp

---

### Post by louieb on 2010-07-31
> **L a r r y said:**
> ... I was able to create a temp folder in /tmp for a program, but it did not remain after I restarted the computer.  Hmmm.

/tmp - gets cleaned out at every reboot. Thats just the normal Linux way.

---

