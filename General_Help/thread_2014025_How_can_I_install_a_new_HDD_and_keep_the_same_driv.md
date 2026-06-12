---
title: "How can I install a new HDD and keep the same drive designations?"
date: 2012-07-01
forum: General Help
---

### Post by motoroller on 2012-07-01
A few weeks ago, I installed a new SATA hard drive, which Ubuntu recognized right away and let me format (in ext4, of course). It was easy and straightforward except for one thing: My new drive became sdb and my old drive became sdc...

Originally, I was using a small SSD as my boot drive, which is known as sda. I had an older HDD which I plugged in and used for some storage, which ubuntu designated as sdb. Ok so far, so good. Then I install a third drive, but ubuntu decides to assign sdb to it, and sdc to the old one! 

This wasn't a disaster or anything; it was just kind of annoying. I even made sure to keep the old drive plugged into the same port on the motherboard. While installing the new HDD, I had to unplug the old one briefly to run the cables, but the system was completely powered down so... yeah...

I might add another drive in the future, and here's my concern: if I add another HDD, how can I be sure that my drive designations will stay the same, and give the new HDD a new designation?

thanks for any suggestions you may have

---

### Post by rai4shu2 on 2012-07-01
Those "sdx" designations are given by the kernel. For tracking, you really should use labels or UUIDs.

man tune2fs
ls -o /dev/disk/by-uuid/

---

### Post by oldfred on 2012-07-01
I find my drives follow the port order on the motherboard, except when I boot with a flash drive plugged in then it can change all over the place.

What port on motherboard did you use?

---

### Post by motoroller on 2012-07-01
hey oldfred... now that I had a look at my MB, I realized what I had done... my boot drive was on port 1, my old HDD was port 6, and my new HDD was port 4. It makes sense now why the kernel would want to rename my old HDD to sdc.

As for the tune2fs thing, I'll read through that manual again and try figuring it out. I already got the UUID for each drive, but I'm just afraid that if I give the drives unique labels it will screw up the boot order or mounting or something. I just need to be reassured :P

I used disk utility to assign a unique label to each drive and it shows up when run ls -o /dev/disk/by-label... So now that they have unique labels, is there anything else I should to do ensure they behave even if I rearrange the MB connections?

---

### Post by rai4shu2 on 2012-07-01
As long as they have unique labels, you're good.

---

### Post by oldfred on 2012-07-01
I like labels and try to label every partition, but they only appear on unmounted partitions in the left panel of Nautilus or if you use them to permanently mount a partition instead of using UUIDs. 

But then they still can be mounted differently than the label as the label is used as the UUID or device entry not the mount. Some think we really should use labels more in fstab, but I have not converted from UUIDs.

I also can get confused. I create a label of Backup, but mount the backup partition as /backup and then I have two entries as they then are different as case matters.

---

### Post by motoroller on 2012-07-01
Ok thanks guys I think I'm starting to understand now... Looks like I'll be good for the time being, although I really need to read more about mount points and how to set them properly.

Once again, these forums have been educational! :guitar:

---

