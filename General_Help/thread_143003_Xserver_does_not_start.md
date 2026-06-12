---
title: "Xserver does not start"
date: 2006-03-11
forum: General Help
---

### Post by Bishop Hill on 2006-03-11
I'm having a really stupid problem, and this really annoys me.

The problem, without any further ado is:

I'm having troubles with the Xserver (GUI, HUD or whatever it is in english). Since Ubuntu's in-build drivers does not support ATi-graphics cards (or at least not mine), I dont get a desktop when I boot, I get nothing exept the terminal (just a black screen and white letters). One of my friends, whose brother is the 1337est Linuxuser I have ever seen, managed to fix this by setting some kind of default-drivers (i did'nt get the highest resolution ever, but it was'nt bad).

And since that guy is away (also, I need to be able to fix this myself), I thought I'll ask here for any help on how to fix this.

Please help me, I know you guys can to it :)
/Daniel

---

### Post by magnusbb on 2006-03-11
Have a look at this thread:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by Bishop Hill on 2006-03-11
Thanks dude. Not exactly what I'm looking for, but I'll try to try this:)

---

### Post by audax321 on 2006-03-11
[QUOTE=Bishop Hill]One of my friends, whose brother is the 1337est Linuxuser I have ever seen, managed to fix this by setting some kind of default-drivers (i did'nt get the highest resolution ever, but it was'nt bad).
[/QUOTE]

Chances are he editted the /etc/X11/xorg.conf file and changed the driver to "vesa". It's done by finding the Section "Device" in the file and changing the value of the Driver line. The way you edit a text file in a terminal is by using a program called nano ( nano <filename> ). But since you need root permissions to edit the xorg.conf file you'd use sudo: 

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by tay on 2006-03-11
I have the same problem.  Xserver wont' start on my Toshiba Satellite L20 / L25 series w/ ATI Radeon Xpress 200M graphics card.  

I did'nt see that mentioned in the last link as supported or not with that diy.

Since I only have a live cd I will have to wait for my new breezy install cd's, to try editing xconfig from the command line.

---

### Post by Bishop Hill on 2006-03-11
[QUOTE=audax321]Chances are he editted the /etc/X11/xorg.conf file and changed the driver to "vesa". It's done by finding the Section "Device" in the file and changing the value of the Driver line. The way you edit a text file in a terminal is by using a program called nano ( nano <filename> ). But since you need root permissions to edit the xorg.conf file you'd use sudo: 

```
sudo nano /etc/X11/xorg.conf
```[/QUOTE]

So its not harder then that one commandline?

BTW, yes, now that you mention it, thats how he did it.

---

### Post by audax321 on 2006-03-11
Also, about the problem with the resolution. There is a section that looks something like this in the file:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768"
        EndSubSection
EndSection

```

It is basically the resolutions supported for the different color depths. Of course, you'd probably use 24 as default.. but after the Modes lines you can list the resolutions. My laptop uses "1280x768" (the highest possible for it's display). You can change these to what ever resolution you want, or even list resolutions like: "1024x768" "800x600" "640x480" and so on. I believe X will default to the first listed resolution.

The other important section is the Monitor section:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection

```

The HorizSync and VertRefresh settings can normally be found for your specific monitor using Google or in the Manual (under Specifications, etc.) Changing these to suit your particular monitor will give you a better refresh rate. Just be careful not to change them to something unsupported, because you can damage your monitor.

Hope that helps. The xorg.conf file is probably the most problematic for people when installing Linux. I know when I first tried SuSE and it didn't work with my old laptop I uninstalled and went straight back to Windows. Knowing what I know now, all I needed to do was a simple edit of the xorg.conf file.

---

### Post by Bishop Hill on 2006-03-17
Can someone tell me exaclt how I edit the xorg.conf? When I open it it nano, theres no text anywere:(

---

### Post by AndrewCaul on 2006-03-17
[QUOTE=Bishop Hill]Can someone tell me exaclt how I edit the xorg.conf? When I open it it nano, theres no text anywere:([/QUOTE]
Did you enter the filename correctly?

---

### Post by Bishop Hill on 2006-03-17
[QUOTE=AndrewCaul]Did you enter the filename correctly?[/QUOTE]

Nope. I wrote it with a non-capital X, so it got f*cked. But now I'm happily surfing using Ubuntu:D

---

