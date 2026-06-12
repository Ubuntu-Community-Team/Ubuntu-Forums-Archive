---
title: "Problems with setting resolution in 8.10"
date: 2009-07-10
forum: General Help
---

### Post by Jeezus on 2009-07-10
I'm trying to use xrandr to set my resolution to 1280x768 because that is the native resolution of my monitor. I have apparently successfully added the resolution to the list of available resolutions, but for some reason I cannot change the resolution with xrandr. The monitor is hooked up via the VGA port, and it's radeon HD 3300 on-board video. I know that with radeon stuff the output is supposed to be VGA-0 instead of VGA, but I've tried both and it just doesn't seem to do anything when I hit enter, just refreshes the prompt... Anyone got any ideas?

---

### Post by CatKiller on 2009-07-10
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Jeezus on 2009-07-12
I have fixed the resolution problem by installing the ATI FGRLX drivers, but now I get this irritating flicker when I try to watch videos. It's really frustrating

---

