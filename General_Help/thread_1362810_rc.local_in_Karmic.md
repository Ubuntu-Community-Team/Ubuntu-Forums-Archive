---
title: "rc.local in Karmic"
date: 2009-12-23
forum: General Help
---

### Post by linuxonbute on 2009-12-23
I needed to disable my touchpad which I did by adding 
 rmmod psmouse 
to /etc/rc.local
in ubuntu prior to Karmic this worked but it doesn't now.

permissions are:

-rwxr-xr-x  1 root    root       330 2009-12-20 16:06 rc.local

Any idea why?

---

### Post by bodhi.zazen on 2009-12-23
I am not familiar with your hardware , does that command work after you have finished booting ?

If so, the boot process has changed and many boot scripts run concurrently (meaning rc.local is NOT running last, and is thus run too early in the boot process). If you wish to use rc.local , add a sleep, 10 seconds is usually sufficient.

sleep 10
rmmod psmouse 

As an alternate, why not blacklist it ?

Open /etc/modprobe.d/blacklist

add psmouse at the bottom.

---

### Post by linuxonbute on 2009-12-24
> **bodhi.zazen said:**
> I am not familiar with your hardware , does that command work after you have finished booting ?


Yes, it does.
> **bodhi.zazen said:**
> 
If so, the boot process has changed and many boot scripts run concurrently (meaning rc.local is NOT running last, and is thus run too early in the boot process). If you wish to use rc.local , add a sleep, 10 seconds is usually sufficient.

And that tells me why it doesn't during boot. 
Thanks
> **bodhi.zazen said:**
> 
sleep 10
rmmod psmouse 

As an alternate, why not blacklist it ?

Open /etc/modprobe.d/blacklist

add psmouse at the bottom.

I will blacklist it so it doesn't affect anything else I might want to put in rc.local.

p.s The file I need to edit is /etc/modprobe.d/blacklist.conf

Thanks very much.
Norman

---

