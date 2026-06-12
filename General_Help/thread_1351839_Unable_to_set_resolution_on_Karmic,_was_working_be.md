---
title: "Unable to set resolution on Karmic, was working before reinstall"
date: 2009-12-10
forum: General Help
---

### Post by jaon on 2009-12-10
I wrote up a whole story explaining my situation, but thought it too long, so I'll just give you the gist of my problem:

[LIST]
[*]I've had a stable Ubuntu install that's been upgraded each new release from 8.04 and was on 9.10 happily for a few weeks.  My system has a Radeon X1950 Pro graphics card and I had been using the flgrx drivers.
[*]Yesterday my Xorg settings were apparently corrupted, and despite all my trying I couldn't get them working again, at least not at the correct resolution.
[*]It turns out AMD has dropped support for my card (Raedon X1950 Pro) in the latest flgrx drivers.  The old drivers aren't compatible with Karmic.  By the time I realised this I'd caused so many problems (even downgrading xorg!) that I figured it was easiest to reinstall Ubuntu.
[*]I've installed Ubuntu 9.10 fresh, am not using propietry ATI drivers, and still can't set my resolution correctly.
[*]When I open "Display Preferences", there are no displays to select, and so no resolutions or display properties I can change.
[*]When I open "Hardware Drivers" it doesn't detect anything, so I can't even attempt to install the proprietry ATI drivers.
[/LIST]

I'm happy to use the Open Source drivers, they provide enough acceleration to enable desktop effects and that's all I need.  But, I still can't set the resolution correctly (or at all), and my screen looks pretty ugly.

So it's a new Karmic install, no special drivers installed, and can't change anything.  Was working on my previous upgraded-to-karmic-over-the-years system until yesterday morning.

Any suggestions?  Need me to post any more details about my hardware/software/what i've tried so far?

I'd appreciate the help, I want my 'aesthetically pleasing' desktop back :P

Thanks
Jason

---

### Post by lidex on 2009-12-11
OK. I'm posting the links to some threads that may help. 
[http://ubuntuforums.org/showthread.php?t=1309925]("http://ubuntuforums.org/showthread.php?t=1309925")
[http://ubuntuforums.org/showthread.php?t=1156406]("http://ubuntuforums.org/showthread.php?t=1156406")
[http://ubuntuforums.org/showthread.php?t=1328290]("http://ubuntuforums.org/showthread.php?t=1328290")

---

### Post by jaon on 2009-12-11
Thanks Lidex.  Your posts got me onto a few things and indirectly let me figure it out eventually.

Just a warning for anyone else who tries... 'envyng' let me install ATI drivers, **EVEN THOUGH they weren't compatible with my card**, leading to my computer restarting by itself a few times.  Whoops :)

Anyway, the result of that was that when it recovered it gave me an Xorg.conf file to fiddle with, rather than autodetecting each time.  With some tweaking based on [this article]("https://help.ubuntu.com/community/RadeonDriver"), I came up with this xorg.conf file, which is working for me.

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection


Section "Device"
	Identifier	"Builtin Default ati Device 0"
	Driver	"ati"
EndSection

Section "Screen"
	Identifier	"Builtin Default ati Screen 0"
	Device		"Builtin Default ati Device 0"
        Monitor         "Generic Monitor"
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Builtin Default Layout"
	Screen		"Builtin Default ati Screen 0"
EndSection

```

Changing the section in "Display" let me change my resolution manually.  Still can't see anything in "Display Preferences" in gnome though :)

And I was just getting used to squished blurry fonts.  Having the resolution at its native seems... too clean :P

---

