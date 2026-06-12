---
title: "Unbale to increase resolution beyond &quot;1024x768&quot;"
date: 2009-07-13
forum: General Help
---

### Post by vimod.c.nair on 2009-07-13
I want to increase my screen resolution beyond "1024x768", but am unable to increase it. I had edited **xorg.conf** and added the **subsection** which was not in the file, but still it doesn't work. This is how I had edited my **xorg.conf** file

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```The subsection part is what I have added after googling around for a solution. My PC uses VIA Chrome 9 for Graphics

Please help me.

One more, Since I am pretty new to Linux I don't know how exactly to change the screen resolution, I mean to say, I used System --> Preferences --> Display to change the screen resolution. Is there any other  or more precise way to change the screen resolution.

---

### Post by ThatBum on 2009-07-13
Do you have an Nvidia card and recent drivers? If so, you might just need to run

```
sudo nvidia-xconfig
```

That should auto configure the xorg file. It worked for me when it wouldn't let me get out of low-graphics mode.

That's mostly all I know, but one more thing, you might need to get newer drivers. The newest ones are 185.18.14. Look around to forum on how to install new drivers.

Thanks for letting me help,

ThatBum

---

### Post by vimod.c.nair on 2009-07-14
Thank You

But, I am not using NVIDIA for graphics, I am using VIA Crome 9.

---

### Post by CatKiller on 2009-07-14
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

