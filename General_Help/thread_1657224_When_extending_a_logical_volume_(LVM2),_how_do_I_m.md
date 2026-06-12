---
title: "When extending a logical volume (LVM2), how do I make it use all the remaining space?"
date: 2010-12-31
forum: General Help
---

### Post by s3a on 2010-12-31
I noticed resize2fs has an -M parameter which allows me to use the minimum amount of space possible and if I am correct, as an upper bound, I simply give no parameters and the filesystem should fill the logical volume's space entirely. However for lvextend, I cannot see anything in the man pages to do this. How do you guys ensure that the logical volumes use every bit of space of your hard drive? Is there a way to do it without having to use a calculator and calculating the amount of data?

Any input would be GREATLY appreciated!
Thanks in advance!

P.S.
Even if you cannot give me the answer I want, it would be nice to know what you guys think is the easiest way of doing so.

---

### Post by noah++ on 2011-01-01
```
lvextend --extents 100%FREE
```

---

