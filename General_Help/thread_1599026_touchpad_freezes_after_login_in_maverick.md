---
title: "touchpad freezes after login in maverick"
date: 2010-10-17
forum: General Help
---

### Post by art_linux on 2010-10-17
I have synaptics touchpad on my Acer One netbook. When stuff is loading after login (panels, nautilus, etc.) i can move cursor and it's ok, but after a few seconds (when environment is loaded, i guess) touchpad freezes, and i have to press hardware "enable/disable touchpad" key twice to get it working. 
How to fix it?

---

### Post by s00n on 2010-10-17
i have the exact same problem.

in gdm while i don't login, my touchpad works. i can even press fn+f9 to toggle it on/off and it works. after login stage, when the session is loaded, it stops working and i can't get it to work again.

---

### Post by art_linux on 2010-10-21
really no suggestions?

---

### Post by utilitytrack on 2010-10-21
> **art_linux said:**
> How to fix it?

Try this:
```
$ synclient TouchpadOff=0
```

---

### Post by art_linux on 2010-10-21
i'm already pressing hardware "Touchpad on/off" key in order to do this.
Is there any solution to stop touchpad from switching off?

---

### Post by sledwich on 2010-10-27
The synclient command works for me but I have to enter for every login. Its very off as it does not happen on another login I have.

Never had these problems with 10.04 - I am ditching 10.10 to go back to 10.04.

---

