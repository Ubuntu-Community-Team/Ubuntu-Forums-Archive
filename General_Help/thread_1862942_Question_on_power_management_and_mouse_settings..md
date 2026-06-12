---
title: "Question on power management and mouse settings."
date: 2011-10-17
forum: General Help
---

### Post by Linuxperiment on 2011-10-17
How can I disable tap-to-click and edge/horizontal scrolling? There's no settings for the mouse. I have a Synaptics touchpad.

EDIT: Ok for the mouse settings what I ended up doing is installing gpointing-device-settings. It works but when I restart, it does not work anymore. I'm starting to think it just does what the synclient from terminal does, but I'm not entirely sure. Does anyone know how to make this program run from the start at default and disable tap to click + scrolling?

---

### Post by resurrectionfern on 2011-10-17
For your touchpad try running synclient from a terminal. It'll list all the parameters for your Synaptics pad, and you can change them using synclient as well, e.g. "synclient touchpadoff=1" turns the touch pad off, "synclient touchpadoff=0" turns it back on.

I have no ideas for power, sorry.

---

### Post by whatthefunk on 2011-10-17
For power, look in /usr/share/applications for a Power Management program.  Its there in 11.04.

---

### Post by Linuxperiment on 2011-10-17
Ok for the mouse settings what I ended up doing is installing gpointing-device-settings. It works but when I restart, it does not work anymore. I'm starting to think it just does what the synclient from terminal does, but I'm not entirely sure. Does anyone know how to make this program run from the start at default and disable tap to click + scrolling?

---

### Post by 2F4U on 2011-10-17
If I remember correctly, in 11.04 XFCE power manager was used. However, there was no menu entry for it. But if you right-click on the battery icon in the task bar and select Preferences, you could configure power management.

---

### Post by Linuxperiment on 2011-10-17
> **2F4U said:**
> If I remember correctly, in 11.04 XFCE power manager was used. However, there was no menu entry for it. But if you right-click on the battery icon in the task bar and select Preferences, you could configure power management.

This works. Thanks!

---

### Post by kalehrl on 2011-10-17
> It works but when I restart, it does not work anymore.

This will make it permanent:

```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```

and at the bottom of the file add:

```
@synclient MaxTapTime=0
```

I'm not sure about the horizontal scrolling but if you find the right command line, just enter it in autostart file.

---

