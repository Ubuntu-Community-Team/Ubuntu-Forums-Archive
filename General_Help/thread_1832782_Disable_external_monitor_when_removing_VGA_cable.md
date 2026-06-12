---
title: "Disable external monitor when removing VGA cable"
date: 2011-08-25
forum: General Help
---

### Post by Brucevdk on 2011-08-25
I have a dual monitor setup (laptop screen + external monitor) and have configured the GNOME panel to appear on the external monitor by default. When the external monitor is disabled through the monitor setup configuration applet (gnome-display-properties) the panel appears on the laptop screen. 

However, the same doesn't happen when you unplug/remove the VGA cable for the external monitor.

Is there any way for Ubuntu to detect that the external monitor cable has been disconnected, automatically disable the screen and hence have the panel appear on the laptop screen instead? 

Thanks in advance.

---

### Post by realzippy on 2011-08-25
..you could delete the monitors.xml file
(which gets created when running the monitors GUI again).

```
rm ~/.config/monitors.xml
```

---

