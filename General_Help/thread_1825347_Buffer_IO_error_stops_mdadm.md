---
title: "Buffer I/O error stops mdadm"
date: 2011-08-15
forum: General Help
---

### Post by MrMakealotofsmoke on 2011-08-15
Hello,
i have a RAID5 array using mdadm consisting of 5x1.5TB drives. Now i had one drive drop out due to a bad SAS cable so i re-added the drive and it began to reshape. The issue im having is it turns out one of the other drives might also be dying as it says it has 55 pending sectors to be remapped (thats not good :S). Currently the issue im having is this:

md/raid:md1: read error not correctable (sector 1718341704 on sde1) (a bunch of these)
then
Buffer I/O error on device md1, logical block 1 (a few of them as well)

Then the drive drops out of the array and stops the reshape causing the sync drive to be added as a spare. Now the array works fine all the other times hence why i didnt notice the other drive dying.

What can i do to stop the drive being dropped when these errors occurred so i can finish the reshape and add a new 1.5TB drive in to replace the dying one?

Cheers

---

### Post by dcstar on 2011-08-15
> **MrMakealotofsmoke said:**
> Hello,
i have a RAID5 array using mdadm consisting of 5x1.5TB drives. Now i had one drive drop out due to a bad SAS cable so i re-added the drive and it began to reshape. The issue im having is it turns out one of the other drives might also be dying as it says it has 55 pending sectors to be remapped (thats not good :S). Currently the issue im having is this:

md/raid:md1: read error not correctable (sector 1718341704 on sde1) (a bunch of these)
then
Buffer I/O error on device md1, logical block 1 (a few of them as well)

Then the drive drops out of the array and stops the reshape causing the sync drive to be added as a spare. Now the array works fine all the other times hence why i didnt notice the other drive dying.

What can i do to stop the drive being dropped when these errors occurred so i can finish the reshape and add a new 1.5TB drive in to replace the dying one?

Cheers

You may need to remove the bad drive and try to clone it onto a new drive and then put that back in the array. 2 bad drives at the same time in a RAID array is close to a disaster.

---

### Post by MrMakealotofsmoke on 2011-08-15
Your telling me :S lol. Ill see what i can do, i dont have 2 spare drives but ill try and sort that out. Anything else apart from cloning?

---

