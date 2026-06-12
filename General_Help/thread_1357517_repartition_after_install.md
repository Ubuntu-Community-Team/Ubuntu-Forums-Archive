---
title: "repartition after install"
date: 2009-12-17
forum: General Help
---

### Post by jwarburton3 on 2009-12-17
I would like to repartition after I finished the install         (9.10).  I tried gparted but could not get it to work.

During the install I selected ext4 type FS.  There is unallocated space on the drive, but I can't get gparted to move or resize any of the existing partitions.

I am using the liveCD version.

Can anyone help?

Thanks
Joe

---

### Post by prem1er on 2009-12-17
You can't partition a drive the is currently mounted. So, if you installed ubuntu to your hard drive, then you need to boot up from a flash drive or live cd. Make sure the hard drive isn't being mounted. And then you can use Gparted to format.

---

### Post by jwarburton3 on 2009-12-17
No the partitions aren't mounted.

I booted the system from the Gparted CD

joe

---

### Post by prem1er on 2009-12-17
Then what is the problem? Are having trouble figuring out how to work Gparted?

---

### Post by jwarburton3 on 2009-12-17
That may be my problem, but I have used gparted in the past.
I have unallocated space after the partition I am trying to resize, but the resize/move dialog box shows 0 space after the partition. So it won't allow me to 'grow'.

I thought it might have something to do with using ext4, as this is the first time I have used it.

I haven't done alot of configuring my system so I could go back and re-install with my new partition sizes, but I was trying to avoid having to do that.

---

### Post by oldfred on 2009-12-17
Once a swap partition is created most liveCDs use it including gparted. You also have to do a swapoff.

---

### Post by Darael on 2009-12-17
The other thing is that your ext4 partition may be within an extended partition, which you'd need to extend into the free space before you can expand the ext4 partition within it.

---

### Post by jwarburton3 on 2009-12-17
Thanks Darael,

That was it. My partitions were 'inside' an extended partition and I had to resize that first.

Thanks again,

---

