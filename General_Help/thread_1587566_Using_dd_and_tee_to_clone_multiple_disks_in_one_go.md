---
title: "Using dd and tee to clone multiple disks in one go..."
date: 2010-10-03
forum: General Help
---

### Post by ragtag on 2010-10-03
I'm looking into using dd with tee, to clone one drive to multiple other drives in one operation. In theory it shouldn't take much more time to do than cloning a single drive. I tried cloning a 32Gig USB stick to 5 copies on my local drive, and it took about 2x the time it took to make one copy. Of course, since I was making all copies on the same drive, it would be slowed down by the head on my drive skipping around.

My idea is to set up a machine with multiple SATA drives (up to 16), each somewhere between 200-1000GB. Make one copy on drive /dev/sdb or to an image file on a RAID, and then clone everything to the other drives. The code would look something like this.

```

dd if=/dev/sdb | tee >(dd of=/dev/sdc) >(dd of=/dev/sde) >(dd of=/dev/sdf) >(dd of=/dev/sdg) >(dd of=/dev/sdh) | dd of=/dev/sdi

```

Are there any hidden issues with this that I haven't thought of?

Or alternative ways to achieve the same result?

---

### Post by ragtag on 2010-11-09
I've been testing this a bit more, with multiple physical disks, and it seems to not work.

I have an image on an internal SATA disk, and have tried copying it to three drives at the same time, one FireWire, and two USB (connected at the front and back of the machine). I get about 24-26mb/sec, with copying to one drive, half that two two drives, and 1/3 of that if copying to three drives. 

It seems like it's reading three times, rather than just once. I thought tee, took the piped output and split it up, meaning it would only read the piped input once, but I may have misunderstood something. It still just runs four dd processes, one for reading and three for writing.

If anyone here is an expert on tee, or understands why this doesn't work, I would love a good explanation. :)

Alternative solutions are welcome too.

---

### Post by kanishkdudeja on 2010-11-09
u can do it with [clonezilla]("clonezilla.org")

---

### Post by psusi on 2010-11-09
Don't use dd to clone disks, it is dumb and copies all of the free space too, and can not deal with the destination disk being a different size.  Use clonezilla or ghost4linux.

Check out the parted magic cd.  You can network all of the computers to be cloned, boot them off the cd, fire up ghost4linux, and have them all clone in parallel from the server over the network.

---

### Post by alphaamanitin on 2010-11-09
> **psusi said:**
> and can not deal with the destination disk being a different size. 
It can deal with disks being a different size, unless you mean automatically expand partitions to fill the drive.  dd doesn't give a damn about the size of the drive being copied to, it will either fill the entire drive up that is receiving the data and quit because it is out of room, or if the receiving drive is larger, quit when it has copied all the files.  


AlphaA

---

