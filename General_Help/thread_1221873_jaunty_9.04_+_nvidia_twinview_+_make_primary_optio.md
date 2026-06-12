---
title: "jaunty 9.04 + nvidia twinview + make primary option"
date: 2009-07-24
forum: General Help
---

### Post by utannheim on 2009-07-24
I'm using the NVIDIA accelerated graphics driver (version 180) which was recommended. When I'm in the office I use twinview to extend my desktop from the laptop to my LCD monitor. (My graphics card is a Quadro FX 570M)

When I use the NVIDIA X Server Settings tool to extend the desktop, it appears like the option "Make this the primary display for the X screen" is ignored. Instead the primary becomes the Display last modified. Even if I apply the settings and re open the tool and make the appropriate screen primary, the setting is still not applied. The only way to make a screen primary is to change the resolution on the laptop display.

So I guess I have 2 questions - 
1. does the make primary option work (it used to in 8.10)
2. if I use a separate X screen, how can I transfer an app from one display to the other? Can it only be done via the command line? Is there any panel applet of other extension that will allow me to do it with the mouse (quickly)? 

Thanks in advance.

---

### Post by SteveDee on 2009-07-24
> **utannheim said:**
> I'm using the NVIDIA accelerated graphics driver (version 180) which was recommended. When I'm in the office I use twinview to extend my desktop from the laptop to my LCD monitor. (My graphics card is a Quadro FX 570M)

When I use the NVIDIA X Server Settings tool to extend the desktop...

...So I guess I have 2 questions - 
1. does the make primary option work (it used to in 8.10)
2. if I use a separate X screen, how can I transfer an app from one display to the other? Can it only be done via the command line? Is there any panel applet of other extension that will allow me to do it with the mouse (quickly)? 

Thanks in advance.

I've had problems with this tool recently where I tried to switch from TwinView back to Separate X Screen. I ended up with the TV as screen0 and had to edit xorg.conf to put it right.

As this is on a computer in our lounge used sometimes as a pc, sometimes to play videos, I decided to make a simple GUI app (in Gambas) to reliably switch between Single, Twin & SepX. I first got each of the 3 configs working reliably and saved each xorg.conf as xorg.conf.single, ...twin & ...sepX. Now I just copy the required version back as xorg.conf and re-boot using my Gambas app. Works reliably every time.

The same thing could be achieved without a GUI app by creating 3 launchers.

When using computer in Separate X Screen mode, I run videos on the 2nd screen (TV) by launching with a command like:-
mplayer {filePathName} -fs -display=:0.1
...actually I run a nautilus script and just have to right click on the movie file and select the script.

For normal computer work (where you want to move an app temporarily to the 2nd screen you are better off with TwinView. But if running videos on a TV its better to use Separate X.

I hope this helps.

---

