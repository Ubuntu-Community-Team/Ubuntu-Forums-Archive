---
title: "Recover Pointsec encrypted partition after gparted format"
date: 2010-01-28
forum: General Help
---

### Post by diablillo77 on 2010-01-28
Hey all!

Well the title says it all. Royal screw-up! I accidentally formatted two Windows partitions inside a Pointsec encrypted hard drive using gparted from a liveCD (in USB). Is there a way to recreate these partitions? If not the whole partition, at least be able to recover everything inside My Documents. I ran TestDisk and it will not see any of the two partitions that existed in the drive. What ever options do I have and what other software can I use? Thanks in advanced for any suggestions.

---

### Post by kidders on 2010-01-30
Hi there,

I doubt you'll be able to recover anything, I'm afraid. One of the drawbacks (or features, depending on how you look at it) of disk encryption is that even seemingly minor damage is invariably catastrophic. In other words, the loss of a single byte of raw data can render the entire device unusable.

Since you've formatted your partitions, you've overwritten small pieces of the data they used to contain, so I wouldn't expect you to be able to recover *any* of it.

> **diablillo77 said:**
> If not the whole partition, at least be able to recover everything inside My Documents.It's a case of all or nothing, really. If it were possible to restore individual files from a damaged filesystem, encrypting it would be pointless.

---

