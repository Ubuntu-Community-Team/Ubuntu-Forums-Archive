---
title: "kernel 2.6.28-15.generic"
date: 2009-09-14
forum: General Help
---

### Post by jamillikan on 2009-09-14
Why does DOSEMU SEGfault in some DOS applications on kernel 2.6.28-15.generic, while it does not on kernel 2.6.27-11?  What changes have taken place in the kernel to cause this issue we're experiencing?

While testing on Karmic, this issue is also present.  Can some PLEASE stabilize DOSEMU and eliminate the SEGfaults?  We will continue using 2.6.27-11 until the issue is resolved.

Thanks!

Joe

---

### Post by rCXer on 2009-09-14
It may be related to [this bug](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/425433) reported last week. Which application are you trying to run and did you try it in dosbox?

---

### Post by jamillikan on 2009-09-14
It is TurboCAT Professional when using the dictionary editor.  I checked the bug report, so it seems like I'm not the only one experiencing this issue.  Hopefully, it will be corrected so we can move forward to Karmic.  I certainly hope so.

To answer your second question about dosbox:  no, it certainly will not run at all in dosbox because of the requirements of serial ports, parallel ports, etc.

---

