---
title: "RAID5 Re-Creating MD0"
date: 2011-07-28
forum: General Help
---

### Post by tylersontag on 2011-07-28
Hey all,  i think i've got myself in a pickle and i was wondering if anyone has any recommendations for me...

Alright, yesterday i had my 3 drive 6TB raid array get in a bad state.  It does this from time to time, i blame it on the controller card getting too swamped or something.  But anyways, the RAID will appear to crash, if you look at the drive in Disk Utility it will say the drive is DEGRADED.  Now my normal fix is to reboot the computer and re-assemble the array.  But not today...

Today, feeling bold and distracted i thought "Theres no reason i need to reboot here... what if i just remove those 2 faulty drives and re-add them?  That should work right?....  wrong.

Drive still won't come up, i try to reboot as usual but now the drive won't assemble, saying it can't find any superblock on the 2 drives i had previously removed.   No mater what i do i can't get this thing to build.  I panic and search the internet for a fix "Surely this is a fixable problem?" I thought.

I came across this site: [http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)

It recommended that i zero out the superblock on the last remaining drive and just recreate the array... sounds easy and straight forward.

I do so, it spends the next 13 hours re-syncing the array... at its conclusion: I have a functioning raid array holding a 4TB unrecognized partition.

I feel i may have passed the point of no return long ago... but can anyone suggest anything at this point that can get me back to my old setup?

---

### Post by tylersontag on 2011-07-29
bump... as i slowly come around to accepting the inevitable :-/

---

### Post by Habitual on 2011-07-29
Well, since you think you are past the point to no return, I'd zero out the superblock.

What does
```
mdadm --detail /dev/md0 | grep Persistence
```
indicate?

I am by NO means a raid guru, but what can it hurt at this point.
I have recently only got my feet wet using software raid on an AWS Instance myself.

I am subscribed to and watching this thread with interest.

Good Luck.

---

### Post by tylersontag on 2011-07-31
```
  Persistence : Superblock is persistent

```

i think what we're dealing with here is 
A) a brash moment of hubris:  "I shouldn't have to restart to reassmeble the RAID, i  can just remove the drives it thinks are degraded and re-add them"
and B) a short coming of the software array system, having the drives themselves hold the meta data of how to construct the array rather than the RAID card itself, plus perhaps  (it could be argued that it was designed that a knowledgable admin should be administrating the actions) that the action of dis-associating the individual drive from an array zeros out its superblock.

assuming after i re-built the array, if it happened to have the exact same striping pattern and block size, and happend to have defaulted the same sectors as the parity blocks as before you MAY be able to force a grab of the partition block that would assemble properly and allow one to rebuild the drive.

Or, more likely than all these ifs, you just ruined 2.5 TBs of data :-/

---

