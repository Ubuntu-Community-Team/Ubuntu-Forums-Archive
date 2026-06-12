---
title: "When upgrading a kernel, how do you deal with video drivers?"
date: 2011-10-03
forum: General Help
---

### Post by WikedX on 2011-10-03
2 months ago I compiled Kernel 3,0 myself and it wouldn't work. I suspected video drivers. I went into failsafe terminal and removed everything ati from my system and it worked again, even in kernel 3.

However trying to use Ubuntus driver manager on kernel 3 failed and installing the drive right from ATI failed as well so I gave up and went back to kernel 2.6.38

I am wondering though how this is supposed to be done. Was I supposed to remove my video drivers before compiling the kernel?

---

### Post by Wayne_V on 2011-10-03
video drivers are kernel specific -- in general you can't load 2.6 drivers into a 3.0 kernel.   

I doubt ATI has 3.0 drivers available yet so you would have to use the open source driver (assuming it loads in a 3.0 kernel ... if not, you would have to compile xorg for the 3.0 kernel as well).

---

### Post by WikedX on 2011-10-03
> **Wayne_V said:**
> video drivers are kernel specific -- in general you can't load 2.6 drivers into a 3.0 kernel. 
 
I doubt ATI has 3.0 drivers available yet so you would have to use the open source driver (assuming it loads in a 3.0 kernel ... if not, you would have to compile xorg for the 3.0 kernel as well).
 
 
ahh
 
see now that can be an issue :(
 
Thanks for the issue

---

