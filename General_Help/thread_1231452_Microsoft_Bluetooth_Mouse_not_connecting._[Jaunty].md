---
title: "Microsoft Bluetooth Mouse not connecting. [Jaunty]"
date: 2009-08-04
forum: General Help
---

### Post by Mike_IronFist on 2009-08-04
Here's a problem I'm having a super tough time fixing. I have a Kensington Bluetooth Micro-Adapter plugged into my laptop, and Ubuntu detects it properly. Yay.

I set my mouse to "discovery mode" (holding the bluetooth button so that a computer can discover it.) and Ubuntu is detecting the mouse. Excellent.

I try to connect to it. The bluetooth applet says "connecting" for like half a second, then says the device was connected successfully. This, however, is false, because my mouse is still blinking to indicate that it's in discovery mode. WHAT?

On previous installations of Ubuntu (Jaunty, same version every time) I've gotten the mouse connected before, no issues then. I also have a dual boot setup and my mouse has no issues being paired and unpaired with my bluetooth adapter when running it in Windows. The issue can't possibly be the mouse.

Please, someone help?

My bluetooth visibility setting is "Always Visible" so that the mouse can find my laptop. Previously, this made everything gravy. Now it doesn't make one lick of difference.

---

### Post by BslBryan on 2009-08-04
Hmmm.  Try running```
gksudo gedit /etc/default/bluetooth
```

And change the HIDD_ENABLED value from 0 to 1.

---

### Post by Mike_IronFist on 2009-08-04
> **BslBryan said:**
> Hmmm.  Try running```
gksudo gedit /etc/default/bluetooth
```

And change the HIDD_ENABLED value from 0 to 1.

Here's something odd. I just rebooted into Ubuntu (I was reading this from Windows, long story) and for no reason at all, my mouse just WORKED.

Go figure.

---

### Post by BslBryan on 2009-08-04
Good.  I'm glad there's no problem anymore.

---

