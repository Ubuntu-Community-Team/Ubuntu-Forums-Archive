---
title: "Ignoring a device now"
date: 2010-12-21
forum: General Help
---

### Post by CheetoBandito on 2010-12-21
udev apparently does not let you ignore devices with rules anymore, at least that's what I'm reading.  If that's not the way to do it now, what is?  I can't seem to find the answer anywhere.

---

### Post by CheetoBandito on 2010-12-21
bump


I've found many threads like mine, none have replies... Even if you don't know the answer, any ideas on another place to ask?

> <   looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:37:04.0/host6/rport-6:0-0/target6:0:0/6:0:0:1':
<     KERNELS=="6:0:0:1"  This one is okay...

> >   looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:37:04.0/host6/rport-6:0-0/target6:0:0/6:0:0:0':
>     KERNELS=="6:0:0:0"
  This is the one I need to block...

I get a ton of Buffer I/O errors from the 2nd device...

---

