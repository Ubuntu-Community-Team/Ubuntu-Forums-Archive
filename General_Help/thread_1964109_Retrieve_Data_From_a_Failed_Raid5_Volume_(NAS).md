---
title: "Retrieve Data From a Failed Raid5 Volume (NAS)"
date: 2012-04-23
forum: General Help
---

### Post by asheenlevrai on 2012-04-23
Hi,

I have a Seagate BlackArmor NAS setup with a 4-disks RAID5 array containing a single volume, where all my data are stored (4x1TB= ~2.5TB available).

For no reason, upon a reboot of the NAS, the volume will now not work anymore (volume is "Failed", not found) while **all 4 disks are reported as "Good"**. Of course I can't access the data anymore. I only have an old outdated backup (~600GB missing on the backup compared to the NAS), this is because the NAS failed just after I moved ~600GB of data on the NAS. Before I had a chance to back them up somewhere else... (I mean, WTfreakingF?)

Seagate guys are not being helpful at all and directed me to their paying data recovery service. This one must be very lucrative these days since there are several post on the Seagate forum with people having apparently the same problem with their BlackArmor NAS. Seagate has no explanation for the cause of the failure and since all disks appear OK, I do not know what I could try to recover (or at least access) the data.

I can't find any instruction online on how to repair a failed RAID5 volume when **all disks appear as fully functional**... :(

I thought maybe I could use Ubuntu to mount the volume (instead of the BA NAS). If I could fit those 4 disks in one of my Ubuntu desktop machine, I may mount the volume using mdamd or something and then copy the data on another NAS server. What do you guys think? Does this sound like making any sense?

I am not familiar with mdamd at all but I eager to learn (I guess I have no choice ;)  ). I don't want to make any definitive mistake though, so I would appreciate any help/advice from you guys.

Once again, I have no clue where the problem comes from, this is why I don't where to start looking for a solution or know how to solve it...

Thanks a lot in advance for any help :)
-a-

---

### Post by J-D-Cronin on 2012-07-05
I know this thread is a few months old, but incase someone else sees it I thought I'd post.

Some people have had success by just updating their firmware. It seems like a bug that the NAS quits recognizing the volume.

---

### Post by asheenlevrai on 2012-07-06
Thanks,

Indeed, I read that from the Seagate Forum.
However, In our case (as for many other people too) upgrading (or downgrading) the firmware had no effect whatsoever...

A colleague of mine used UFS Explorer RAID Recovery (100€) to mount the array in a PC and retrieve the data. We then created a new volume from scratch (in the Black Armor) and copied the data on it.

We should ask Seagate to give us the 100€ back ;)
Thanks for your reply anyway

Best,
-a-

---

