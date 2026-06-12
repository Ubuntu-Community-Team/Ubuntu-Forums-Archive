---
title: "primary monitor designation,  amdcccl seems strange"
date: 2012-07-13
forum: General Help
---

### Post by ortermagic on 2012-07-13
I have set amdcccl, it seems to be working well...however the annoying  thing is that my left screen is designated no2 and the right screen is  no1... I wonder how to change them over to make primary screen show up  on left hand screen. Can anyone help?

See enclosed screenshot attatchment

---

### Post by ortermagic on 2012-07-13
**Has nobody ever had a problem like this?**
have I not explained my difficulty well enough, maybe am I imagining that I have a problem.

---

### Post by Redblade20XX on 2012-07-13
> **ortermagic said:**
> **Has nobody ever had a problem like this?**
have I not explained my difficulty well enough, maybe am I imagining that I have a problem.

Are you talking about one physical screen being split into two, two physical screens being mis-labeled or multiple workspaces being mislabeled?

- Red

---

### Post by ortermagic on 2012-07-13
Hey Redblade, 
I'm talking two separate physical screens, two almost identical LG screens, the lefthand one shows up as 2 and the righthand shows as 1 I would like to know if I can swap them over to make the left one 1 and the right one as two.

---

### Post by QIII on 2012-07-13
I believe the designation is based on which monitor is connected to which port on the card.

It doesn't matter so long as you can, for instance, move the cursor from the left side of your extended desktop to the right without it jumping back to the wrong side of the other monitor.

Swap the cables (or just rearrange the monitors) if you want it to be consistent and go back to CCC and sort out how you want them physically located.

---

### Post by ortermagic on 2012-07-13
> **QIII said:**
> I believe the designation is based on which monitor is connected to which port on the card.

It doesn't matter so long as you can, for instance, move the cursor from the left side of your extended desktop to the right without it jumping back to the wrong side of the other monitor.

Swap the cables (or just rearrange the monitors) if you want it to be consistent and go back to CCC and sort out how you want them physically located.


I seem to remember trying that and it did not make any difference If you don't mind I will attempt that move after I've had a bit of sleep...it's getting late here, so I will swap the plugs over in the morning. Thanks for taking an interest.

---

### Post by QIII on 2012-07-13
If I don't flop on the couch and fall asleep on the couch when I get home from work, I'll mess around a bit tonight with a couple of monitors and see what I get.

---

### Post by Vaphell on 2012-07-13
you may try looking into /etc/X11/xorg.conf

```
Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
**	Option	    "Position" "1920 0"**
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
**	Option	    "Position" "0 0"**
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
[B]	Option	    "Monitor-DFP3" "0-DFP3"
	Option	    "Monitor-DFP4" "0-DFP4"[/B]
	BusID       "PCI:1:0:0"
```


either way my monitors have their IDs switched too but behave correctly. Having said that, amdccle is undoubtedly quirky.

edit: tried to switch, the right one was 1. again. Probably depends which one gets autodetected first or something. Either way it's possible to make the dual monitor setup behave correctly.

---

### Post by QIII on 2012-07-13
On the other hand:

```
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
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection
```

---

### Post by Vaphell on 2012-07-13
my main system is 10.04 and it works when configured in amdcccle as i mentioned earlier. Right now i am testing on 12.04 and it fails horribly - amdcccle crashes badly every 2 clicks and whatnot. What is surprising, the standard display config tool works quite well (it complained about not big enough virtual desktop, but setting Section/Subsection/Virtual to 3200 1200 in xorg.conf made the error go away)

---

### Post by QIII on 2012-07-13
It's been working fine for me since Beta.

How did you install it?

---

### Post by ortermagic on 2012-07-14
Thanks for the input everyone, I swapped the dvi ports over before I started the machine this morning and got one screen which was simply white tho the mouse cursor was able to move across both screens (turning into a cross on the white screen)
 Then I had a look at display mgr to find that it only detected one monitor. 
So I initiated the amdccle app and played around with the settings a bit, then I applied the multi desktop with displays 2 option and found that the display ID had righted itself and 1 was on the left, as I wanted it to be. Oddly, if I apply the 'single desktop display (multi-desktop )option the left monitor assumes number 2. 
At one point I had trouble in with unity only being able to work in 2D mode but somehow, I'm not sure how because I had a visit from a friend (a mac lover) which disturbed my concentration for a couple of hours.
 You are spot on AMDCCLE is **well quirky** and doesn't seem to want to play with Display Manager properly I took one or two screen-shots along the way.
I tried to install using the driver from the amd download site (ati-driver -installer-93-86.x86_64) however It did not want to install (took about an hour then informed me it had failed) tried that twice. In the end I set it up using synaptic.

