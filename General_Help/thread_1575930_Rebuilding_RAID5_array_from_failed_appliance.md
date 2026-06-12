---
title: "Rebuilding RAID5 array from failed appliance"
date: 2010-09-16
forum: General Help
---

### Post by gnarmy on 2010-09-16
Hello,
 
This isn't exactly Ubuntu specific, but I do plan on using Ubuntu to try to recover this array. I've been using a Freedom9 freestor 4020 for the past few years, and other than it totally blowing up last week it's been pretty good.
 
I was on vacation for almost a month, and a few days after I returned my NAS (freestor 4020) started acting up. I tried a few power cycles, but was dismayed to see that I could not log in via browser or SSH (SMB shares were no accessible either). A drive failure light is supposed to illuminate if a disk fails, but no dice. I plugged all 4 drives from the NAS into an Ubutnu 9.04 Desktop system and one started throwing out all kinds of errors. Thinking that it would be a simple rebuild, I went to my local computer shop and picked up another 500GB drive (same manufacturer/part #), replaced the failed drive, and powered up the NAS again... Nothing. I left it for 12 hours then powered it down, plugged the new drive into my linux box again to see if it rebuilt... the drive was a virgin.
 
What gives me hope that I can still recover the data is Ubuntu sees "RAID components" on the drives (through disk manager and parted), and gives me the option of initializing the array.
 
My plan of attack is to plug all of the drives back into my Ubuntu box, initialize the RAID array via LVM, and pretty much hope for the best. The data is not uber critical, but it would be a pretty big pain in the behind to rip/upload all the software that was on it (ripping hundreds of DVD/CD images is not fun). If my Ubuntu box can make sense of this newly initialized/mounted RAID set... I'll plug in a 2TB external drive, copy the data over, and rebuild the NAS from scratch, then put my data back on (perhaps a different unit, or something running openfiler).
 
My question to you is:
 
Is this a waste of time? Do you have any other ideas/suggestions on how this may be done better?

---

### Post by Baked- on 2010-09-16
I think if you initialize the array you will lose your data.

---

### Post by CharlesA on 2010-09-16
> **Baked- said:**
> I think if you initialize the array you will lose your data.

Normally, yeah.

I hope you have a recent backup. If the array has totally failed, you are SOL about getting it back up and running.

Normally what would happen if a disk went out, you'd just swap it out and rebuild the array. It doesn't sound like that's what happened here, unfortunately, since it wasn't rebuilding the drive. :(

---

