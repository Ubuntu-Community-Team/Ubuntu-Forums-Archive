---
title: "WIPE vs 0.21"
date: 2011-04-26
forum: General Help
---

### Post by DAB4970 on 2011-04-26
Hello everyone.  I have been trying to find out what the default number of passes are when wiping one partition that spans the entire drive.  Or is there a default number?  Maybe it's suppose to run until it doesn't see anything left to overwrite.

# wipe /dev/sdb1
<ubuntu 10.10, kernel 2.6.35-28>

I have 2 old pata desktop drives, 20 GB and 40 GB, that I am "cleansing".  I let it pass 7 times on the 40 GB drive before ending the process with sysmon.

Is there any other utility that I could try?

---

### Post by lithopsian on 2011-04-26
By default, wipe uses 34 passes with different patterns.  The number of passes and the patterns used are configurable for the truly paranoid.

---

