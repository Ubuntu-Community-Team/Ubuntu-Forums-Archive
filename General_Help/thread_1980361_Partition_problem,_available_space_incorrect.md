---
title: "Partition problem, available space incorrect"
date: 2012-05-15
forum: General Help
---

### Post by wmcmick on 2012-05-15
Hi!

I have a problem with a RAID unit (Adaptec) on a Ubuntu machine. It's a raid5 unit with six 2TB hardrives totalling at about 9-10TB. 

The problem is that the reported available space seem to be about 7400GB when checking the properties of the mount. 

Adaptec Storage Manager and Disk Utility shows correct sizes. I'm attaching a couple of screenshots. Any idea why this could be? 

Greatful for any help, thanks in advance!

---

### Post by dcstar on 2012-05-15
> **wmcmick said:**
> Hi!

I have a problem with a RAID unit (Adaptec) on a Ubuntu machine. It's a raid5 unit with six 2TB hardrives totalling at about 9-10TB. 

The problem is that the reported available space seem to be about 7400GB when checking the properties of the mount. 

Adaptec Storage Manager and Disk Utility shows correct sizes. I'm attaching a couple of screenshots. Any idea why this could be? 

Greatful for any help, thanks in advance!

Usable filesystem space is not the same as partition space. Filesystems have overheads.

---

### Post by wmcmick on 2012-05-15
Here 1.5TB is missing, that's seems a lot.

---

