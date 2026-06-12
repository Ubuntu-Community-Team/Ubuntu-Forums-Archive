---
title: "Slow file transfers on 10.10"
date: 2010-10-30
forum: General Help
---

### Post by nepenthe on 2010-10-30
Has anyone else noticed that file transfers on Maverick are significantly slower than on Lucid? A review of Maverick on [Tom&#8217;s Hardware](http://www.tomshardware.com/reviews/ubuntu-10-maverick-meerkat-linux,2774-11.html) finds that it is considerably slower. My own test says: On 10.10, file copy between two NTFS drives maxes at 30 MBytes/s; on 10.04.1, the same operations clock in at 40 MBytes/s. Both drives are capable of rw speeds of 70-90 MBytes/s, which I got on WinXP, and hdparm&#8217;s cached read results back that up.

Any ideas why file transfers are so slow, and especially why Maverick is even slower than Lucid?

**See next post.**

---

### Post by nepenthe on 2010-10-31
Okay, never mind that first post. That was the performance between NTFS partitions. Apparently, the NTFS driver in Ubuntu isn’t all that efficient.

What’s more irritating is that I get only about 30 mbytes/s from one machine running Maverick when I mount something via sshfs on a Lucid machine. And that definitely does not depend on the filesystem of the remote partition. When the first machine was still running WinXP, I got up to 40 mbytes/s over the network. Why the difference?

---

