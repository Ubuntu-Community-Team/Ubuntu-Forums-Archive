---
title: "Resizing root"
date: 2010-11-23
forum: General Help
---

### Post by .09. on 2010-11-23
Hi


I have my partitions as follows:
- Windows 7
- Ubuntu
If I shrink the Windows partition will I be able to enlarge the Ubuntu root partition with gparted live cd?
I know I can add space after Ubuntu but can it be done before it?

---

### Post by eriktheblu on 2010-11-23
For clarity I'm assuming you have:
|----------|-----------|
and you want to have:
|------|---------------|

Yes, this can be done.

What Gparted will actually do is first move the data to the left, then expand the partition to the right. This takes more time, and I think has a higher potential for failure. I have done it successfully multiple times.

When shrinking your Windows partition, it's best to use the built in MS tools to avoid confusing Windows.

---

### Post by drs305 on 2010-11-23
Check out this post for tips on expanding / :
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Also at the bottom of that page is the link to a nice post by *srs5694*

---

### Post by .09. on 2010-11-24
Thanks, it worked! ;)

---

