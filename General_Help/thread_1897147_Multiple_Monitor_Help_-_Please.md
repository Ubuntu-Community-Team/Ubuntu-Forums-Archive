---
title: "Multiple Monitor Help - Please"
date: 2011-12-18
forum: General Help
---

### Post by ThePhysician on 2011-12-18
I'm running an (ATI) XFX HD 5870, and trying to use Gnome 3 because Unity is abysmal for triple monitor support... and just about everything else but that's irrelevant. 

Well when trying to set my left and right monitors to not be mirrors of the middle one I get this ridiculous error:

"required virtual size does not fit available size: requested=(5760, 1080), minimum=(320, 200), maximum=(1920, 1920)"

All my monitors are the same size and model.

What display environment or whatever you guys call it best supports 3 monitors with ATI?

Is there any way to bring back 3 monitor support in Gnome 3? If not, is there a way I can get to legit Gnome 2? If I use Gnome 3 as "classic" it still is actually Gnome 3 just acting like 2 and still won't let me use my monitors.

Should I try Kubuntu? Xubuntu? Any idea how I can get an x whatever that let's me max windows (like Linux games or games in Wine) across all 3 screens?

---

### Post by Synoc on 2011-12-18
it SOUNDS like it's thinks you have one montior and want three times the width than is possible on one... I unfortunately have only gnome 2 and may not be able to help you set it up. if the file exists on your computer it make help to give us the output of 
```
 cat /etc/X11/xorg.conf
```
this will let us (maybe) see what your computer is looking at. however this file seems to be disuse in many cases and thus sometimes is not even there, or not looked at when it is...  but it is a jumping off point, perhaps.

---

### Post by ThePhysician on 2011-12-18
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

```

I installed Catalyst Control Center in the Software Center, and if I set any of the options to use more than one monitor and click apply, instead of giving me an error message there it just doesn't do it. Unless I click to just mirror all the displays the same, which makes the other 2 a waste of electricity, lol.

I think Gnome 3 and Unity are very very very much coded in a way that tries to restrict use to one monitor. =(

And sadly, from what I've read there's no way to get back to 2 without installing an older version of Ubuntu?

---

### Post by QIII on 2011-12-18
Are you using the Catalyst driver?  If so, when you set up your monitors, it should generate an xorg.conf, even though it there is none by default.

I have a machine that runs two monitors from an XFX 5870.  They are slightly different resolutions, and you are running three monitors, but this should help.  I'm also running KDE.

At the bottom, look at the virtual screen resolution.  You should be able to adjust that accordingly.

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "61"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "0-DFP3"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3600 1920
        Depth     24
    EndSubSection
EndSection


```

---

### Post by Synoc on 2011-12-18
if I am not mistaken the "0 0" value for position is where it starts on the X Y axis? so you might want to check and make sure those are start running successively.

---

### Post by ThePhysician on 2011-12-18
Well after switching to the proprietary one in "Additional Drivers" I lost the ability to use multiple monitors even when in Unity. And when clicking "remove" it looks like I still can't use the other ones.

Where are the drivers you'd suggest using?

Also, no idea where the xorg.conf is. Searching for it in Unity under search for files and folders just takes me to a website error result. Thaaanks a lot Unity, lol.

---

### Post by Synoc on 2011-12-18
> **ThePhysician said:**
> Well after switching to the proprietary one in "Additional Drivers" I lost the ability to use multiple monitors even when in Unity. And when clicking "remove" it looks like I still can't use the other ones.

Where are the drivers you'd suggest using?

Also, no idea where the xorg.conf is. Searching for it in Unity under search for files and folders just takes me to a website error result. Thaaanks a lot Unity, lol.

ctrl+alt+T will give you a terminal the code I posted will display the contents of that file to the screen, highlight, copy and paste it here. /etc/X11/xorg.conf is the path to the file and file name inside that directory. IF it exists. I do not have a PC with an ATI card to see what drivers are there to be used. 

if you are afraid of the terminal (I used to be) you can open up your file browser (nautilus) and start at File System>etc>X11 and look for a file called xorg.conf. IT MAY NOT BE THERE. if so tell is that. if it is, double click on it it should bring it up in your default text editor (gedit most likely) copy and paste the contents here. 

WHEN PASTING: highlight the pasted text and click on the "#" button. that will post the EXACT text as it was written.

---

### Post by QIII on 2011-12-18
AMD and Ubuntu have had a fling going on for several years.  The latest  AMD Catalyst driver is made available in the Ubuntu repository just as  the new Ubuntu version is released.  So 11.10 will have the most recent  one as of the release date.

Since I disliked Unity from the get-go because of its lack of configurability and GNOME shell because it seemed to me to be a rushed (and quite flawed) effort, I installed the Kubuntu spin this time around.  I've always liked GNOME over KDE, but that was a personal choice rather than one borne of a really strict comparison.

KDE is simply different, so I don't bother even listening to "KDE is better or GNOME is better."  Well, until now.

This is purely my opinion, but I would say that Unity is a POS and a grave error on Canonical's part.  GNOME shell is not ready for prime time.

So, all of that is to say that what I have done works on a machine with the KDE desktop environment.  If it is not working in Unity or GNOME shell, this may be an issue.  I was not aware that it might be.

---

### Post by ThePhysician on 2011-12-18
Okay. I got KDE booted up and 3 monitors working fairly well. Just fairly.

My only question is do you have bezel compensation with Catalyst Control Center? Or is there any way to say.. set KDE so it thinks I have one big monitor and not 3 separate ones? You know, one wallpaper/game/whatever spanning all 3?

Apparently their love affair is not enough to get full Eyefinity over here? Lol

---

### Post by QIII on 2011-12-18
Eyefinity will eventually come.  It is something that has been more  effort to port to Linux than they thought.  Hey.  They know the world is  mostly Windows and they have a business to run -- they need to make a  profit.

I don't game, so I've never worried about bezel correction.  Unfortunately, I can't help you there.

But I can say that my screen spans both monitors.

Under "Display Manager", select the "Multi-Display" tab and select "Multi-Display desktop with display(s) x" where x should be the number of monitors you have.

It works the same way if I boot the machine to Fedora with KDE.

---

### Post by ThePhysician on 2011-12-18
Hm, I don't know what's going on with mine. I think I have the same card as you, the XFX HD 5870.

In KDE I tried to install the catalyst control center and proprietary driver, and then it had me restart and now in KDE I can't open any windows besides right clicking and changing the wallpaper. If I right click and try to add the bottom panel back KDE crashes. If I try to do about anything KDE keeps crashing.

Is KDE Plasma the same that will come in Kubuntu? KDE was certainly the closest I've gotten to everything working, would it be a better bet just to install all of Kubuntu instead of KDE on Ubuntu, or would there be no difference then?

---

### Post by QIII on 2011-12-18
Reboot to rescue mode.  There is a bit of a wrinkle in installing the AMD/ATI drivers.  My bad for not forewarning you.

Get to a command prompt and type 

```
sudo aticonfig --initial
```

Reboot normally and tell me what you get.

---

