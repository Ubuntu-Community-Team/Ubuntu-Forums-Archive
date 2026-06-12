---
title: "PCH poison interrupt (Natty)"
date: 2011-05-23
forum: General Help
---

### Post by manybodycpa on 2011-05-23
Dear all,

After updating to 2.6.39-0-generic (running Natty on a Lenovo X220),
I have the following error (usually after attempting to or resuming
from suspend):

[drm:pch_irq_handler] *ERROR* PCH poison interrupt

The 2.6.38 kernel produces random freezes which are now gone. However,
this problem also makes the system completely unresponsive and requires
a reboot. Suspend/resume was working fine with 2.6.38.

Any help is appreciated.

Martin

---

### Post by williumbillium on 2011-05-25
This may help you.  There's a patch in the thread below if you feel like recompiling but looks like it should be fixed in 2.6.40 otherwise.

[http://groups.google.com/group/linux.kernel/browse_thread/thread/9ec0a2e305a296be/b673f37cfc79f7c3?show_docid=b673f37cfc79f7c3](http://groups.google.com/group/linux.kernel/browse_thread/thread/9ec0a2e305a296be/b673f37cfc79f7c3?show_docid=b673f37cfc79f7c3)

---

### Post by manybodycpa on 2011-07-17
Hi!

I have seen this patch as well, but have not managed to compile the driver.

Also, I have installed the 3.0.0 kernel (aka 2.6.40), but the issue persists
(looking at the intel driver source, the patch has not been included yet).

Best

Martin

---

