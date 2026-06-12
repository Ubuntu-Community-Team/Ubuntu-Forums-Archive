---
title: "Config to support hard poweroff?"
date: 2012-02-18
forum: General Help
---

### Post by Mister Tibbs on 2012-02-18
Is there a known config for a system that is to be subjected to hard poweroffs?  I'm considering using Ubuntu for a single application that could be powered off at any time.  My application won't have open files, so it won't care, but I need the OS to reliably come back up without lengthy fscks, etc.  I imagine at a minimum write caching would need to be disabled - the loss in performance is not an issue.

I wanted to use MS-DOS or something like it that can suffer the most severe of shutdowns, however DOS does not have the device support I need.

Thanks.

---

### Post by dcstar on 2012-02-18
> **Mister Tibbs said:**
> Is there a known config for a system that is to be subjected to hard poweroffs?  I'm considering using Ubuntu for a single application that could be powered off at any time.  My application won't have open files, so it won't care, but I need the OS to reliably come back up without lengthy fscks, etc.  I imagine at a minimum write caching would need to be disabled - the loss in performance is not an issue.

I wanted to use MS-DOS or something like it that can suffer the most severe of shutdowns, however DOS does not have the device support I need.

Thanks.

Use a Live USB install with Persistence.

---

