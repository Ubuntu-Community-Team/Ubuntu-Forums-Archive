---
title: "Moniter and mouse problems"
date: 2009-09-05
forum: General Help
---

### Post by Kealan124 on 2009-09-05
My grandmother's computer was hit by some bad adware, and she asked me to help her. I decided it would be better to wipe everything and start again. Instead of buying an XP installation disk, I used Ubuntu 9.04. Her CD drive doesn't work, and I installed it via USB drive. It installed properly, but now it has rather big problems.

First of all, the screen. When I try to adjust the resolution, it gives me several choices, the highest of which is 800x600. Her moniter is able to run 1280x1024, but it says unknown for the moniter. Trying to install the driver Ubuntu recommends (and the other two choices in the menu, as well) tells me I need to reset. After I do, a message tells me the moniter does not support the display settings. (The ubuntu loading bar runs, and I see the mouse for just a fraction of a second). To fix this, I reboot, press esc and launch into recovery mode, where I have it fix display problems. I have tried googling this, and attempted several of the fixes I have found, with no results.

Also, the mouse. After a few minutes of use, it just stops. The cursor is still on-screen, and the lights on the mouse are on, but the cursor does not move or click no matter what I do. I have to restart every time this happens. (The computer inself still works, and I can still type, but I lose all mouse control).

I have been trying various things to fix this for DAYS now. My grandmother wants to be able to use her computer again, please help..........

If it helps, her computer is a Dell Dimension C521, with an nVidia GeForce 6150 LE graphics card, iirc.

---

### Post by Kealan124 on 2009-09-05
Anyone? :(

---

### Post by CatKiller on 2009-09-05
> **Kealan124 said:**
> Anyone? :(
Patience is a virtue, you know.

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

Can't help you with the mouse.

---

