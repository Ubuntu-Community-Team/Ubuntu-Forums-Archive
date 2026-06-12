---
title: "Ubuntu runs so bad!"
date: 2009-12-05
forum: General Help
---

### Post by wle on 2009-12-05
My computer is 2.00GHz and 1.50 gb of ram

And when I run visual effects on ubuntu it is so ridiculously slow and choppy. My computer ran great on windows nothing like what is happening with ubuntu.

I don't think this is supposed to be like this because I looked up the system requirements for visual effects and it said you need 

[LIST]
[*]1.2 GHz x86 processor
[/LIST]

[LIST]
[*]384 MB of system memory (RAM)
[/LIST]

[LIST]
[*]Supported graphics card
[/LIST]

So is there anything I can do to make ubuntu run better for me?

---

### Post by aznenemy on 2009-12-05
with that low of specs dont even try running anything like that its slow cause your trying to use the gpu to much

---

### Post by whitehaint on 2009-12-05
I didn't see it mentioned, did you get a driver for your graphics card? I would also upgrade your ram and 1.5 gigs is a bit low for any system nowadays.

---

### Post by ElSlunko on 2009-12-05
> **whitehaint said:**
> I didn't see it mentioned, did you get a driver for your graphics card? I would also upgrade your ram and 1.5 gigs is a bit low for any system nowadays.

Maybe for some things but in general 1.5 is much more than enough for regular usage in ubuntu.

---

### Post by rockfx01 on 2009-12-05
@aznenemy & whitehaint

Way to actually help him resolve the issue. :roll: 2.00 gHz and 1.5GB RAM is plenty to run Ubuntu.

@wle
The visual effects feature uses the graphics card. If it is running slow it probably means your graphics card driver doesn't support 3D acceleration.  I've had this same problem in the past.  Also, some of the older graphics cards might not support the newer implementations of the visual effects.

What make/model of graphics card does your system have?

You can install proprietary drivers from nvidia or ATI which are closed source but typically handle the graphics much better, but depending on how old your card is you still might not be able to get VFX working smoothly.

In the system menu, go to System->Administration->Hardware Drivers.  It should automatically detect if there are drivers available for your system.  Install them and reboot.

Try the visual effects again.  If it is still very choppy, or if there are no proprietary hardware drivers available for your video card, you might be out of luck for the visual effects (Compiz).  Everything else in Ubuntu should work just fine, just leave the VFX disabled.

If you really want to you can dig deeper and see if there is a way to custom configure your graphics settings and drivers, etc to get VFX working ok but you'll have to do some research on your own to figure that out if the above doesn't resolve your issue.

---

### Post by mickie.kext on 2009-12-05
Type 

> jockey-gtk

in terminal and see if there are any drivers showing up. If it does not show up, try to update system (either GUI app or 'sudo aptitude update') and than try jockey again.

---

### Post by whitehaint on 2009-12-05
Dude, did you not see I asked for clarification first on a graphics card driver?? Geez no need to be rude.

---

### Post by deathbyswiftwind on 2009-12-05
As stated before did you install your graphic card drivers? If not there are plenty of threads here to help you install ati/nvidia drivers or you could always use envy (install via synaptic) and it will install the ait/nvidia drivers for you.

---

