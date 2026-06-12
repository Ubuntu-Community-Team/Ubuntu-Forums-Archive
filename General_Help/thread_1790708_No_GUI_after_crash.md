---
title: "No GUI after crash"
date: 2011-06-25
forum: General Help
---

### Post by hugo53 on 2011-06-25
I'm using Meerkat inside VMWare on Windows 7. My laptop restarted for some reason with the vm powered up. Now when I restart the vm I get a black screen with a terminal window - no GUI. 

The restart has:
FATAL: Module vmhgfs not found
FATAL: Module vmsync not found

How can I get the GUI back?

Thanks

---

### Post by wafflesausage on 2011-06-25
Try modprobe vmhgfs and modprobe vmsync and tell me what happens.

---

### Post by hugo53 on 2011-06-25
It repeats the messages from boot:
FATAL: Module vmhgfs not found.
FATAL: Module vmsync not found.

---

### Post by hugo53 on 2011-06-25
If I can't recover this vm, is there a way get my home tree out so I can copy into a new build?

Before I do that, isn't there a log file that will tell why it isn't staring the desktop on startup?

Thanks

---

### Post by hugo53 on 2011-06-25
Okay, I found a solution on the debian forums:

sudo apt-get install xserver-xorg

---

