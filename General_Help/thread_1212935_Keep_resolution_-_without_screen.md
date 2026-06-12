---
title: "Keep resolution - without screen"
date: 2009-07-14
forum: General Help
---

### Post by YigalB on 2009-07-14
I use my Ubuntu as a stand alone machine - with no screen attached. I connect and control it through VNC.

Yesterday I installed 9.04 and everything was OK - I could control the reolsution of the screen, etc.
Once I took out the VGA cable of the screen, 
and restarted it - it gave  me maximum of 600*800.
If I connected the VGA cable and restart - I get again many oprions for resolutions. 
What can I do in order to keep the resolutions I like, regardless if a screen is attached or not?

Thanks

---

### Post by Wim Sturkenboom on 2009-07-14
Modify xorg.conf.

Add the monitor refresh rates (lookup the specs of your monitor in the manual).
Add the required modes.
Optionally you might have to use something like *useedid false*.

Example of aprt of my xorg.conf below.

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       27.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver         "nvidia"
    Option         "UseEdidFreqs" "False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1050" "1440x900" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

notes
In your case it might have to be *useedid* instead of *usededidfreqs*
Only specify modes that you want to use

---

### Post by YigalB on 2009-07-14
I am not sure I understand.
I want the VGA card to provide all resolutions it can regardless if a physical screen exists or not.
Of course - if a screen is connected, the card should offer only resolutions that the screen can handle. This is working OK.
But in my case - no screen is attached, so no limit should be applied from the VGA card point of view, since I use VNC to view.

---

### Post by CatKiller on 2009-07-14
> **YigalB said:**
> I am not sure I understand.
I want the VGA card to provide all resolutions it can regardless if a physical screen exists or not.
Of course - if a screen is connected, the card should offer only resolutions that the screen can handle. This is working OK.
But in my case - no screen is attached, so no limit should be applied from the VGA card point of view, since I use VNC to view.

They are the same thing. With no screen attached, X cannot acquire the EDID information that lets it automatically set the resolution. Rather than risk damaging a monitor, it defaults to really low refresh rates, which means really low resolution.

The solution suggested is to tell X to ignore the (lack of) EDID information and instead use the values that you've given it. Since X is starting up with the correct resolutions when the monitor is plugged in, you can probably get the values you need from X's log at /var/log/Xorg.0.log from a successful start up. Otherwise, the monitor documentation should have it in.

---

### Post by Wim Sturkenboom on 2009-07-14
The above configuration should use the highest reolution that you have specified by default. And it will do that ALWAYS as it will ignore any connected monitors. So if you connect the monitor and it does not support the resolution, you will get an out-of-range message and you can cycle through resolutions with <ctrl><alt><+> and <ctrl><alt><->.

The problem is that if you don't connect a monitor, the system thinks that there might be an old monitor (as those don't inform the system about their capabilities) that does not support anything above 800x600 and therefore uses a safe assumption (800x600). So you have to specify everything so X can tell the driver what it can use.

Sorry if that's not what you want and I don't know how to achieve it.

---

