---
title: "How do i keep ubuntu from changing links?"
date: 2006-06-03
forum: General Help
---

### Post by Abild on 2006-06-03
Hi everybody

In my current setup i have libGL.so.1, libGL.so.1.0.8762 and libGL.so.1.2.libmesa.
libGL.so.1 is linked to libGL.so.1.0.8762
I use the libmesa library when loading compiz by setting the LD_PRELOAD=/usr/lib/libGL.so.1.2.libmesa variable.

My problem is that ubuntu recreates the link between libGL.so.1 and libGL.so.1.2.libmesa every time i run synaptic. This causes X to crash whenever i launch compiz.

Can anyone tell me how to stop ubuntu from changing my files?

Thanks in advance :)

---

### Post by Abild on 2006-06-04
Anyone?

---

### Post by GoGoGadgetFeet on 2007-04-30
I'm sure by now you've solved this, but I just ran across it today.  It appears that some part of the boot process links libGL.so.1 to the last libGL.so that is listed (alphabetically?).  If manually altering the link gives you correct results until you reboot, then simply move the higher-named libGLs to another location.  Don't delete them!  You may wish you hadn't!

---

