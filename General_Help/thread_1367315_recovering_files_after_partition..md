---
title: "recovering files after partition."
date: 2009-12-29
forum: General Help
---

### Post by Groundswell on 2009-12-29
there's so much on the web about data recovery that i can't even find what i need. I'de like be sure i get it right the first time and use the appropriate program for my situation.

my situation is... an unorganized file pile of a hard-drive i use just for music/pics/junk, became repartitioned during a rushed install a few months ago. I've let it sit since because i don't really use it often. a few new files were written to it, but not much.

anyone have any experience with this stuff and could point me in a direction??

---

### Post by rahilm on 2009-12-29
I have used testdisk extensively:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

also , the photorec software included within the package is a good data recovery agent.

---

### Post by doas777 on 2009-12-29
the overwritting may be problematic (as may be the time since the partit was overwritten), but you may be able to recover the partition itself with testdisk, or many of the files with photorec. both tools are on the ubuntu-rescue-remix livecd. 

you will need a free  volume with the same or greater capacity than the partition you are trying to recover to write the recovered data to (it CANNOT be the original partition).

try testdisk first, and if that fails, fall back to photorec. the benifet to testdisk, is that it will recover all files, but photorec can only recover files from specific types (images, mp3;s, word docs etc) because it needs to be able to tell the begining and end of files, just by their raw data, so it needs to understand the filetypes data format.

---

### Post by Groundswell on 2009-12-29
it sounds like photorec is all i really need. i did have a few large downloaded files but i'm really not concerned about them. The drive has been mounted probably 3 times since it happened so it should be relatively untouched

the only setback,.... i don't have someplace to recover files to thats as large as the drive. but i do have a space that could hold all the data that was on the drive. so can you clarify? 

"you will need a free volume with the same or greater capacity than the partition you are trying to recover to write the recovered data to"

is that strict? or is that assuming the mentioned recovery drive is full?

---

### Post by doas777 on 2009-12-29
> **Groundswell said:**
> it sounds like photorec is all i really need. i did have a few large downloaded files but i'm really not concerned about them. The drive has been mounted probably 3 times since it happened so it should be relatively untouched

the only setback,.... i don't have someplace to recover files to thats as large as the drive. but i do have a space that could hold all the data that was on the drive. so can you clarify? 

"you will need a free volume with the same or greater capacity than the partition you are trying to recover to write the recovered data to"

is that strict? or is that assuming the mentioned recovery drive is full?

if you tried to recover files A -Z on the hdd, you would recover A, and rewrite it to the disk, in the process overwritting sectors of files F, K, and V. recover file B, and it will overwrite chuncks of M, Z, and E. as this keeps going, you will find that there are no recoverable files left. 

that make sense? I'm not sure I expressed it clearly.

---

### Post by Groundswell on 2009-12-29
yeah i got you, and i understand that, but what about recovering to a different volume that is smaller then the target drive thats being recovered. 

the drive that needs recovering is 130 gigs, but only had 70 gigs of data, i have a 109 gig volume thats empty, could i recover to that?   as i'm writing this i'm realizing that it would pick up older data that when combined with what i want could be a full 130 gigs... looks like i defenitely need another drive the same size or larger... thanks for your help

---

### Post by doas777 on 2009-12-29
> **Groundswell said:**
> yeah i got you, and i understand that, but what about recovering to a different volume that is smaller then the target drive thats being recovered. 

the drive that needs recovering is 130 gigs, but only had 70 gigs of data, i have a 109 gig volume thats empty, could i recover to that?   as i'm writing this i'm realizing that it would pick up older data that when combined with what i want could be a full 130 gigs... looks like i defenitely need another drive the same size or larger... thanks for your help

that will work for photorec, but not for testdisk. sounds like you like photorec, so it should work out for ya.

Good Luck!

---

