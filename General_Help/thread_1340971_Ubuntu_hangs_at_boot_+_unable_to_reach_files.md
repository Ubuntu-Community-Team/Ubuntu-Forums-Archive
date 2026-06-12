---
title: "Ubuntu hangs at boot + unable to reach files"
date: 2009-11-29
forum: General Help
---

### Post by doc.arne on 2009-11-29
Hey,

i've got a really urgent problem. My ubuntu hangs at boot saying DRDY err. I know this usually means a hard drive is broke, but i don't think mine is (i can start windows just fine with dual boot).

My windows printer was hooked up to my computer when i tried to start it up. I unlugged it and shut down my computer manually. Could that be the cause?

If you can't answer that, can at least anyone tell me where i can find my ubuntu files in windows. They're in the same partition so things like explore 2fs don't work there. My windows was installed first and my ubuntu on a fake partition on top of that. I can't read my files through the live cd either, because he only mounts the partition with my windows files.


Please help me! I need this file immediatly!

---

### Post by davidpramana on 2009-11-29
> **doc.arne said:**
> My ubuntu hangs at boot saying DRDY err. I know this usually means a hard drive is broke, but i don't think mine is (i can start windows just fine with dual boot).

My PC too. but, i'm okay with it because i use Ubuntu on my netbook now. I hope someone can help u (and me). :D

---

### Post by john newbuntu on 2009-11-29
If you suspect a bad disk and if you know the partition where ubuntu was mounted, you may need to run the e2fsck command after mounting ubuntu from a liveCD.  For example, if it is /dev/sda2

sudo e2fsck -C0 -p -f -v /dev/sda2

---

