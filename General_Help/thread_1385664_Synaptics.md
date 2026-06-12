---
title: "Synaptics"
date: 2010-01-19
forum: General Help
---

### Post by Marvin666 on 2010-01-19
Does anybody know of an utility to let me setup my touchpad? I mean like enabling horizontal, and vertical scroll, setting what corner taps do, and setting the boundaries of all these zones.

---

### Post by michy99 on 2010-01-19
I don't know if it will do everything you want, but this will do some of them anyway. Install the gpointing-device-settings package. For some reason it doesn't make a menu entry so you have to start it from a terminal. (You can add a menu entry for it.)

---

### Post by marshmallow1304 on 2010-01-19
Edit: That one ^ is probably better.  Its description says it is a successor to gsynaptics.


[gsynaptics]("apt://gsynaptics") will configure vertical and horizontal scrolling.  I don't know about the rest.

---

### Post by baddog144 on 2010-01-19
I've always used gsynaptics

EDIT: If you're just dealing with the one input device, gsynaptics seems more or less identical to gpointing-device-settings

---

### Post by Marvin666 on 2010-01-19
Gsynaptics spit this out at me in an error message: ```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics 
```
Neither of those files exist.
Gpointing recognizes it as a generic ps2 mouse.

---

### Post by n0dix on 2010-01-19
> **Marvin666 said:**
> 
Neither of those files exist.


Create the xorg.conf. Then use the program.

---

