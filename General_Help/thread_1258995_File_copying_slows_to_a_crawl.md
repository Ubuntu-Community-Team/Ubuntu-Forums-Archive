---
title: "File copying slows to a crawl"
date: 2009-09-05
forum: General Help
---

### Post by valros on 2009-09-05
Copying a 3.3Gb file to a 4Gb flash drive formatted with fat32 starts out at a standard 20mbs then slows down until its unresponsive within a minute.

---

### Post by JC Cheloven on 2009-09-05
Perhaps you're too close to limits. On on e hand there is the 4Gb limit for a single file in fat32. On the other hand, the device you're copying on is just 4Gb. Perhaps there isn't room for some temporary management or whatever. 
I'd try formatting the media in ntfs (or in ext2/ext3 if you're not concerned with windoze compatibility).

---

### Post by c0mput3r_n3rD on 2009-09-05
I agree with JC Chevelon, a flash drive, just like a HDD, needs a certain amount of memory blocks to itself, either for swap or what have you (not entirely sure).  Your flash drive might say 4Gb on it, but  look at the actual total capacity, it will be less. check that out.
```

df /media/name_of_your_device

```

---

