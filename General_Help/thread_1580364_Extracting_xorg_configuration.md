---
title: "Extracting xorg configuration"
date: 2010-09-23
forum: General Help
---

### Post by coyoteboy on 2010-09-23
Hi all, I'm having some trouble getting my touchscreen to work, primarily because of the switchover from a single xorg.conf to multiples and the dynamic setup. I'd like to be able to spit out the current config into an xorg.conf form so that I can then add on the section for the touchscreen manually and force X to use my new fixed .conf.

Anyone know of a way of achieving this? Dynamic hardware detection is all well and good when it gets it right, but with a serial-attached touchscreen I've spent the best part of an evening trashing X configs!

---

### Post by SteveDee on 2010-09-25
> **coyoteboy said:**
> Hi all, I'm having some trouble getting my touchscreen to work, primarily because of the switchover from a single xorg.conf to multiples and the dynamic setup. I'd like to be able to spit out the current config into an xorg.conf form so that I can then add on the section for the touchscreen manually and force X to use my new fixed .conf.

Anyone know of a way of achieving this? Dynamic hardware detection is all well and good when it gets it right, but with a serial-attached touchscreen I've spent the best part of an evening trashing X configs!

My understanding is that (from 9.10.onwards) you create your own xorg.conf with only the changes you require...but take a look at this: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

