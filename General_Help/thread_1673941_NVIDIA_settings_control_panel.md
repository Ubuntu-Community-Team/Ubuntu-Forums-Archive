---
title: "NVIDIA settings/ control panel"
date: 2011-01-23
forum: General Help
---

### Post by mocatz187 on 2011-01-23
In a previous version of UBUNTU I was able to enter a NVIDIA control panel to adjust my RGB settings.  Now I'd like to change it slightly but there doesn't seem to be a NVIDIA control panel.
There used to be two of them.  After installing the video driver, If I tried to go into UBUNTU video settings  I would get a console message stating I now need to use NVIDIA control panel and would automatically open it for me.
Does anyone know where it went or what my options are

---

### Post by efflandt on 2011-01-23
If you are able to go into **Monitors**, it sounds like nvidia drivers are  either not installed or not active for some reason (not installed  properly or bad or missing /etc/X11/xorg.conf).

Did you reboot after activating nvidia in System > Adminstration > Additional Drivers (or Hardware Drivers Lucid or earlier)?  If you go there, does it suggest activating nvidia, say "activated, but not in use", or say "activated".  If either of the latter 2 cases chose "remove".  Then in any case try "activate", then reboot.

If you installed **nvidia-current** using Synaptic, maybe you forgot to also install **nvidia-settings** and/or **nvidia-current-modaliases**, and might not have any /etc/X11/xorg.conf.  In that case the above paragraph should resolve it.

If you manually tried installing drivers with a script from nvidia, I cannot help you.

---

### Post by mocatz187 on 2011-01-24
My drivers run my desktop environment just fine and any installs or changes would be from an update or some kinda corruption.  I have been running UBUNTU on this computer for over 3 years and the control panel was always under system.  My color isn't off by much, some would look and not even notice anything.  I just thought maybe I would undo the extra 10% red I added to it but since it's gone...
On another forum someone suggested I access it from the terminal but when I input nvidia-settings as they suggested the terminal stated that nvidia-settings did not exist so I don't know whats going on.
three years ago when I first installed Ubuntu I had to reboot after an update to get my resolution to display properly and it was horrible looking before that so I know my driver is functioning to some degree because my resolution is perfect. I can't change it but it's not bad.  I can definitely live with it but when stuff just disappears it can be a little unnerving.

---

### Post by mocatz187 on 2011-01-24
Monitors under "system" reminds me of the original UBUNTU display settings. It does offer some adjustment but no RGB.  So I guess I'm only missing one control panel.  This must be the control panel that would not open all the way after I rebooted  from my original install because it knew I had the NVIDIA working properly and would ask if I wanted to open NVIDIA instead.  remembering that is giving me a better feel for what might be going on here. If I try to install a new one from terminal will it automatically replace the corrupted one if it's even there anymore or should do some steps prior to  installing.
Thanks.

---

### Post by mocatz187 on 2011-01-24
hmm.  Seems that after reading lots about thisa the only conclusion I can come up with is that Ubuntu has adopted a microsoft type policy where they think we're too stupid to mess with our settings and they have decided to deactivate these things whenever you get an update.  Can it be fixed, of course. Just goto System/administration/hardware drivers. There you should see that your NVIDIA 3D graphics accelerator disabled.  Simply enable it.
Problem is that evry update will require you to check ALL of the things that some punk decided you didn't need.
Previously I had a problem with viewing Youtube and other videos in full screen. Jittery video. I had to pop out to get it to work.  Well, it's fixed.
I wish I could remember where all of those forum posts were at that I was reading that nobody new how to fix because this is the solution.  I guess people just haven't gotten used to the idea that updates are basically gonna wipe a whole bunch of stuff out without telling us.

---

