---
title: "Problem with Gparted"
date: 2010-12-11
forum: General Help
---

### Post by Maggar on 2010-12-11
I need to add more space to a Ubuntu install, however it's on the right and has no space to add. My plan is to copy it to the empty space on the left and remove the original in order to use the rest of the space that used to be windows. I'm not to smart about partitions however I believe this is the way to do it?

The problem is when I attempt to copy the roughly 10gig partition into the 68ish gig space I get an error telling me that there isn't enough room. Not really sure what the issue here is, I took some screen shots of it to possibly help. I couldn't save the error message because I was on the live cd so I took a pic of that as well.

Having troubles attaching images to this post so I'll just upload and add the urls for now....

```

http://img547.imageshack.us/img547/3343/gparted1.png
http://img46.imageshack.us/img46/9638/gparted2.png
http://img602.imageshack.us/img602/1025/gparted3.png

```

---

### Post by Quackers on 2010-12-11
It would appear from your second screenshot that /dev/sda5 has been copied to the beginning of the disc.
If you want to extend /dev/sda5 you will first need to extend /dev/sda2 to the left. /dev/sda2 is an extended partition that "holds" /dev/sda5 and /dev/sda6 which is your swap partition. 
If /dev/sda2 is extended to the left you will then be able to extend /dev/sda5 to the left.
Is that what you want?

---

### Post by efflandt on 2010-12-11
It might be that you are trying to move a logical partition to a point on the disk that is NOT withing an extended partition, so an exact copy of the partition would not even work there.  So the true error may be that there is insufficient extended partition space to put it there (in not so many words).  Also it may help to do **sudo swapoff /dev/sda6** so nothing is in use on that drive at the time, especially to try the following.

Try moving the beginning of the extended partition down to the beginning of the drive, then copy (or move the beginning of) sda5 down to the beginning of the drive.  Note that copying a primary or logical partition or moving the beginning of it can take awhile, so don't start that when you need to go somewhere soon or when a storm looks likely (power failure).

That quantity of swap does not make much sense unless you have a very old system with less RAM than that.  Normally you would have **swap >= RAM** if you want to be able to hibernate.  So you might then want to shrink the end of sda5 and make sda6 (swap) larger if necessary.

---

