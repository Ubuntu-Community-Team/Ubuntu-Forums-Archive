---
title: "What is MiB/S in System Monitor"
date: 2011-01-09
forum: General Help
---

### Post by UncleBoarder on 2011-01-09
I'm getting approximately 10MiB/s file transfer between machines sharing via NFS.  If it's reporting Bytes, that's reasonable.  If bits, then that's a problem.

As a network Admin, I think of MB/s as megabytes per second... and Mb/s as megabits per second.

But I also often see this printed or reported incorrectly.

So, which does System Monitor display for network traffic, bytes or bits?

---

### Post by Vaphell on 2011-01-09
you could check it yourself - if the transfer takes 8x more time to complete than it should then it's bits. Either way MiB = mebibytes.

---

### Post by UncleBoarder on 2011-01-09
True I could, but since I'm in the midst of copying a hard drive, I figured this would be faster.  Thanks!

I am curious as to why it displays in megabytes since almost all network speeds are measured it bits per second?

And secondly... can I change it to display bits per second?

---

### Post by maphilli14 on 2011-02-06
> **UncleBoarder said:**
> 

And secondly... can I change it to display bits per second?

Yes, look in Edit / Preferences / "Show Network Speed in Bits"

It's a check box!

HTH, and thanks!

Mike

---

