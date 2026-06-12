---
title: "EXT-4, Delayed write, msync  (), and fsync ()"
date: 2010-06-04
forum: General Help
---

### Post by BillRebey on 2010-06-04
I'm seeing very odd behavior with Ubuntu 9.10, which includes EXT-4.

I use memory-mapped files, and they're apparently being corrupted across power failures.  

Does anyone know definitively if "msync(...,MS_SYNC)" REALLY commits data to disk, or if it just commits it to the "file system", which might mean it gets caught up in the Delayed Write "feature" of EXT-4 and not actually persisted?

I can't find documentation on the matter - the man pages for msync don't mention the issue at all.

---

