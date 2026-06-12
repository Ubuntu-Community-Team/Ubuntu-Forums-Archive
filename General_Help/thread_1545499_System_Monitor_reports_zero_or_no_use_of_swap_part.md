---
title: "System Monitor reports zero or no use of swap partition"
date: 2010-08-04
forum: General Help
---

### Post by finny388 on 2010-08-04
Currently and for the last half an hour System Monitor reports
31% in use by programs
68% in use by cache

So my 1GB of ram is maxed out. Things are kind of slow but not crawling (though at times, simple things like scrolling are stalled)

But it reports Swap: 0% in use.

Seems confirmed by the following:```

$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        967         26          0         82        560
-/+ buffers/cache:        323        669
Swap:          964          0        964

$ sudo blkid
/dev/sda1: UUID="c96e9d20-74c0-4db6-b591-fdf0bfae4d24" TYPE="ext3" 
/dev/sdb1: LABEL="HOME" UUID="4c164d01-ad11-49de-9e79-ee649af88602" TYPE="ext3" 
/dev/sdb5: UUID="52a6bb51-0bb2-4c6a-b685-23d18584c352" TYPE="swap"
/dev/sdd1: LABEL="120GB" UUID="4206-705F" TYPE="vfat" 
/dev/sdc1: LABEL="SD_EEE_16GB" UUID="3834-3633" TYPE="vfat"
```

I did try to search around for a similar issue but couldn't find one.

Shouldn't swap be being used when ram is at 99%?

thanks

---

### Post by chopinhauer on 2010-08-04
> **finny388 said:**
> Currently and for the last half an hour System Monitor reports
31% in use by programs
68% in use by cache

Shouldn't swap be being used when ram is at 99%?


It is a common misunderstanding: you RAM is used at 31% and since RAM is thousands of times faster than the hard drive, Linux uses the unused RAM to cache some disk data. However it releases the cache whenever programs request more memory.

Unused RAM is wasted, so it is actually a good thing to have 100% used by programs + cache.

---

### Post by finny388 on 2010-08-04
Ah, that explains why it was so consistently at 99%. I guess I didn't realize what caching truly meant.

Inching my way towards better ubuntu understanding.

Thanks!

---

