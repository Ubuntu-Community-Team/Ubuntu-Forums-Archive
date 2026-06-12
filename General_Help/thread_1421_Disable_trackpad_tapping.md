---
title: "Disable trackpad tapping"
date: 2004-10-20
forum: General Help
---

### Post by b-m-w on 2004-10-20
All,

How might I go about disabling trackpad tapping? If anything on a laptop can get me in trouble, my inability to tap, tap/drap, double-tap will do it!

I have looked into the mouse settings but cannot find anything trackpad specific. Please point me in the right direction.

Peace,
Brandon

---

### Post by knappen on 2004-10-21
What type of touchpad do you use?

---

### Post by b-m-w on 2004-10-21
According to my Windows drivers it is a Synaptic TouchPad v. 5.9. It is on a Gateway 450 series laptop.
--
Brandon

---

### Post by daniels on 2004-10-22
Edit /etc/X11/XF86Config-4, and in the Synaptics InputDevice section, add:
        Option "TapButton1" "0"

---

### Post by Bob Collins on 2004-11-03
[QUOTE=daniels]Edit /etc/X11/XF86Config-4, and in the Synaptics InputDevice section, add:
        Option "TapButton1" "0"[/QUOTE]
 Does Ubumtu use Peter Osterlund's Synaptics TouchPad driver? I poked around and didn't find it. Or is there a general touchpad option in XFree86? I didn't find that either.

Bob Collins
Sunnyvale CA USA

---

