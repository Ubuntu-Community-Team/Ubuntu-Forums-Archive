---
title: "parity checking without raid"
date: 2010-01-30
forum: General Help
---

### Post by bonfire89 on 2010-01-30
Is it possible to have a drive dedicated to parity check for several other drives and not use a raid?

I want to keep all the drives separate, raids seem too dangerous.


Thanks

---

### Post by dcstar on 2010-01-30
> **bonfire89 said:**
> Is it possible to have a drive dedicated to parity check for several other drives and not use a raid?

I want to keep all the drives separate, raids seem too dangerous.


And exactly what are you going to do if a drive fails some sort of parity check?

---

### Post by pietjanjaap on 2010-04-11
Look at unraid.(and maybe zfs file system).
Then you can repair 1 failing drive.
3 drives = 2 drives files + 1 drive parity(you can repair 1 drive)

This goes up to 18 drives, 1 can fail and be rapaired.

Unraid you can swap a small drive for a big one.
You can grow your server with bigger drives, with swapping drives.
You can use different sizes of drives(parity drive must be the biggest).

If 2 drives fail then you only lose the 2 drives, the other drives you can read with every other computer.

---

