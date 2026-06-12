---
title: "Nvidia drivers/ resolution issues"
date: 2009-08-23
forum: General Help
---

### Post by froggger on 2009-08-23
I am having some issues installing/finding the correct drivers for my card.
Its an old agp geforce mx420.

I have tried no drivers, the drivers recommended in the hardware manager, and have done whats on [this site]("http://guitarchasers.org/guchmain/archives/323").

The website steps have been the most successful, I got it up to 1024x768, but then on reboot I got a message saying that I needed to either use generic settings, my own settings, or backup settings.  If I chose generic, it would go back to 800x600, if I went with custom, it left me at 1024x768, but it gives me the same prompt every reboot, and I haven't tried the backup settings, because that's not what I want.

I have tried to custom edit xorg.conf, but that didn't change anything.
The NVIDIA settings don't have any options for my display currently, just a couple options about the app itself.

I'm at a loss here, I'm a linux noob, but consider myself a fast learner.

Any help would be appreciated.

---

### Post by CatKiller on 2009-08-23
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

### Post by froggger on 2009-08-23
that did it, thanks so much!

---

### Post by CatKiller on 2009-08-23
No worries :)

---

