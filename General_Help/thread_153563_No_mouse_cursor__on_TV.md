---
title: "No mouse cursor  on TV"
date: 2006-04-01
forum: General Help
---

### Post by revolver on 2006-04-01
Installed new NVidia drivers 8178 and mouse corsor dissapeared on my TV (NVidia TVout). On my LCD display every thing is working. 
On TV I can see that mouse indeed response to left/right clisks. It is just no cursor icon, I can not see it.
Mouse is creative wireless usb device. Xorg.conf file attached.

Any ideas?  Thanks.

---

### Post by revolver on 2006-04-01
Adding to "Screen" section of TV following line solve the problem
 Option         "sw_cursor"

---

