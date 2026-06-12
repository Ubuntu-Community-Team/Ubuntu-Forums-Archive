---
title: "VNC Server Configuration"
date: 2009-08-12
forum: General Help
---

### Post by stevebond001 on 2009-08-12
Hi
I have installed VNC onto my (Jaunty) PC and am accessing it from an XP machine (using tightVNC)

Does anyone know how to configure the PC (or connecting client) to allow me to:

1.  Scale the viewer to show all of the desktop in the viewer window.
2.  Blank out the Jaunty PC screen when I am accessing it from the tightVNC viewer

I have tried looking around for this information but there seems to be no definitive guide on how to do this.

Many thanks in advance

---

### Post by stevebond001 on 2009-08-13
Anybody?  Please help!:(

---

### Post by kg87 on 2009-08-13
TightVNC - At least your using the right client ;)

all you need to do to scale the screen (providing its Windows your viewing it on), is to open VNCviewer. Then go options, and then you need to set the scaling (its a percentage). remember, if its not quite right you can manually set it by typing it in. 

ok, and on the other one, I know how to do it in windows, but not sure Ubuntu side of things. i DO know for certain that option is set within VNCserver, as far as that i dont know, 

you could try in terminal "man <name-of-vnc-server>" and see if that helps, or even "man <name-of-vnc-server> | cat > VNCserverManual" which will save it to a text file for further reading.

---

### Post by stevebond001 on 2009-08-13
KG87
Thank you very much for your help.  I'll give it a go and let you know

Cheers

---

### Post by stevebond001 on 2009-09-03
Hi
I've installed tightvnc server on my host and ran a "man tightvncserver" in a terminal session, but there;s no mention of suppressing the display whilst connected via vnc.  Any other ideas?

Many thanks in advance

---

