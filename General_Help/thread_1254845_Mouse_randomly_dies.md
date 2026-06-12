---
title: "Mouse randomly dies"
date: 2009-08-31
forum: General Help
---

### Post by hunterzaiah on 2009-08-31
I'm having a serious problem with my jaunty installation. The mouse stops working after random periods of time of the computer being on. My problem seems very similar to the one posted here:
[http://ubuntuforums.org/archive/index.php/t-421581.html](http://ubuntuforums.org/archive/index.php/t-421581.html)
But I've tried the listed solution  (appending 'acpi=force irqpoll' to the kernel line of menu.lst) to no avail.

The keyboard and rest of the computer work fine after the mouse dies, and there are no processes that seem out of order with top or pstree. 

I really need some help with this problem. I've been a long time linux user, but this bug is frustrating me to the point that I'm considering switching back to Windows if I can't get it fixed.

Thanks in advance for any help, let me know if there are any configuration files that you'd like to see .

-Isaiah

---

### Post by fragos on 2009-09-01
I've perhaps the same problem. On occasion the cursor disappears from the screen. I've set the Ctrl key to help locate my cursor and it shows the cursor is in the upper right hand corner. I've found that unplugging the mouse's USB cable and plugging it in again works every time.

---

### Post by earthpigg on 2009-09-01
hi,

these aren't wireless mice that are left plugged in and turned on when not in use, are they?

---

### Post by fragos on 2009-09-01
> **earthpigg said:**
> hi,

these aren't wireless mice that are left plugged in and turned on when not in use, are they?

Mine is a wired mouse.

---

### Post by paradigm2 on 2009-09-01
Is this a laptop?  I've had the same issue on a laptop and suspected that it might have been heat related.  What are the temps in the case (desktop) or in the laptop?  If you need this info in Gnome there are a few applets such as the "Sensors Applet" which well give this information.

---

### Post by earthpigg on 2009-09-01
> **paradigm2 said:**
> in Gnome there are a few applets such as the "Sensors Applet" which well give this information.

you dont *need* gnome, though there may be some GNOME front ends that use this as the backend or something else. the the terminal program is called lm-sensors.
```
sudo apt-get install lm-sensors
```

to configure it:
```
sensors-detect
```

to run it:
```
sensors
```

---

### Post by fragos on 2009-09-01
Mine is a desktop and I use the temp sensors. My system isn't running too hot. To be honest it happens infrequently enough that I'm not concerned. I've also noticed that a tiny piece of lint can find it's way inti the LED or laser path and can cause erratic cursor responses to mouse movement. I just blow it out and I'm good again.

---

