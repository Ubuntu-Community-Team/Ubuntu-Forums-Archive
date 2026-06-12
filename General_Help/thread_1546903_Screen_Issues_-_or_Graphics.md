---
title: "Screen Issues - or Graphics"
date: 2010-08-06
forum: General Help
---

### Post by ExSuSEusr on 2010-08-06
Ubuntu (forget the version I haven't updated in a while).
8800 GTS
AMD 6400 Dual Core 3.2
 
I run a dual boot system with XP. I went to swap from Windows to Ubuntu and when I logged in the screen was enormous. In fact 1/4 of the desktop (the upper left corner) took up the entire monitor. No idea even where to begin to fix this. It was running perfectly fine without updates or screwing with the settings.
 
Any ideas?

---

### Post by What Rights on 2010-08-06
If you have the NVIDIA drivers, open the Nvidia X server settings in the System>Administration and change your monitor's resolution.

---

### Post by ExSuSEusr on 2010-08-06
Tried that - the only option I get is 640 x 480.

---

### Post by thehipho on 2010-08-06
Did you try to Reinstall NVIDIA drivers?

---

### Post by ExSuSEusr on 2010-08-06
It gives me an "unknown monitor" message - so I am going to try a couple of things first...  video card drivers are a PITA to mess with / install.  Maybe it's just nVidia.
 
Going to plug in a different monitor and see if it detects it - then plug the main monitor back in - see if it will find it then.
 
I really don't think it's the video card - they were installed long ago and I've never had a problem - don't like updating things once they're working.

---

### Post by What Rights on 2010-08-06
> **ExSuSEusr said:**
> It gives me an "unknown monitor" message - so I am going to try a couple of things first...  video card drivers are a PITA to mess with / install.  Maybe it's just nVidia.
 
Going to plug in a different monitor and see if it detects it - then plug the main monitor back in - see if it will find it then.
 
I really don't think it's the video card - they were installed long ago and I've never had a problem - don't like updating things once they're working.
If you don't like updating things once they are working, wouldn't you say your monitor problem labels it as not working?

---

### Post by ExSuSEusr on 2010-08-06
That actually worked.

Shut the system down.
Unplugged the monitor.
Plugged in a different monitor.
Fired up the machine.
Booted in (everything perfect).
Shut down the machine.
Plugged the old monitor back in.
Fired it up.

Good to go now.

Neat little trick if you happen to have two monitors.

---

### Post by What Rights on 2010-08-06
Probably reset the monitor configuration in xserver.

---

