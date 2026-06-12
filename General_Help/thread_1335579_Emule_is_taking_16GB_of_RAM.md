---
title: "Emule is taking 16GB of RAM"
date: 2009-11-23
forum: General Help
---

### Post by Lockheed on 2009-11-23
Well, only 4gb, cause that&#8217;s all I have, but it would use everything no matter how much I had.

Every time it loses the connection, it starts expanding in RAM until computer is no longer usable. 
I am looking either for:
1. A way to make aMule stop doing that
2. A script that will kill programs occupying more than 80% of memory

---

### Post by manolo on 2010-12-16
Also happens to me :-(
To avoid a freeze of the system I invoke amule from a shell script with the directive:
{
#1GB limit of virtual memory use
ulimit -v 1048576
amule
}

I have checked at amule bugzilla ([http://bugs.amule.org](http://bugs.amule.org)) and there are many reports of memory leaks but no solutions :-(

---

### Post by Olhado256 on 2011-01-03
If you're using the 2.6.35-23 or 24 kernel, this is a known problem and the only solution right now is to revert to the 22 kernel. aMule developers are aware of the situation and are trying to fix it. If you want to help track down the cause, see this thread:

[http://forum.amule.org/index.php?topic=18144.15](http://forum.amule.org/index.php?topic=18144.15)

---

