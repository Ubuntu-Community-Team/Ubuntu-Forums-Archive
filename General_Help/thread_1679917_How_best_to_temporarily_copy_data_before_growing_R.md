---
title: "How best to temporarily copy data before growing RAID0 array"
date: 2011-02-01
forum: General Help
---

### Post by Jimbro727 on 2011-02-01
Hey,

I currently have two hard drives, with my root partition configured in RAID0.  I'd like to add two additional hard drives, and include them in my RAID0 array.  I need to recreate the array to do this, so I'd like to copy everything off of the existing array, add the drives, build the new array, and copy everything back.  I have an external hard drive with four times the capacity of my current array.  What would be the best way to copy this data so that nothing is missed, so I can just copy everything back and boot back up?

[LIST=1]
[*]dd, image the entire root partition, mount it after creating the new array, copy everything back (at the filesystem level)
[*]dd, image the entire root partition, write it back out to the new array, I'm not sure how this would work, because the partition will be the wrong size, I don't know much about dd.
[*]rsync, just rsync everything on root over to the external
[*]something else?
[/LIST]

I plan on booting to a live CD and mounting my current array there, so I won't be working on a live filesystem.

If I'm missing anything, please let me know.

Thanks,
Jim

---

### Post by ragtag on 2011-02-01
I've used dd in the past to copy an entire machines over to a file on an external disk, replace the drive in the machine, and then copy all the data back afterwards. It worked perfectly, even with both a Windows and Ubuntu partition on the disk. I just dd the whole device (/dev/sda). The USB drive needs to be ext3 or pretty much any file system other than fat32.

If you want to be on the safe side, you should probably take a backup of the files using rsync to a second USB drive, so at least you have your files if everything goes horribly wrong (from human error or a failed drive).

When using dd set the block size to something big like 16M (see 'man dd'), this will speed up the copyig by about a factor of 8. And use a live cd, like you said, as you don't want to dd the partition you're running your OS from.

If the new drive is bigger, you can just resize the partitions afterwards.

:)

---

