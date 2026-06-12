---
title: "Does the Disk Utility Benchmark Utility display actual read speeds?"
date: 2012-04-02
forum: General Help
---

### Post by patw on 2012-04-02
I recently set up an HP pavillion and was almost certain that my
PLEXTOR PX-128M 6G/s would be bottlenecked at the HP MB 3G/s speed because they only support S2 (3G) even though they call it S3 (3G). But when I run benchmark utility, it shows acg read rate = 514M/s.  Is that the actual measured read rate?

I'm also seeing 490.65 and 196.81M/s on AS SSD benchmark.

---

### Post by dcstar on 2012-04-03
> **patw said:**
> I recently set up an HP pavillion and was almost certain that my PLEXTOR PX-128M 6G/s would be bottlenecked at the HP MB 3G/s speed because they only support S2 (3G) even though they call it S3 (3G). But when I run benchmark utility, it shows acg read rate = 514M/s.  Is that the actual measured read rate?

I'm also seeing 490.65 and 196.81M/s on AS SSD benchmark.

Just because something is connected to a 6gb/s pipe does not mean the things on each end are capable of using that bandwidth.

The only time a disk drive will get **close** to reaching that rate is for the tiny amount of data it may have in its cache - and that will only last a fraction of a second.

The limiting factors of HDD throughput are not the connecting cables.

---

### Post by HiImTye on 2012-04-03
remember also that rates are typically in bits not bytes 514MB/s is 4.015625Gb/s

---

