---
title: "Fastest way to make a raw image, dd?"
date: 2009-07-11
forum: General Help
---

### Post by jm8254og on 2009-07-11
I am going to have to take a raw image of many machines next week and am trying to get it as effecient as possible.  I am booting to a server live enviroment and have tested linen, dd, and sdd so far.  

dd with split and writing to a FAT32 target has been the fastest by far as of now.  For some reason writing to NTFS is about 30-40% slower.  

Any ideas?  I can't compress and need it to be a raw image.

---

