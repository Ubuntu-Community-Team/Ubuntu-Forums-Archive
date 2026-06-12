---
title: "Laptop crash - black screen!"
date: 2010-03-18
forum: General Help
---

### Post by pingu1 on 2010-03-18
Hi!
My laptop was shut down normally, but when it restarts - it just shows the very first image (Toshiba something....) which is the screen where it says what commands to type to get into bios.

After this - the screen shows nothing more. All black, except some faint (extremely faint) lines... 

I don't know - my first thought was that the screen itself was caput, but since it shows the initial screen - I guess it's not.....

Help?

---

### Post by realzippy on 2010-03-18
Enter the BIOS and see if your harddisc is detected...

---

### Post by pingu1 on 2010-03-18
How do I see if it is detected? That it gives me a boot-sequence which includes HDD?
I don't have the laptop here, because I'm at work, but I will try all the comments I get later today....

I don't think it's a harddriveproblem, but I will check.... thanks.

---

### Post by pingu1 on 2010-03-18
I called and checked - apparantly it does *not *show the screen where it says which button to press to enter Bios. It just shows a screen saying "Toshiba" for maybe 1-second - then all black.

---

### Post by realzippy on 2010-03-18
..connected to power or only battery?

---

### Post by pingu1 on 2010-03-18
Only power. There is no battery in the laptop. I removed it, because it only lasted 20 minutes anyway when fully charged... ... I've run it without battery since... ... ...

---

### Post by pingu1 on 2010-03-18
Now they tell me that the ubuntu-login-sound is there - but no screen.

Tips/advice?

---

### Post by pingu1 on 2010-03-18
Bump

---

### Post by nightwolf2k5 on 2010-03-18
This probably is an issue with your graphics card.

