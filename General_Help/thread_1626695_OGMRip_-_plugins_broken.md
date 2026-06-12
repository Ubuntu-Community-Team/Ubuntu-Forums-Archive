---
title: "OGMRip - plugins broken"
date: 2010-11-20
forum: General Help
---

### Post by zenon222 on 2010-11-20
ubuntu performed some updates today, and now OGMRip has lost almost all of its plugins! Notably, x264 is completely gone.

I've tried reinstalling, to no avail.

Ideas?

Thanks.

---

### Post by zenon222 on 2010-11-20
I think this may be the problem, when executing OGMRip from the command line I see this:
```
Plugin libogmrip-xvid.so disabled: MEncoder is built without XviD support
Plugin libogmrip-x264.so disabled: MEncoder is build without X264 support

** (ogmrip:9414): WARNING **: Failed to initialize module libogmrip-x264-options.so

** (ogmrip:9414): WARNING **: Failed to initialize module libogmrip-xvid-options.so

```
I'll try building mencoder from scratch.

---

