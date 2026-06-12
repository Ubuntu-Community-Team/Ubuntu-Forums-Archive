---
title: "Encrypted RAID"
date: 2010-12-18
forum: General Help
---

### Post by Fancycakes on 2010-12-18
Hello all! I had been planning on creating a RAID 5 array over 4 2TB drives. I was going to use mdadm as the RAID controller, and then use cryptsetup to encrypt and format /dev/md0.

My question is in the event of a drive failure. In the event of a failure, I would normally dispense indiscriminate justice upon the offending drive and then have it summarily replaced to allow the array to restore itself, but what if the array was encrypted?

My first thought is that it wouldn't do anything with the new drive, it's unformatted, it hasn't been encrypted, etc, etc. I'd be in a pickle because I don't have enough external storage that would be able to hold the data of a 6TB array.

My second thought is that it would accept the new drive like one of its own and then take care of everything itself, copying LUKS headers from the other drives like it would the lost memory blocks.

I know from experience that not everything is like the magical land of happiness as depicted above, so I ask the Ubuntu Forums if the community has some knowledge about RAID - no matter how small - that could help.

---

### Post by SaturnusDJ on 2010-12-18
I don't know anything about encryption but if mdadm is the layer that's most down (as: HDD - mdadm - encryption - filesystem - what you see) it should just do a rebuild as any other RAID5 array.

---

### Post by Fancycakes on 2010-12-18
I suppose the only thing for it is to create an encrypted RAID off of three of the total four drives, remove one drive and replace it to see what happens. That way I'll know if it keeps the restoration well enough and if it'll encrypt as well.

---

