---
title: "xorg.conf, change default resolution"
date: 2010-10-03
forum: General Help
---

### Post by cgroza on 2010-10-03
Hello, at startup my resolution is set to 1024x768 but i want it to 1152x864. I tried a tutorial about editing the xorg conf file but it didnt worked. The tool that comes with ubuntu doesn't shows a higher resolution that that and nvidia-settings can not save the file.
Here is my xorg file. Thank you.

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"

       SubSection "Display"
          Depth        16
          Modes      "1152x864_85.00"
       EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by wojox on 2010-10-03
Run these two commands in the terminal

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by papibe on 2010-10-03
If you're able to set the resolution you want using System -> Administration -> NVIDIA X Server Settings, you can save those settings to your xorg.conf.

Go to X Server Display Configuration (on the left), and then on the right click save to X Configuration file.

Good Luck!

---

### Post by cgroza on 2010-10-04
> **papibe said:**
> If you're able to set the resolution you want using System -> Administration -> NVIDIA X Server Settings, you can save those settings to your xorg.conf.

Go to X Server Display Configuration (on the left), and then on the right click save to X Configuration file.

Good Luck!

It says it can not parse the file and then it gives me an window with the path to xorg in it and if I click save it says "cannot open xorg.conf for writing." I tried a trick a few minutes ago and I will give you the feedback after I reboot.

---

### Post by papibe on 2010-10-04
> ...it says "cannot open xorg.conf for writing."
probably because you weren't root at the moment. Save it on your home directory and then move it to /etc/X11.

Don't forget to backup the one you have right now (just in case).

Regards.

---

### Post by cgroza on 2010-10-04
Sure , thanks.

---

