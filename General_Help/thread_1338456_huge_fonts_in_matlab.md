---
title: "huge fonts in matlab"
date: 2009-11-26
forum: General Help
---

### Post by hanlin on 2009-11-26
I have matlab installed on my laptop which has a 1400x1050 screen. I also have a dock for the laptop connected to a 2048x1152 monitor. When I'm running matlab on the big monitor, everything's normal, but if I'm on the laptop only, the fonts in matlab are huge. The menus are normal sized but the area where you type has huge fonts. Now this doesn't happen if I have matlab open while undocking. In that case, the font looks normal. Only when matlab is opened while in laptop mode does it happen. 

I'm running Karmic x64. I have a feeling it has to do with java, since both matlab and maple (another program that has the same issue) run on java, and both have the exact same issues. Any ideas what's causing the problems?

---

### Post by solar george on 2009-11-26
Do you have a nvidia graphics card? If so try editing you /etc/X11/xorg.conf to include;
```
        Option  "UseEdidDpi" "false"
        Option  "DPI" "96 x 96"

```
In the device section, e.g my xorg.conf is;
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "UseEdidDpi" "false"
        Option  "DPI" "96 x 96"
EndSection

```

---

### Post by hanlin on 2009-11-26
No. I have the Intel X3100. Will something like that work for my card?

---

### Post by solar george on 2009-11-26
> No. I have the Intel X3100. Will something like that work for my card?

You probably don't anything in xorg.conf then, have you set the dpi (to 96) in System Settings> Apearance> Fonts ?

---

### Post by hanlin on 2009-11-26
Yes, it's set to 96dpi there. I don't have a xorg.conf file. I also did some looking around online and noticed that:

xdpyinfo | grep resolution

produces 145x145 instead of 96x96. It suggested putting 'Xft.dpi: 96' into ~/.Xdefaults or ./Xresources but neither one does anything. Where should it be put? And is there a way to run it manually?

---

### Post by solar george on 2009-11-26
hmm have you tried restarting after making those changes?

---

### Post by hanlin on 2009-11-26
Yes. Nothing changed. For now, I have found that changing the screen resolution and then back fixes the issue. I guess I'll have to do this from now on until a better fix comes along.

---

