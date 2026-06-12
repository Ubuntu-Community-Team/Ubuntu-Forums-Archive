---
title: "USB drive reads as a CD"
date: 2012-08-07
forum: General Help
---

### Post by fritz269 on 2012-08-07
So I have a USB drive that has some files on it that is being mounts as a CD. How can I change it to read as a USB?

---

### Post by dcstar on 2012-08-08
> **fritz269 said:**
> So I have a USB drive that has some files on it that is being mounts as a CD. How can I change it to read as a USB?

You have to wipe the Partition Table (which wipes the whole device, usually) and then create fresh partitions on the device. Gparted will do usually this.

Some devices have these actually built into their firmware and you need a firmware update to wipe these pesky partitions.

---

