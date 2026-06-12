---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)"
date: 2010-03-27
forum: General Help
---

### Post by Colo2 on 2010-03-27
Hey

So, we had a power cut, and when I turned it back on, I got:

> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)

hence, the computer won't boot. 

Ubuntu is installed within windows.

I had so much data on there, please could someone help me fix this without a re-install?

Thanks

- Tom :popcorn:

---

### Post by Colo2 on 2010-03-27
Please help :(

---

### Post by matt! on 2010-03-27
I've also got this. My laptop froze and I had to switch off. 

Luckily, in the wabi menu there's an older Linux kernel that still boots. But I'd appreciate a fix for the most recent kernel. There's lots of references to this problem all over the forum but there doesn't seem to be one solution but rather a mish mash of suggestions. 

Perhaps it would help I we could figure out exactly what the error means and what might have caused it?

---

### Post by Colo2 on 2010-03-27
Hey Matt

For me, it was caused by the virtual drive that WUBI created being corrupt when my system shut down unexpectedly. 

I'm just doing a re-format, this time, I'm not using wubi.

- tom

---

### Post by matt! on 2010-03-28
But I can still run ubuntu using the older kernel?

---

### Post by matt! on 2010-03-28
Did some more reading and found it is due to a bug in wubildr that has been patched but not released mainstream.

You can grab a patched binary from a link toward the end of this thread, replace it and all is well without the need for any reinstallation/recovery etc:
[http://ubuntuforums.org/showthread.php?t=1317397](http://ubuntuforums.org/showthread.php?t=1317397)

Hope that helps somebody else in this ridiculous situation.

matt

---

### Post by James78 on 2010-05-03
N/a

---

