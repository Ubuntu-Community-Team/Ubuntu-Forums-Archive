---
title: "Kernel Konfusion"
date: 2011-07-30
forum: General Help
---

### Post by holadebob on 2011-07-30
My new update notification says "This package contains the Linux kernel image for version 2.6.32 on x86/x86_64..........
............**You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed**."

This new update includes changes to 2.6.32-33.70, 2.6.32-33.71

My newest meta package listed in Synaptic is 2.6.32.33.39 and is installed.

Is this an error or am I ignorant of Kernal update codes?

Also, can I run these three Kernal file updates (linux-headers, linux headers-generic, linux-image) without problems? The phrase "You likely do not want to ....." seems subjective and doesn't make things very clear to me. 

Thank you 
10.04 happily cruising along

---

### Post by grahammechanical on 2011-07-30
As I understand it, a meta package contains everything needed, dependencies and such which would have to be installed in addition to the kernel image package. It is for this reason that the comment is made "you likely do not want to install this package directly."

If you install just those packages directly you will have to install other stuff directly as well. If you install the meta package then those packages get installed indirectly along with the other stuff that they need.

This is my understanding.

Regards.

---

### Post by holadebob on 2011-07-30
What I find a bit confusing is that the meta package in synaptic is an older version than the updated kernel listed on the update manager. Maybe I need to wait until the meta package offer in Synaptic is updated to reflect the update manager kernel changes?

Thank you

---

### Post by holadebob on 2011-07-31
Bump Please give me some info...

---

### Post by SavageWolf on 2011-07-31
You can go back to an older kernel if you want to, so you wont be left with an utterly broken system if you update your kernel "too early". I'd recommend you install the kernel that the update manager recommends, if only to keep it quiet.

---

### Post by holadebob on 2011-08-01
I went ahead and did the update with no problems. Still don't understand the meta package kernel update system, but as long as it works, I guess I shouldn't worry.

Thank you all for the help!

---

