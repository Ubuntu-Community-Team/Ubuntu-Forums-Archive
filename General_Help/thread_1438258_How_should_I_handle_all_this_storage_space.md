---
title: "How should I handle all this storage space?"
date: 2010-03-24
forum: General Help
---

### Post by busydoingnothing on 2010-03-24
I'm building an Ubuntu 9.10 home server to essentially backup all my PCs to, serve media, and store other large data (I record music and film). Here's what I have as far as storage goes:

[LIST]
[*]4GB CompactFlash: for OS
[*]2x 500GB WD drives: intended for RAID-1 for backup (which I will in turn back to external drive on a weekly basis)
[*]3x TB Hitachi drives: intended for RAID-5 for media and storage
[/LIST]
Both RAIDs will be software-driven. Now, a few questions:

[LIST=1]
[*]From what I've read, I can benefit from using LVM on top of the RAID. Is this true, and besides the complexity and potential difficulties in recovery in case of disaster, is there a downside to LVM?
[*]Would I benefit at all from using smaller logical volumes on the RAID-5, or should I just make one at the full size of the drive?
[*]Also from what I've read, it seems that XFS may be the best filesystem to use, from a stability and performance standpoint. Should I go that route, then? I suppose that if it IS beneficial to have multiple smaller logical volumes, then there may come a point that I need to shrink and grow these logical volumes, and if that's the case, it appears XFS is out of the question. What's the runner-up; Reiser?
[*]I currently have /swap and /home partitions on the CF card. I'd at the very least like to remove the /swap partition and just create a swap file on the RAID-5. Should I move my /home partition to the RAID-5 as well?
[/LIST]
Hope I'm not askin too much here! Thanks guys.

---

### Post by busydoingnothing on 2010-03-25
Nothing?

---

