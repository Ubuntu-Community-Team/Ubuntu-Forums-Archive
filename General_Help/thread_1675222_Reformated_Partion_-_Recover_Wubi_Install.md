---
title: "Reformated Partion - Recover Wubi Install"
date: 2011-01-25
forum: General Help
---

### Post by Winnard on 2011-01-25
While using *GParted,* I accidentally re-formatted, a NTFS partition which held both my Win7 and Ubuntu 10.04 LTS install using "Wubi", to Ext4. 

When I try to boot into Ubuntu I get - 

**"Windows Failed to start. " \ubuntu\winboot\wubildr.mbr**

"0xc0000001"

Trying to load into windows produces a similar error.

Please can someone suggest a way of **reversing** the format (I've been careful to try and not write anything to the disk since) or at least a way of recovering the majority of my files? 



Update: I have used TestDisk 6.11.3, however it us unable to find any history of the previous NTFS partition.

---

### Post by Mark Phelps on 2011-01-25
Testdisk is the premier app for Linux users for partition recovery; thus, don't know of any other Linux app.

If you're willing to experiment, Runtime Software makes several MS Windows file/partition recovery products, which are available as free trial versions: GetDataBack for NTFS, and Recovery My Files.

You will need the drive connected to a MS Windows box and the app installed on that box to try it out.  Also, the free versions don't do any recovery; only the paid versions do that.

---

### Post by Winnard on 2011-01-25
Thanks for the suggestions. I've changed the number of heads per cylinder in TestDisk, and am running the Deep Scan a second time. Fingers crossed!

The issue is complicated by the fact it's a laptop - so connecting it to a Win Box is slightly more difficult.

---

