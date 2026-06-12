---
title: "No support"
date: 2010-06-04
forum: General Help
---

### Post by Colo2 on 2010-06-04
Hello all

I installed the NVIDIA driver for my card, and it resulted in my monitor saying: NO SUPPORT ~ When GDM starts. 

It must have stuffed up my xorg.conf file or something? How can I fix this? I can still use the command line (ctrl + alt + f1)

Thanks.

---

### Post by Colo2 on 2010-06-04
I really need this PC, for work. Please :( does someone know how I can fix this?

---

### Post by Jakiejake on 2010-06-04
Where did you install them from

---

### Post by Colo2 on 2010-06-04
official.

from nvidia site.

---

### Post by Colo2 on 2010-06-04
no one knows what I can do to fix this?? :(

---

### Post by ajgreeny on 2010-06-04
Delete any **/etc/X11/xorg.conf** that the driver has made using the command line, then restart the system and you should get the GUI with the default nv or nouveau driver from lucid.

This will give you a way to then go to the **System- Administration- Hardware Drivers** menu item to see if there is a driver available that way.

---

### Post by Colo2 on 2010-06-04
thanks for the reply.

I tried with the restricted driver before, and got the same problem. That time, the PC was blank, so I just re-installed. but this time I can't. I get this problem every time I install nvidia driver, no matter how I do it.

---

### Post by Colo2 on 2010-06-04
thanks :P I got my GUI back, but still no driver. Oh well :(

---

