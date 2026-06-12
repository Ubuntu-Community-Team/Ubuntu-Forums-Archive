---
title: "RAID0 array hard dive had become unpartitioned"
date: 2011-12-15
forum: General Help
---

### Post by Chris_huh on 2011-12-15
I've got a RAID0 array set up consisting of 2x3tb hdds. It was working fine until ubuntu crashed and i went to reinstall it. I've had to do this before and it has worked fine afterwards, but this time one of the HDDs claims to be 'Not Partitioned' in Disk Utility.

When i go to start up the array in Disk Utility it says that it is Not Running, Partially Assembled, with one of the HDDs partitioned to a GUID table and is recognised as part of the raid, while the other one just says Not Partitioned, but the SMART status lists it as healthy.

Is there any way to fix this without creating a new partition? I assume that would lose everything on the disk that way?

---

### Post by Chris_huh on 2011-12-16
anyone? i'm concerned that i've probably lost everything

---

### Post by zero2xiii on 2011-12-16
Hay,

If you run fsck on the drive? Maybe it can be repaired. But RAIDs are tricky stuff. 

Good luck

EDIT:

Wow, I just did some research on RAID arrays (first time I heard anyone using a 0 array, could not remember what it was) and it seems like that is not a good idea:

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

see under the part about raid0:
> RAID 0 (block-level striping without parity or mirroring) has no (or zero) redundancy. It provides improved performance and additional storage but no fault tolerance. Hence simple stripe sets are normally referred to as RAID 0. Any drive failure destroys the array, and the likelihood of failure increases with more drives in the array (at a minimum, catastrophic data loss is almost twice as likely compared to single drives without RAID). A single drive failure destroys the entire array because when data is written to a RAID 0 volume, the data is broken into fragments called blocks. The number of blocks is dictated by the stripe size, which is a configuration parameter of the array. The blocks are written to their respective drives simultaneously on the same sector. This allows smaller sections of the entire chunk of data to be read off the drive in parallel, increasing bandwidth. RAID 0 does not implement error checking, so any error is uncorrectable. More drives in the array means higher bandwidth, but greater risk of data loss

So if the one drive coroupted, you can not recover the system at all basicly.

---

### Post by dcstar on 2011-12-17
> **zero2xiii said:**
> Hay,
.........
see under the part about raid0:


So if the one drive corrupted, you can not recover the system at all basically.

[LIST=1]
[*]Do not "Quote" information in your posts - use "Code" tags.
[*]RAID 0 is anti-RAID, it is basically evil and anyone using it for important data without regular backups has rocks in their head.
[/LIST]

---

### Post by Chris_huh on 2011-12-20
I'm new to raid and only had two hard drives to set up a raid with. Now that prices of hdds seem to have skyrocketed i'm thinking its gonna be a long time before i can get any more.

So before i start this again (i do have a backup of most of the files) what would you recommend? 

This probably isn't the best of places to ask since i am moving away from ubuntu and moving to windows home server, but purely as a RAID setup? I have 2x3tb HDDs in a HP Proliant Microserver, which has space enough for another two HDDs and an optical. My plan was probably to use all four in some sort of raid array to get as much storage as i can and then install the OS onto a fifth that i would fit into the ODD. 

I will be using this mostly as a media server so am coming round to the idea that i might just spend a bit more and buy a completely new system and use the HP elsewhere, since it isn't always powerful enough to decode/transcode 1080p video.

A lot of that information probably isn't relevant so essentially:

I currently have 2x3TB HDDs that i want in RAID, with an ultimate aim to have 4 HDDs set up in RAID providing striping and mirroring (if they are the correct terms). Can i add HDDs to a raid setup after it is made? If not, can i set up a mirror of one HDD now and then later add another mirrored array that is seen as a striped array using software?

I will be so grateful for any help. I kinda had this sorted out but the system kept on crashing, requiring re-installations, and eventually it just killed everything.

---