---

### Post by ortermagic on 2012-07-14
Nice mountain wallpaper mate

---

### Post by ortermagic on 2012-07-14
I've just got round to paying attention to the xorg.conf question  sorry I'm all over the place today. Looks like I have a more lengthy File here compared to the others shown perhaps bloat has something to do with the problem that I have?

I still have problems with single display multi-desktop when I apply it I only get one screen working, with a blank white screen on my LHS monitor 
I'm still learning, please forgive my ineptitude.

[B]

Heres my copy of xorg.conf

[/B]Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP7"
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
    Identifier   "0-DFP6"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP7" "0-DFP7"
    Option        "Monitor-DFP6" "0-DFP6"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP7" "0-DFP7"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by QIII on 2012-07-14
> **ortermagic said:**
> Nice mountain wallpaper mate

Thanks.   A stock panoramic photo I got off the web somewhere.  I don't know where it is.

There's a sharp line down the middle because I corrected for the bezels.  Because there is a gradient in the color of the sky from left to right it makes the screen shot look like the color values on the monitors change right there.  Oh, well.

The example I showed was in Xubuntu Precise, which may be why things look OK for me.  The only Ubuntu I have installed right now is Quantal, so I haven't installed fglrx yet.  There is a patch to allow installation, but I'm testing a stock installation right now.  The closed source fglrx driver usually hits the repo in the final Beta or the RC.

Anyway, it could be a quirk in how fglrx and the display manager are communicating in Ubuntu.

(BTW, our xorg.confs are probably about as long as yours.  Those were just sections.)

---

### Post by ortermagic on 2012-07-14
> **QIII said:**
> Thanks.   A stock panoramic photo I got off the web somewhere.  I don't know where it is.

There's a sharp line down the middle because I corrected for the bezels.  Because there is a gradient in the color of the sky from left to right it makes the screen shot look like the color values on the monitors change right there.  Oh, well.

The example I showed was in Xubuntu Precise, which may be why things look OK for me.  The only Ubuntu I have installed right now is Quantal, so I haven't installed fglrx yet.  There is a patch to allow installation, but I'm testing a stock installation right now.  The closed source fglrx driver usually hits the repo in the final Beta or the RC.

Anyway, it could be a quirk in how fglrx and the display manager are communicating in Ubuntu.


Thank you for clearing up re: 
(BTW, our xorg.confs are probably about as long as yours.  Those were just sections.)

I ended up removing all Xconf files and lostfunctionality so i'm back to square one and am replying to you on a newly installed, virgin, copy of 12.04 os.

 In the end I had messed around with the AMD driver so much that it would not even shut down...Whenever I needed to restart I got a screenful of cryptic coding which stuck and would not resolve, so I had to force a power off each time. 
Not only that but I found that the amdcccle driver caused my ubuntu startup splash to come out with just basic font, fglrx is definitely quirky (Red)
I had all this trouble before, two months ago when I tried it. I will not be using the additional drivers again till I know for sure it works.
About the panoramic, funnily enough I googled panoramic desktop images and saw one of your other posts I like the idea of a competition But i'm too embroiled in **stuff** to take part right now.

---

### Post by ortermagic on 2012-07-16
Well!  for anyone interested, I managed to get a desktop image to span across both screens using the onboard graphics driver I don't think I will trouble myself with the enigma of amdcccle any more. Although the image file is pretty heavy on resources, something I will try to rectify later.
 I love Ubuntu!

---

### Post by SteveHillier on 2012-08-14
ortermagic,
I was having this same problem.  Other details an issue but...
I was using Catalyst Centre to position my screens.  It was placing screen 1 to the right of screen 2.  Ok I could have physically moved the monitors but hey, the software should reflect reality.  
After several attempts I looked at settings->displays and found that the screens were the wrong way round here.  I swapped them and the when I rebooted Catalyst Centre had them the right way round.

---

### Post by SteveHillier on 2012-08-14
Other issues,
I am fast coming to the conculsion that Catalyst Control Centre is just not up to the job.
Two monitors I am Ok with on the system I am using at this moment but the new system I want to build I want with 4 monitors.
Whilst I have the screens the right way round I cannot move smoothly from screen 1 to screen 2.   The cursor seems bounded on all edges of screen 1 and then suddenly it will jump across to screen 2 where it appears bounded on all 4 edges
I will probably start a new thread to cover the issues I have found

---

### Post by SteveHillier on 2012-08-19
As promised I started a new thread and now have 4 monitors working on a single system

Have a look [here]("http://ubuntuforums.org/showthread.php?t=2042265")

---

