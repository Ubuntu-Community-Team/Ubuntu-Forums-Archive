---
title: "How would I go about implementing this partitioning scheme...is it possible?"
date: 2009-11-18
forum: General Help
---

### Post by sefs on 2009-11-18
What I want to do is this....

It is one HDD.

I want 3 partitions

1st partition
----------------
/

2nd partition
--------------
/home
/var

3rd partition
-----------------
swap

Is it possible to get a setup like that on the 2nd partition?

Thanks.

---

### Post by djk44883 on 2009-11-18
Yes, it's possible... but no not exactly like that.

> 2nd partition
--------------
/home
/var

Is asking for 2 partitions.  So your set up would actually include 4.  Which is possible.  You can have several logical partitions within an extended one.  

If you use the graphical installer, you most likely won't even be confronted with which type.  Just specify the size you want and mount point.

DJ

---

### Post by Cheesemill on 2009-11-18
Someone may prove me wrong but I'm 99.999% sure that's impossible.

What are you trying to achieve? There may be a different solution.

---

### Post by sefs on 2009-11-18
Here is what I am trying to achieve...

I want root on its own partition with out /var because for what i am doing /var grows too fast and the partition runs out of space. But i don't want to make the / partition any bigger.

So I created a separate partition for /var...but then the problem was it had unused space...quite a bit where was wasted...

/home has it's own partition

So I was thinking maybe i can merge /var /home into one partition and just have a small /root partition and the remaining space as /var and /home where they can grow as they like in the remaining space.

Thanks.

---

### Post by mechro on 2009-11-18
From what I can figure out from the manpage a device(partition) is mounted to a directory and not the other way round. So if you did mount sda2 /home and then mount sda2 /var the second one would apply.

I suppose you could put /var in your /home directory??

---

### Post by Cheesemill on 2009-11-18
Sounds like you're after LVM.

It's not that complicated (although alot of the descriptions make it seem that way).

For more info check out these links:

[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)
[http://www.tuxradar.com/content/lvm-made-easy](http://www.tuxradar.com/content/lvm-made-easy)
[http://workaround.org/ispmail/lenny/basic-debian-installation](http://workaround.org/ispmail/lenny/basic-debian-installation)

The last one is a mail server how-to but has one of the best LVM explanations I've found, just scroll down to the LVM section, it's about a quarter of the way down (make sure you read to the bottom as it gives you the commands to resize a partition).

---

### Post by mechro on 2009-11-18
> **Cheesemill said:**
> Sounds like you're after LVM.

It's not that complicated (although alot of the descriptions make it seem that way).

For more info check out these links:

[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)
[http://www.tuxradar.com/content/lvm-made-easy](http://www.tuxradar.com/content/lvm-made-easy)
[http://workaround.org/ispmail/lenny/basic-debian-installation](http://workaround.org/ispmail/lenny/basic-debian-installation)

The last one is a mail server how-to but has one of the best LVM explanations I've found, just scroll down to the LVM section, it's about a quarter of the way down (make sure you read to the bottom as it gives you the commands to resize a partition).

Here's another one...

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by Cheesemill on 2009-11-18
> **mechro said:**
> Here's another one...

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

Thanks mechro, great link. That's going straight into my bookmarks :)

---

### Post by 3Miro on 2009-11-18
On an old version of Madrake I had manually mounted the same partition on two separate folders. I know it is possible, however, I am not sure if it is permissible on Debian (or any new system) and it is certainly not advisable. Besides I don't know how the initial installation would proceed, I did it with non-system folders.

You may be able to also do that with symlink, or maybe I did it with symlink at the time. It was long time ago.

/home is user space and it has access rwx for the users, /var is root space, and that can cause trouble with permissions and security.

---

### Post by sefs on 2009-11-18
```

Command (m for help): n
Command action
e extended
p primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (1033-9729, default 1033):
Using default value 1033
Last cylinder or +size or +sizeM or +sizeK (1033-9729, default 9729): +100M

```

He starts from partition number 2 and not 1 ... why?

What is going on with this tip...
```

As per wayupnorth comment, make sure all your future partition are mounted under /target, for example, you will need to issue:
# mount /dev/sdaX /target/boot
# mount /dev/lvmvolume/usr /target/usr
... 

```
Note the three dots which could mean that I should be typing something in addition to what is given?

---

### Post by Cheesemill on 2009-11-18
I can't help you there I'm afraid sefs, I've never set up LVM manually.

I always just use the alternate installation CD when I need LVM, as in the ISPmail link I posted.

---

### Post by sefs on 2009-11-18
Is that alternate method CD more straight forward?

I want to install 9.04 but it's a desktop CD. But I have the 9.10 alternate CD.

Would I be able to partition/prepare the drive with the 9.10 alternate CD.  Exit out of there and then boot with the 9.04 Desktop CD and install on the prepared LMV disk?

Thanks.

---

### Post by sefs on 2009-11-18
Current setup.

---

