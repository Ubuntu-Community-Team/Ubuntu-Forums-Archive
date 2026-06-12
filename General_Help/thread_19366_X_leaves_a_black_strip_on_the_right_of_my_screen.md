---
title: "X leaves a black strip on the right of my screen"
date: 2005-03-11
forum: General Help
---

### Post by rosslaird on 2005-03-11
I've been experimenting with my X server settings, trying to increase my glxgears frame rate from 50 (!) to what it is now: about 5000. Lots of improvement there. I accomplished this by blacklisting the AGP modules as shown in [this](http://ubuntuforums.org/showthread.php?t=18197&page=3&pp=10)  post. So far so good.

However, I now have a black strip about 3/4 of an inch wide on the right side of my screen during my X sessions. It doesn't cut anything off; it just stops rendering at that point. So my screen size has been shrunk a bit. And the resolution of fonts seems to have suffered -- they don't look as anti-aliased. I didn't change anything in my xorg.conf file (I don't think) to make this happen (I did just now change the refresh rates from 60, because I had this problem before, way back, and changing them to 60 fixed it).

I have a 19 inch LCD display. Here's the relevant bit of my xorg file:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"RenderAccel"		"true"
	Option		"IgnoreDisplayDevices"	"CRT, TV"
	Option		"NvAGP"			"1"
	Option     	"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Samsung 193P (SyncMaster)"
	Option		"DPMS"
	HorizSync	56-75
	VertRefresh	30-81
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Samsung 193P (SyncMaster)"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
	#Mode	0666
#EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
	Option		"RENDER"	"Enable"
EndSection

```

Ideas, anyone?

Thanks.
Ross

---

### Post by rosslaird on 2005-03-11
Well, I seem to have fixed the problem. I changed the default sync rate in Gnome to 60 (this worked before, but it did not work when I changed the xorg.conf file earlier today): System --> Preferences --> Screen Resolution

I thought I'd post the fix in case others have this issue.

---

### Post by Torben Lund on 2006-06-19
I'm a complete newb to Linux and I also have a Samsung 193p monitor.  I also have a 3/4" strip down the RHS of my screen and I can't get rid of it.

With my screen set at a resolution of 1280x1024, I tried tried to set the refresh to 60KHz but the only option was 75KHz.   If I reduce the resolution to a clunky-looking 1024x768, the screen is correctly filled - so it looks as though the refresh rate is the key.

However, after setting my xorg.conf file so that it looked the one in @rosslaird's post (above), I rebooted and found that was still unable to reduce the refresh rate below 75Khz as described by @rosslaird. :confused: 

Can somebody please help out a hapless newb and tell me what I have to do to make 60MHz an option for 1280x1024 in the screen resolution dialogue?

Many thanks
Torben

---

### Post by rosslaird on 2006-06-21
It's been a while, but as I recall, the things to look at are the default depth (make sure that the default, which is usually 24, is set to the resolution you want) and the sync settings. I think you can even try to comment out the sync settings, because X might just use 60 no matter what you put. But I could be a bit hazy on that point.

You can also use "xvidtune".
Fire it up from a terminal, play around with the left/right wider/narrower settings, them copy the modeline that it prints out in the terminal window into your xorg file. Search the forums for "xvidtune" and "modeline".

Good luck.
Ross

By the way, here are the relevant bits of my current xorg.conf for my Samsung monitor under Dapper:

```

Section "Monitor"
    Identifier     "SyncMaster"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1280x1024" 108.0 1280 1372 1484 1688 1024 1025 1028 1066 +hsync +vsync
    Option         "DPMS" "true"
EndSection

```
...
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"

```
...
```

    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection

```

---

### Post by Torben Lund on 2006-06-21
Many thanks for taking time to respond Ross.

I adjusted my xorg.conf per your instructions and I also undid the changes to the Sections "DRI" and "Extensions" that I had copied from your previous post:
As per this code:

```
#Section "DRI"
    #Mode    0666
#EndSection
Section "Extensions"
    Option        "Composite"    "Enable"
    Option        "RENDER"    "Enable"
EndSection
``` 
Which now looks like this:

```

Section "DRI"
   Mode    0666
EndSection
#Section "Extensions"
  #   Option        "Composite"    "Enable"
   # Option        "RENDER"    "Enable"
#EndSection
``` 
I have no idea what these sections were about but as you'd not mentioned them in your latest post, I guessed that they might not be relevant (I'll make a point of looking this up for future reference though).  After I restarted X, I didn't have to tweak or adjust anything - my screen looks perfect!

I really appreciate your help with this - the collaborative support that takes place on Linux forums is amazing compared to my experience as a WIndows admin over the last twelve years - I really like it over here :) 

Very best regards
Torben

---

### Post by rosslaird on 2006-06-21
I'm happy to oblige. And glad you got it worked out. Typically, people will respond on the forums (within a day or two, and often much quicker). The trick is to be specific -- and not to ask, as sometimes happens, why things don't work "like Windows". That's like asking why a motorcycle doesn't work like a tricycle...

The Linux community does tend to be a helpful bunch.

As for xorg.conf, it is a cryptic beast, mostly because of all the video cards and possibilities and attempts to keep up with (and be ahead of) the Mac and Windows Vista. Don't even think about getting into xgl -- at least not yet, unless you want to learn the intricacies of Linux very fast, by trial and error.

The composite and render options handle complex graphics, basically, for video games. Composite also allows for true transparency of desktop windows and other eye candy. But it's quite buggy also. You can use those options if you make sure that the correct modules are loaded:

```

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

```

On my system, the above modules (and no others) work. And there are some other configuration settings too, I think.

But you may not want to start playing around with things now that you've just got everything set up correctly.

Cheers.

Ross

---

### Post by Torben Lund on 2006-06-21
Thanks Ross,

I'm much obliged for the potted tutorial :)  BTW, I swear that until you mentioned it, XGL had not even entered my consciousness! 

I'm going to take your advice and leave the mysteries of xorg.conf well alone until I've got more important things working - but I am so pleased to find that everything is so configurable and I am just itching to see what I can do - based on the maxim "if it ain't broke, you're not trying hard enough"...

Despite feeling as though I'm on one of the steepest learning curves I've yet mounted, this is such great fun after Windows (though I'm not sure my wife would agree :wink: )!

All the best
Torben

---

