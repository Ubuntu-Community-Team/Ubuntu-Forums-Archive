---
title: "Does a 32-bit OS support ext2/3 drives 2TB and more?"
date: 2010-01-18
forum: General Help
---

### Post by probedb on 2010-01-18
I'm only asking as I want to use an eSata enclosure which will combine 2 drives into one so I'd be presented with 4TB.

Can 32-bit 9.04 cope with this as one partition or would I have to create multiple partitions on it?

Cheers :)
Paul.

---

### Post by kidders on 2010-01-19
Hi there,

Ext2/3 only have a 32-bit address space, so the maximum filesystem size is 16TB regardless of the bitness of your OS.

(Strictly, the upper limit is 2^32 blocks. The 16TB figure applies to the default 4k block size.)

I hope that helps.

---

### Post by wkulecz on 2010-01-19
IMHO 4TB in a Raid0 is asking for trouble.  How are you going to keep all that data backed up?  One drive dies both drive's data are gone.  I'd use raid 1 for 2TB or mount them as two seperate 2TB drives and let one backup the other.

Raid of any level is not a backup -- accidental deletes or overwrites are instantly gone.

--wally.

---

### Post by probedb on 2010-01-19
Cheers kidders!

> **wkulecz said:**
> IMHO 4TB in a Raid0 is asking for trouble.  How are you going to keep all that data backed up?  One drive dies both drive's data are gone.  I'd use raid 1 for 2TB or mount them as two seperate 2TB drives and let one backup the other.

Raid of any level is not a backup -- accidental deletes or overwrites are instantly gone.

--wally.

That's the problem I have. My Revo doesn't have a port multiplier on eSata so I can't mount as two separate drives. Still a while before I can get new drives but thanks for the input!

---

### Post by PrvSAT on 2010-07-18
> **probedb said:**
> Cheers kidders!



That's the problem I have. My Revo doesn't have a port multiplier on eSata so I can't mount as two separate drives. Still a while before I can get new drives but thanks for the input!

Isn't this a matter of a operating system's driver? I have the 4x enclosure and on the same hardware, I have a OsX and Windows installed and when connecting, all drives are recognized but not in ubuntu.
Is this a matter of driver or a bug?

---

