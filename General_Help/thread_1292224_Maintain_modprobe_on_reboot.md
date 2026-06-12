---
title: "Maintain modprobe on reboot"
date: 2009-10-15
forum: General Help
---

### Post by lcoff on 2009-10-15
I have an old (non-usb) sidewinder gamepad.  I can get the gamepad working correctly in 9.04 by using the following commands:

sudo modprobe ns558
sudo modprobe sidewinder

On researching this I found that if I add

ns558
sidewinder

to /etc/modules these will load automatically on boot.  However this is not the case.  What am I doing wrong??

---

### Post by blueridgedog on 2009-10-15
Can you post the content of your /etc/modules file?

---

### Post by lcoff on 2009-10-16
> Can you post the content of your /etc/modules file? 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ns588
sidewinder

---

### Post by blueridgedog on 2009-10-16
As an alternative, you could put the lines:

```
modprobe ns558
modprobe sidewinder
```

At the end of the file /etc/init.d/rc.local

With:
```

gksudo gedit /etc/init.d/rc.local
```

Be careful!

---

### Post by lcoff on 2009-10-16
Thank you for helping with this.

I added the lines as provided to /etc/init.d/rc.local and on reboot it is still not working.

---

### Post by lcoff on 2009-10-16
I should have noticed the error when I posted the contents of my /etc/modules file.  I had a typo it should have read ns558 not ns588.  Works perfectly now!

Thank you.

---

