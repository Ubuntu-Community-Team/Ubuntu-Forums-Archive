---
title: "Kernel update causes unity to reset"
date: 2011-07-13
forum: General Help
---

### Post by rueben on 2011-07-13
Hello people

I just upgraded my kernel from 2.6.38-8 to 2.6.38-10 in ubuntu 11.04 from the update manager. 

The problem is, after rebooting and using kernel 2.6.38-10, unity seems to have been "reset". That means no icons on the sidebar besides the workspace switcher, app launcher and file launcher. All the shortcuts are gone; the icon size on the sidebar is back to 48px. Basically it's looks like a fresh install. 

Is there a way to fix this or do I have to manually drag all the shortcuts to the sidebar again?

---

### Post by philinux on 2011-07-13
> **rueben said:**
> Hello people

I just upgraded my kernel from 2.6.38-8 to 2.6.38-10 in ubuntu 11.04 from the update manager. 

The problem is, after rebooting and using kernel 2.6.38-10, unity seems to have been "reset". That means no icons on the sidebar besides the workspace switcher, app launcher and file launcher. All the shortcuts are gone; the icon size on the sidebar is back to 48px. Basically it's looks like a fresh install. 

Is there a way to fix this or do I have to manually drag all the shortcuts to the sidebar again?

I just this minute rebooted after the kernel update and checked this for you.
I don't use unity at all but I had set up some shortcuts.
They are still there for me after the update.
Back to classic now.

---

### Post by Frogs Hair on 2011-07-13
Try this command.```
unity --reset-icons
```

---

### Post by rueben on 2011-07-13
That didn't help. The sidebar doesn't hide and compiz is reset even though in compiz settings manager everything seems to be the way it is.

I guess I am stuck with 2.6.38-8 for now

---

### Post by philinux on 2011-07-13
> **rueben said:**
> That didn't help. The sidebar doesn't hide and compiz is reset even though in compiz settings manager everything seems to be the way it is.

I guess I am stuck with 2.6.38-8 for now

I'm not a unity expert but it sounds like its defaulted to unity 2d. Maybe graphics driver issue with the new kernel.

---

### Post by rueben on 2011-07-13
> **philinux said:**
> I'm not a unity expert but it sounds like its defaulted to unity 2d. Maybe graphics driver issue with the new kernel.

You were absolutely right! There was a problem with the ati driver. I had to force uninstall both fglrx and the amd proprietary driver and reinstall the driver. Now everything is back to normal. Thanks for pointing me in the right direction

---

### Post by pingu1 on 2011-07-15
Rueben  could you give me a step-by-step guide to what you did?
I have an ATI Mobilit Radeon 4200 card, and linux will not start after the kernel-update...

---

