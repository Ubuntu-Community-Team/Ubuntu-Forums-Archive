---
title: "Dual Monitors"
date: 2009-12-29
forum: General Help
---

### Post by motorcity909 on 2009-12-29
Following the demise of my son's desktop PC (and it's subsequent replacement with a laptop), I've got a spare monitor.  It's the same as the one I'm looking at whilst typing this - a Gateway 19" TFT.

That's connected via VGA but looking at the back of my machine, there is also a DVI connection - as per attached (not my pic, found on web for illustrative purposes).

The monitor also has the same connection which I believe is a DVI-I Dual Link.

If I buy the right cable (a 29 pin male to male), am I right in thinking I'll be able to have dual monitors?

I have heard setting this up in Ubuntu can be tricky...?

Thanks as always.

---

### Post by howefield on 2009-12-30
> **motorcity909 said:**
> If I buy the right cable (a 29 pin male to male), am I right in thinking I'll be able to have dual monitors?

Yes, that would give you the best picture quality, you could also get away with a VGA to DVI adapter and use your existing VGA cable, you might even have one, they often come with monitors or grpahics cards.

As to being tricky, a lot depends on the graphics card you are running ?

---

### Post by motorcity909 on 2009-12-30
I think it can be done as I've got Nvidia X Server Settings under System>Admin, and within that I can select twin-view and autodetect display to find any attached displays.

Seen some YouTube vids of people using those settings to set up a second monitor, so pretty confident it can be done.  Just need to invest that tenner on a cable or adapter.

Out of interest (and without opening the case up), is there a command I can run to tell me what my card is?

Cheers
Dave

---

### Post by howefield on 2009-12-30
> **motorcity909 said:**
> Nvidia X Server Settings under System>Admin, and within that I can select twin-view and autodetect display to find any attached displays.

Pretty much spot on. To save the changes you make using the above, you might need to run the program as admin, ie,  in terminal type

```
gksu nvidia-settings
```

> is there a command I can run to tell me what my card is?

Yes...

```
lspci | grep VGA
```

---

### Post by motorcity909 on 2009-12-30
Thanks again howefield.

The output from that is:

```
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)
```Dual monitors do-able with that card?

Cheers
Dave

---

### Post by howefield on 2009-12-30
> **motorcity909 said:**
> Thanks again howefield.

The output from that is:

```
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)
```Dual monitors do-able with that card?

Absolutely, I'd expect so, it is an older card but does have twin outputs. You should be golden.

---

### Post by motorcity909 on 2009-12-31
Thanks for all your help howefield.

I'll let you know how I get on with this.

Cheers
Dave

---

### Post by motorcity909 on 2010-02-06
Success!  Got a new cable, plugged in the second monitor, changed the settings in Nvidia X Server Settings and there it was, dual monitors!!

Brilliant.  Now I can play around with large wallpapers and lots of screenlets.

Thanks for all the help earlier.

Dave :D

---

### Post by ubuntedo on 2010-03-09
Sorry,
            can you tell me how you have fixed the problem?
I've a Satellite with NVidia FX5200 and Ubuntu 9.10 but my pc doesn't see the LCD connected through S-Video connector

My lspci | grep VGA output is

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

My /etc/X11/xorg.conf is 


Section "Screen"
    Identifier    "Default Screen"
    Option    "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection

---

