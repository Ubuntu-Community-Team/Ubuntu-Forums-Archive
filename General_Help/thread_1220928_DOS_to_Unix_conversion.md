---
title: "DOS to Unix conversion"
date: 2009-07-23
forum: General Help
---

### Post by tonysonney on 2009-07-23
I was trying to build a system.But I had to copy it through a windows machine. But I can build it on Linux. But some people claim that code can be built on Linux. I was wondering whether the files in DOS text would make any difference as I am building in Linux?

---

### Post by keplerspeed on 2009-07-23
What exactly are you building, and how are you trying to do it?

---

### Post by wojox on 2009-07-23
dos2unix - cleans up end of line handling. Converts DOS text files to UNIX/Linux format.

There is also WinSCP.

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

### Post by tonysonney on 2009-07-23
dos2unix command converted the dos files to unix format. So I think this thread is irrelevant any more. But does it really make any difference? I thought Linux would not bother whether the files are in DOS or UNIX format.

---

### Post by nikhilk on 2009-07-23
> **tonysonney said:**
> dos2unix command converted the dos files to unix format. So I think this thread is irrelevant any more. But does it really make any difference? I thought Linux would not bother whether the files are in DOS or UNIX format.

Technically, it is not Linux (the kernel) that bothers about the line endings but bulk of the Linux applications.

---

