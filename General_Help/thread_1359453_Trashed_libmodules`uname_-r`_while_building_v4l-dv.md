---
title: "Trashed /lib/modules/`uname -r` while building v4l-dvb"
date: 2009-12-19
forum: General Help
---

### Post by AW01545 on 2009-12-19
I'm not complaining about this really, I learned a lot about the kernel building environment by doing this, but I believe I'm going to have to reload to get around this problem.

What I was trying to do was build the v4l-dvb driver package from the latest Mercurial v4l-dvb repository.   I'm running Mythbuntu 9.10.

I ended up with some funny symbol reference errors where my saa7134.ko referred to symbols in ir-common.ko, but even though these symbols seemed to be in (and the modules loaded), the errors were about non-agreement on symbols, so I think there must've been some kind of version system for the symbols:

[  221.185767] ir_common: disagrees about version of symbol module_layout

While working on this problem, I foolishly trashed my complete /lib/modules/`uname -r`, and then just deleted it.  I couldn't reboot in this condition, so I went into recovery mode from a live CD, and copied the same corresponding modules from another system running the identical release (both are running 32-bit kernels.)

I figured this would work, but to my surprise, I received an INVALID MODULE FORMAT error:

FATAL: Error inserting saa7134 (/lib/modules/2.6.31-16-generic-pae/kernel/drivers/media/video/saa7134/saa7134.ko): Invalid module format


Now, I'm pretty certain I'm going to rebuild this machine.  I'm going to lose some recorded material and my configuration, but I've learned a lot of lessons.

Some things that would be helpful to know are:

How do you recover your modules, and is it possible to backup/restore them?

How would I go about backing up my mythtv environment?

What am I missing from my build procedure that my v4l-dvb modules don't work?

Thanks!

---

