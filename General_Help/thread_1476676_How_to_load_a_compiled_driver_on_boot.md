---
title: "How to load a compiled driver on boot?"
date: 2010-05-08
forum: General Help
---

### Post by ambdeep on 2010-05-08
I wanted to know if there is any way of adding a driver that i compiled during boot apart from adding it in ```
/lib/modules/<kernel version>/kernel/drivers
```
It works fine till i update to a newer kernel...then i have to add it in the new kernel file....so is there a permanent method?

---

### Post by ambdeep on 2010-05-09
*bump*

---

### Post by Shazaam on 2010-05-09
Maybe give dkms a try?

[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)
[http://packages.ubuntu.com/karmic/dkms](http://packages.ubuntu.com/karmic/dkms)
[http://packages.ubuntu.com/Lucid/dkms](http://packages.ubuntu.com/Lucid/dkms)

---

### Post by ambdeep on 2010-05-12
how exactly do i use dkms?

---

