---
title: "Wireless not working..."
date: 2010-03-16
forum: General Help
---

### Post by jblaven on 2010-03-16
OK,

I reinstalled Ubuntu yesterday and now I can't seem to get reconnected to the internet...  If I remember correctly, the last time I used my Wireless G, it worked right out of the box.  Now it doesn't.  Any ideas?

Thanks,

Joe

---

### Post by trideceth12 on 2010-03-16
What do you mean "not working"... Can you connect to the network at all? Does your wired connection work? Can you see your network's ESSID?

---

### Post by l4zy on 2010-03-16
Can you see any SSIDs ?

If so what kind of authetication / encryption does that WLAN-BOX use ?

---

### Post by amite on 2010-03-16
check bcmlw package .if not installed install it from cd

---

### Post by jblaven on 2010-03-16
> **trideceth12 said:**
> What do you mean "not working"... Can you connect to the network at all? Does your wired connection work? Can you see your network's ESSID?
 
How do I check to see if I can see my network's ESSID? 
 
Usually when I insert the USB Wireless G adapter, it shows up in the panel on my desktop, showing me the different wireless networks in the surrounding area.  
 
Now, it does nothing.  I tested the adapter on another computer on the same wireless network and it works fine.
 
This computer I am typing on now, is a 3rd wireless computer on the same network, so it is also working fine...
 
Joe

---

### Post by jblaven on 2010-03-16
Right now, I've got no encryption (to help with setting it up).

---

### Post by trideceth12 on 2010-03-16
> **jblaven said:**
> USB Wireless G adapter

Ahh.. no experience with USB wireless adaptors.

---

### Post by nightwolf2k5 on 2010-03-16
When you login, make sure that the session (at the bottom) is set to Gnome. Sometimes if it is set to Failsafe Gnome, your issue happens.

---

### Post by jblaven on 2010-03-16
> **amite said:**
> check bcmlw package .if not installed install it from cd
 
 
Wonderful...  I get an error message:
 
"Unable to mount Ubuntu 9.10 i386
Error mounting: mount exited with code 32:
mount: unknown filesystem type 'iso9660'

---

### Post by jblaven on 2010-03-16
> **nightwolf2k5 said:**
> When you login, make sure that the session (at the bottom) is set to Gnome. Sometimes if it is set to Failsafe Gnome, your issue happens.
 
OK, checked it...  it was set to Gnome.

---

### Post by carlosgs91 on 2010-03-16
.

---

### Post by jblaven on 2010-03-16
Here is the latest...

Since this was a new install (yesterday) and I didn't reformat the drive before installing, I figured that a reinstalling it with a reformat would make the difference.  It did.

I left my /home partition as is.

---

