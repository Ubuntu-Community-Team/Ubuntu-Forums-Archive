---
title: "Many applications open on second screen"
date: 2009-11-13
forum: General Help
---

### Post by scotty64 on 2009-11-13
I have moved to KDE as Desktop environment. I notice that several applications (Firefox, Thunderbird, Qsynth,...) always open on my second monitor so I have to drag their window to my big screen in order to use them there. KDE does not seem to store the window location, because when I restart an application the same thing happens.
My configuration:
Dell XPS M1330 Laptop with NVIDIA graphics chip and NVIDIA driver installed.
The external LCD is configured as the primary display with the laptops LCD as second screen. The laptop sits on the right hand side of the external LCD.
KDEs "Multiple Monitor Support" settings list the monitors in the correct order. I have tried both settings ("Display 1" and "Display containing the pointer") for "Show unmanaged windows", but it does not help.

---

### Post by Giblet5 on 2009-11-13
How are the monitor's configured for Xorg?

Twinview, or separate X screens?

I'm guessing Twinview by the description. I have never had much luck at getting new windows to map on a specific monitor in twinview mode (basically one large logical screen). This is because the window managers either forget the configured fixed geometries for a given window class, or because they're running into some other overriding constraint. I haven't researched it to determine which because I use separate X screens.

You can force apps to a fixed position using geometry statements of the form: ```
firefox -geometry +1600+100&
```

For details, see ```
man X
```

Using separate screens, it is possible to reliably start applications on a specific monitor. Example:
```
thunderbird -display :0.0&
firefox -display 0.1&
``` will pop up tbird on screen 0 and firefox on screen 1 every time.

I do that here: a 23" 1920x1200 lcd to the side and a 30" 2560x1600 main, both hanging off of an nvidia 280 GTX card. It takes getting used to, but it works well and its behavior is completely predictable.

You can enable separate X screens via ```
sudo nvidia-settings
```

Save the X config, then restart X via ```
sudo /etc/init.d/gdm restart
```

Use those same two steps to revert to twinview if the separate screens is not what you need.

---

