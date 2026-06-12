---
title: "Ubuntu doesn't show login prompt?"
date: 2011-08-29
forum: General Help
---

### Post by Livin4Jesus on 2011-08-29
I have Ubuntu 10.04. I left at about 9 PM this morning to an event, and left it in the Arch Linux Live CD (Used Unetbootin). I was gone until about 7 PM or so. When I came back, I restarted so that I could go to Ubuntu. When I started it up, everything seemed fine...until it got to the part where the login prompt is suppose to come up. It just shows the background. I've tried uninstalling and re-installing Nautilus and gdm, (Also tried repairing the packages) and it didn't fix the problem. The only thing I can do is hit the power button on my computer, and Ubuntu will show some options to shut down. I've tried using my Terminal shortcut, didn't work.
Can anyone help me with this? I don't really want to re-install Ubuntu, since I have some important stuff on there...

---

### Post by Wim Sturkenboom on 2011-08-29
Does <ctrl><alt><Fx> work (x being 1..6)? Should get you to a console.

If so, login and run
```

sudo service gdm stop

```
to stop the display manager

and
```

sudo service gdm start

```
to start it again; next <alt><F7> (or sometimes <alt><F8>) to get back to the graphical interface again. If that does not work, stop gdm again and use *_startx_* instead of *_sudo service gdm start_*
```

startx

```
That should definitely get you to the graphical environment.

PS 1
How can you use a terminal shortcut if your not logged in yet; makes sense to me that it does not work.

PS 2
> 
since I have some important stuff on there...
See my signature why I don't believe that it's important. **Make backups**

---

### Post by Livin4Jesus on 2011-08-30
I tried both of your methods, but neither of them worked. However, when I used startx, it the monitor went blank, looking like it was about to boot into the GUI. But instead, it went back to the Terminal and mentioned something about Xorg...

---

### Post by Wim Sturkenboom on 2011-08-30
> **Livin4Jesus said:**
> ... it went back to the Terminal and mentioned something about Xorg...Check the xorg log file (in *_/var/log_*; no Ubuntu at hand to be more specific) for pointers to the problem (search for lines containing *_EE_* first).

---

### Post by Livin4Jesus on 2011-08-30
OK, I found 1 error in two Xorg errors (Both were exactly the same);
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
I don't quite think this has anything to do with the login screen not showing up, because the background is displayed, and I can still move my mouse around...
However, I did find a lot of (WW)s... :confused:

---

### Post by cryptotheslow on 2011-08-30
Do you know if you manually installed an nVidia graphics driver?

Problems like this can occur when a kernel update drops in on your automatic update.

Used to happen to me frequently on 9.x when I had a manually installed nVidia driver, every time I would have to remove and reinstall the driver using the .sh file from the terminal. (I learnt to keep the file handy). Not had that problem in 10.04 using the Proprietary Drivers option within Ubuntu, it just seem to rebuild / refresh them as necessary when a kernel update arrives.

Can you post up the output of:
```
cat /etc/X11/xorg.conf

```

So we can see what's been configured for X.

---

### Post by Livin4Jesus on 2011-08-31
Alright, here's the output:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option         "AllowGLXWithComposite" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "Coolbits" "1"
    Option         "TripleBuffer" "1"
    Option         "DamageEvents" "1"
    Option         "BackingStore" "1"
    Option         "InitialPixmapPlacement" "2"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

