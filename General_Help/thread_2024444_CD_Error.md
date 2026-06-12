---
title: "CD Error"
date: 2012-07-13
forum: General Help
---

### Post by noelc on 2012-07-13
Hi Guys,

I,m wondering if anyone can tell how to fix the error message below. The CD I,m trying to load is Ubuntu 12.04lts?



Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0: can't read superblock


Thanks

---

### Post by Rexilion on 2012-07-14
First line is non-critical. You tried mounting without the '-o ro' option, so it tries to mount '-o rw' which is not supported on these filesystems. This is normal, as these filesystems are not designed to be 'written to'.

Second error is kinda fatal. First block with all the critical information is either broken/corrupted/missing.

Maybe try burning again?

---

### Post by noelc on 2012-07-14
> **Rexilion said:**
> First line is non-critical. You tried mounting without the '-o ro' option, so it tries to mount '-o rw' which is not supported on these filesystems. This is normal, as these filesystems are not designed to be 'written to'.

Second error is kinda fatal. First block with all the critical information is either broken/corrupted/missing.

Maybe try burning again?

Wow thanks Thats annoying as I didnt burn the CD but bought it on line so I could upgrade to 12.04. So your suggestion is to source (Or burn) another CD?

---

### Post by Rexilion on 2012-08-25
I guess, but if you bought you should return it. Or maybe check:

```
dmesg | tail -n5
```

Maybe your CD-drive is dying/too old?

---

