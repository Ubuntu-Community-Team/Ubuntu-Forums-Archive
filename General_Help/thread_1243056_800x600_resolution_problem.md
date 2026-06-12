---
title: "800x600 resolution problem"
date: 2009-08-17
forum: General Help
---

### Post by WesParmalee on 2009-08-17
Hey guys, I've been having this problem with running my screens resolution 800x600, it's not the monitor as I have ran that mode before on it. I'm thinking it might be a graphics driver problem, but if I install older drivers for it (version 173, 96) it might cause other types of problems :(

Has anyone been able to fix this issue? If so, how?

And my Graphics chip is nvidia 6150 se

Thanks in advance.

---

### Post by running_rabbit07 on 2009-08-17
This is where I had to go to get the proper driver. You menu will look different but what you need will be in the same place. System>Administration>Hardware Drivers.

---

### Post by wojox on 2009-08-17
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

You card is listed.

---

### Post by philcamlin on 2009-08-17
i found this this should be helpful :)
[http://ubuntuforums.org/showthread.php?t=402301](http://ubuntuforums.org/showthread.php?t=402301)

---

### Post by CatKiller on 2009-08-17
> **WesParmalee said:**
> it's not the monitor as I have ran that mode before on it.

That doesn't mean that it's not the monitor that's causing the problem now.

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

### Post by running_rabbit07 on 2009-08-18
Did any of these posts help you?

---