Try the workarounds mentioned in [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

Hope this helps.

---

### Post by pingu1 on 2010-03-18
This site seems to be all problems occuring later in the startup than my problem.
My computer (I guess) doesn't get as far as these... I don't even see "grub loading".... .... ....

I do not understand this, as it should not load any graphicsdrivers this early... ... 
Please correct me if I am wrong...

---

### Post by nightwolf2k5 on 2010-03-18
What happens if you press cntrl+alt+f1 when you get the blank screen (after the ubuntu login sound passes)?

---

### Post by wrose51106 on 2010-03-18
Wondering if the "lightbulb" has burnt out on the backside of the LCD. Hook up a external monitor and give it a whirl.

You might need to use the FN and an F key to toggle.

-Bill

---

### Post by pingu1 on 2010-03-18
I am currently posting from my computer, but using an external monitor....
Works fine on an external. If it works flawlessly on the external monitor - I would guess I can rule out drivers and other softwarecomplications? It's a HW issue?

---

### Post by pingu1 on 2010-03-18
If I go to System - Administration - System Testing,
and then test the monitor - I get following error (I guess it's from Xorg):
> This display is using the following resolution:

ERROR: xrandr -q should return a single line with '*'

Is this acceptable for your display?

---

### Post by pingu1 on 2010-03-18
bump

---

### Post by pingu1 on 2010-03-18
I am now this close <--> to formatting/reinstalling... hope this may help... although I fear it's hardware....

---

### Post by pingu1 on 2010-03-18
Bump
I reinstalled Ubuntu. Same problem. I had to reinstall using the external monitor.
I know fn+F5 is switching between sending the signal out and sending it to the internal monitor,
but the standard monitor does not respond.... ..... ..... 

Help!  I am not ready to give up on it yet... ....

---

### Post by pingu1 on 2010-03-18
I checked my Xorg.conf after reinstalling and it says:
> 
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    3408 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

---

### Post by pingu1 on 2010-03-19
bump, kick, upper-cut

---

### Post by pingu1 on 2010-03-19
Could it be that because I re-installed Ubuntu from the xternal monitor, that it only sets the Xorg.Conf to use this as its only display/monitor?

---

### Post by nightwolf2k5 on 2010-03-19
hmm..as far as i know karmic koala does not come with the "xorg.conf" file.
You could do one of 2 things:
1. Add Driver "vesa" in the device section and restart.
2. Delete the xorg.conf file and restart.

---

### Post by pingu1 on 2010-03-19
I think it's in etc - X11 - Xorg.Conf... .... 

With regards to the things I can do:
Option1:
Do I remove the "device section" that is there now, before adding "vesa",
or do I use the current one? Or can I just add another "device section" in addition to the present one?

2. If i delete Xorg.conf - do I have to unplug the external monitor? Or will it detect my main monitor anyway? (hopefully detect it....)

Thank you.

---

### Post by nightwolf2k5 on 2010-03-19
Actually the xorg.conf file is now obsolete and it not being present in karmic koala is a new feature.

For option 1, add the "vesa" part to your existing  device section.. like mentioned below.

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

2. Let us see it is works without the external monitor. So unplug it for now. (But it should really detect it).

---

### Post by wrose51106 on 2010-03-19
Turn the lights off. and look at the laptop screen. I bet you can see a very faint image on there. The back light sounds like it burnt out.

-Bill

---

### Post by pingu1 on 2010-03-19
I put in Driver "vesa" to my Xorg.Conf - and restarted after turning off all lights...
Yes - you are right, wrose51106, I see a faint white square... It's the bulb/back light....

Thanks everybody. 

Anybody know a rough price for a fix? The laptop is an "older" Toshiba Satellite (M40).

---

### Post by pingu1 on 2010-03-20
bump kick scream :)

---

### Post by pingu1 on 2010-03-20
Anyway - thanks everybody for the help. Much appretiated.

---

### Post by pingu1 on 2010-04-01
I have now been using an external monitor for some weeks without problems (except for the fact that my laptopscreen is black and not functioning at all).

BUT: now I have noticed, to my amazement - that the red/black Ubuntu screen that is shown right before the login-screen is actually "flickering" on for about 1/2 second while I start up the computer with the external monitor on. It seems that the laptopmonitor wakes up for a nanosecond only to die right out again. Anybody understand why this happens? If my "lamp" is out - why would it show the screen (more or less O.K. - but dimmed) once during the startup?

---

### Post by cbecker78 on 2010-04-30
Some of these older Toshiba PCs have a physical push-in switch that is depressed when you close the lid... this switch can usually be set in windows to hybernate, suspend, or turn off the screen.  Whatever the last setting in windows was is usually the setting that Ubuntu uses (in my experience... I have three toshibas).  It is somewhat common for these push-pins to either get stuck in a down/partially-down posistion, or just break.  

IF you have one of these pins, AND it functioned to turn off the screen when you closed the lid-- it's possible it is malfunctioning and causing your problem... try pulling it up with a pair of tweezers, or moving it back and forth a bit to free it if stuck. 

If that's not the case, I don't know.  I know my old satellite 1805 would refuse to show anything on screen past grub BL untill I added "ddm false" or something similar to the xorg.conf... but grub and bios displayed w/o a problem... so that is not likely your issue.

---

### Post by pingu1 on 2010-05-14
Hi cbecker78!
Thank you for the tip. I actually got the screen to work flawlessly 2 days ago. I shut the computer down, closed the lid, and then the next day - BLACK SCREEN AGAIN!
So I guess it might be the problem you are describing. What I can see is that there is only one of the 2 holes that has this "push-in-switch" up when the screen is up. The other hole (on the right) has nothing - just a hole. 

Is there supposed to be 2 of these "push-in-switches" ?

---

### Post by pingu1 on 2010-05-14
Is it possible for the light/backlight to not function for months, and then wake up all of a sudden to work for 2 days, then just die again? Seems strange to me....
If a bulb is broken, it's broken... and will not work again .... ?

---

### Post by cbecker78 on 2010-05-14
There could be a loose connection for the lighting.  I've never taken one of these monitors apart, so not so sure what is going on there.  I'm not sure about the two holes.  I guess wiggling the push pin didn't help?  Could you post the model number of your toshiba?  it should be on the bottom on a silver sticker (most likely).

---

