---
title: "Squares instead of text"
date: 2010-06-21
forum: General Help
---

### Post by davidogg on 2010-06-21
Installed 10.04, getting squares instead of text in certain places.

Sorry for the sixe of the pic. Any ideas?

Edit bodhi.zazen: Please do not post such large screenshots. Either post a part of the screen or use thumbnails.
[IMG]http://yourspiff.com/iboards/amiga/b/src/127715065191.png[/IMG]

---

### Post by doas777 on 2010-06-21
have you changed your fonds recently?

---

### Post by Smart Viking on 2010-06-21
Yes, you could try to change the font the system uses, i don't remember how to do that in gnome, but you will probably find it pretty easily. :)

---

### Post by John Harris on 2010-06-21
I had the smae problem, i cant remember exactly what resolved it im afraid, i know there were alot of system restarts involved (always puts my mind at ease). If you go to the ubuntu software centre and remove the 'installer for microsoft truetype core fonts' if its installed, restart your machine and install it again, your problem should be sorted (i hope) good luck :)

---

### Post by davidogg on 2010-06-21
Haven't messed with fonts, but for giggles and kicks I changed them and back to default again, still have the squares. It's really wierd because they are kind of random, and in places where they are working, some lines will be squares, even though they should be using the same font as the lines around it... like here in the Main Menu prefs

 Edit bodhi.zazen: Please do not post such large screenshots. Either post  a part of the screen or use thumbnails.

---

### Post by eriktheblu on 2010-06-21
> **davidogg said:**
> Sorry for the sixe of the pic. Any ideasResize in F-Spot.

As for the fonts, I'd try to reinstall the font packages.

---

### Post by bodhi.zazen on 2010-06-21
Did you change fonts ?

Tell us more about your installation, is this a minimal install ?

Are you using or did you enable apparmor ?

---

### Post by davidogg on 2010-06-21
> **bodhi.zazen said:**
> Did you change fonts ?

Tell us more about your installation, is this a minimal install ?

Are you using or did you enable apparmor ?

Haven't changed any fonts from default. regular install with a few extra packages added for ms codecs. Haven't touched apparmor, unless it's enabled by default. Enabled compiz. Installed debian grub graphics. pretty much stock.

That Debian icon in my main menu prefs... is that kosher, or possbly something inadvertantly installed with the debian graphics? 

Reinstalling fonts now

---

### Post by bodhi.zazen on 2010-06-21
How did you install the msfonts ?

Do you have a custom /etc/X11/xorg.conf ?

Usually one sees blocks in place of text when there is a problem with fonts, either the path is off (set in xorg.conf) or apparmor is blocking access or the fonts have been altered in some way.

---

### Post by davidogg on 2010-06-21
> **bodhi.zazen said:**
> How did you install the msfonts ?

Do you have a custom /etc/X11/xorg.conf ?

Usually one sees blocks in place of text when there is a problem with fonts, either the path is off (set in xorg.conf) or apparmor is blocking access or the fonts have been altered in some way.

"ttf-mscorefonts-installer" in Software Center. That's removed now, since the fonts are default anyway.

/etc/X11/xorg.conf ;
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

does that seem a bit sparse?

the only font's I'm using are the default sans-10, sans bold-10, and monospace-10, I reinstalled the package "ttf-freefont" but still have squares.

---

### Post by davidogg on 2010-06-21
Hmm, I did a sudo fc-cache -fv and everything is normal now.

Thanks guys for the help!

---

