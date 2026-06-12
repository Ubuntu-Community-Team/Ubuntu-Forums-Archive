---
title: "lsmod and built-in kernel modules"
date: 2010-01-01
forum: General Help
---

### Post by james_mcl on 2010-01-01
Hi all,

I've been trying to find out if a problem I've been experiencing in Karmic is kernel bug 9147. One of the pieces of advice I've found was to unload the ac, thermal, battery, and processor kernel modules. However, none of these show up when I run lsmod.

Are they built into later versions of the kernel? If so, would this explain why they didn't show up? (They were all present when I ran lsmod in Hardy, btw.)

Thanks,

JM.

---

### Post by tom4everitt on 2010-01-01
Short answer: Yes it would explain it. Only loaded modules are shown by lsmod, and built-in modules are not loaded. And no, you can not unload built-in modules. 

What you could try is building your own kernel from source. Then you get to decide which modules to build in, and which to load as modules.

---

