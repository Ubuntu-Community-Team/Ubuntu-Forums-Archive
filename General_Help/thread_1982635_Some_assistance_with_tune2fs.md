---
title: "Some assistance with tune2fs"
date: 2012-05-18
forum: General Help
---

### Post by psych1610 on 2012-05-18
I'm looking for some assistance with tune2fs here. I created a single 2 TB partition on my 2 TB hard drive. When I mount it anywhere, say, /mnt/Media and issue df -h /dev/sdb1 I see this: 

/dev/sdb1       1.9T   28G  1.8T   2% /mnt/Media

I realize this is because ext4 reserves 5% of the blocks by default.

So I unmount /dev/sdb1 and issue: tune2fs -m 0 /dev/sdb1 where I see this:

tune2fs 1.42.2 (9-Apr-2012)
Setting reserved blocks percentage to 0% (0 blocks)

Of course, I think, success! So I reboot the machine for good measure, remount the drive, and issue a df -h /dev/sdb1 again where I see that 28 GB or 2% of my drive is still filled.

tune2fs -l /dev/sdb1 shows me this:

Block count:              488378368
Reserved block count:     0
Free blocks:              480664949

Which seems to suggest that I don't have any reserved blocks, but some are still being used. This is an empty hard drive as I have just partitioned it. 

If I issue df -h /dev/sdb1 while it is unmounted I see this:

udev            1.8G     0  1.8G   0% /dev

but I don't believe that matters much. 

Running du -sh /mnt/Media reveals there is nothing on the drive: 
8.0K    /mnt/Media/

Can someone help me figure out what's really going on here? Why do I still have 28 GB reserved/used when I told it not to reserve anything. This is a hard drive for storage space only. / and /home are on another drive entirely so I really don't feel like I need 28 GB reserved.:confused:

---

### Post by dcstar on 2012-05-20
> **psych1610 said:**
> 
.........
Can someone help me figure out what's really going on here? Why do I still have 28 GB reserved/used when I told it not to reserve anything. This is a hard drive for storage space only. / and /home are on another drive entirely so I really don't feel like I need 28 GB reserved.:confused:

Where do you think all the data about what is stored on the filesystem is kept, thin air?

---

### Post by psych1610 on 2012-05-22
dcstar, Of course I realize the data has to be kept somewhere, however, I feel by saying what you did you either did not read or did not understand the question in my post.

Let me re-state my question for you.

When ext4 reserves 5% of space on a drive (28 GB in this case) why are there still 28 GB used after I tell it to reserve 0%. At the very least I would expect that number to drop by 5% since, you know, there's no longer anything reserved. Instead it stayed the same.

I will readily admit to you I don't know a heck of a lot about file systems but it seems like common sense that I should have more space free and less used after the file system has stopped reserving space. Please feel free to elaborate more on what you said and explain why the amount of free space has not changed despite the file system not reserving it anymore.

---

### Post by dcstar on 2012-05-22
> **psych1610 said:**
> 
.........
When ext4 reserves 5% of space on a drive (28 GB in this case) why are there still 28 GB used after I tell it to reserve 0%. At the very least I would expect that number to drop by 5% since, you know, there's no longer anything reserved. Instead it stayed the same.
........

Possibly you have to use **resize2fs** to restructure the filesystem. When you change the structure of a filesystem you usually must do more than just change a value in the definitions.

---

