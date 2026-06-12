---
title: "2d artifacts (BFG Nvidia 8800 GTX)"
date: 2010-09-21
forum: General Help
---

### Post by Furiam on 2010-09-21
Hi all.

I'm having artifact problems as shown in the screenshots. These start to happen after a video has been watched, or a game played... but sometimes after 2 minutes, or 2 days, or 2 weeks (Computer never goes off). The fix for this is to switch to console and restart GDM, or log off / log in.

My graphics card is : 
Nvidia 8800 GTX (Nvidia 256.53) on x86_64.
Ubuntu version 9.10, 10.04 and now 10.10 (It's been going on for a while). Also happend to a lesser degree on Vista.

Card manufacturer is BFG which has now been liquidated, just fantastic that after having this problem for so long I decide to look into RMAing it (Just this computer is for work mainly).

So- given that I know it's not a software issue, what happens when GDM is restarted that I can run "on the fly" so I dont lose my session to solve this problem?

I've also tested that the problem doesn't occur due to heat, as it's very random. Severly underclocking the card has also made no difference, leading me to think the issue is elsewhere.

2d effects high or low, the results are sporadic.

Looking in the log files, there is nothing indicated, so it's as if Ubuntu doesn't even know it's happening (Again another tick against hardware issue).

KDE and GNOME both have this issue as well.

Incase the screenshots get reduced too much. Text appears, then may disapear, and most of the time text is displayed as if printed on screen with a dot matrix with a bad ribben- blotchy. highlighting text will sometimes make the text appear. Scrolling will alter what text is shown/hidden. Images such as smilies on the right of this post new message blink on and off. Screenshot 2 is missing huge chunks of text on the right screen. AWM on the bottom of screen 1 is missing icons. However with intellihide, mousing over results in a potluck as to which icon is shown.

Finally to reitterate- restarting GDM fixes this! for a while. Without buying a new card, or restarting GDM and losing my session all of the time- any alternative fixes?

Any help would be great!

---

### Post by Quackers on 2010-09-21
Can you go back to the previous proprietary video driver? I had some slight problems with the latest nvidia driver (I have nvidia 8800M GT card). It may be worth a try.

---

### Post by Furiam on 2010-09-21
The driver makes no odds. I've used a few since I switched from Windows (Which also had the similar/same problem).

The fact that 3d games are not affected at all, 2d is screwed.

VLC under "Default output" flickers every 2-3 seconds. Switching this to GLX video output stops the flicking and plays fine whilst everything else falls to pieces on screen.

So- 
- 3D works fine whilst 2D is mashed up
- 2D looks mashed, both text and images, and video (except for GLX video output)

I'm thinking there could be something wrong with 2D acceleration?

Triggers (Could be instant, or happen after a few days since the last GDM restart / reboot)
- Playing a 3D game
- Watching a video

If none of those triggers are hit, it'll stay fine forever.

I've convinced myself now for a while that this is not a driver/OS/System issue, but a hardware fault on the card itself. But restarting the GDM fixes it all- like a complete driver reset? Anyone know enough about GDM to tell me if I can trigger this effect?

---

### Post by Quackers on 2010-09-21
What you say sounds reasonable to me, but please bear in mind that I am no expert in the field :-)
I hope you can get some further suggestions which will help.

---

### Post by Furiam on 2010-09-21
Thanks for your replies none the less :)

---

### Post by tc-progra-soft on 2010-09-29
Hello , I am experiencing similar problems on  HP laptop with  nVidia Corporation G86 [GeForce 8600M GS] (rev a1). 
Mine problems were much more awful random crashes withou any trace in logs.
Artifacts usually were the small intro to blinking CapsLock and full laptop crash. Sometimes my screen consisted with artifacts only ( green and red stripes ).
I have spent 3 days fighting with this problem. Now I have narrowed it to artifacts only.
The factors causing full crashes:
1. enabled 3D ( glx working )
2. native NVIDIA drivers;
3. nvidia-current driver
Now I am using nouveau.
My guess is that the problem may be caused by HDMI connection.
Best Regards,
Tomasz
-----------------------
Ubuntu 10.04 2.6.32-25-generic
nVidia Corporation G86 [GeForce 8600M GS] (rev a1).

---

### Post by tc-progra-soft on 2010-10-07
Finally solved. 
I have tested folowing  drivers:
nvidia-current
nv,
nouveau,
nvidia closed:
NVIDIA-Linux-x86-173.14.25-pkg1.run
NVIDIA-Linux-x86-195.36.15-pkg1.run
NVIDIA-Linux-x86-195.36.24-pkg1.run
NVIDIA-Linux-x86-195.36.31-pkg1.run
NVIDIA-Linux-x86-256.53.run
NVIDIA-Linux-x86-260.19.04.run
 with all these drivers I experienced minor ( artifacts only, artifacts and X crash ) or major problems ( crash of Xserver before login to gnome ).
I was lucky to get frequent traces in logs - minor crashes starts with the following statement in Xorg.0.log
[FONT=Arial Black][SIZE=2][COLOR=Black][mi] EQ overflowing. The server is probably stuck in an infinite loop.[/COLOR][/SIZE][/FONT]
2 Weeks lost, with approx 50 X crashes. Linux are you Windows ME clone?
[COLOR=Black]_IT IS NOT ANY DRIVER FAULT!_[/COLOR]
[COLOR=Black]The problem was solved by downgrading gdm package
from:[COLOR=Red] 2.30.2.is.2.30.0-0ubuntu3
[COLOR=Black]to: gdm 2.30.0-0ubuntu5  
The last one is a good one!
[/COLOR][/COLOR][FONT=Arial Black]BEWARE OF gdm [COLOR=Red]2.30.2.is.2.30.0-0ubuntu3[/COLOR] !!! Ticking Time bomb!
[FONT=Arial]Best regards,
Tomasz[/FONT][/FONT][/COLOR]

---

### Post by tc-progra-soft on 2010-10-21
I am sorry but  downgrading to gdm 2.30.0-0ubuntu5 didn't resolve the problem. The error is still present.
My case most likely is  following :
1. the bug occurs -> [mi] EQ overflowing. The server is probably stuck in an infinite loop. 
2. overheating of nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
3. artifacts are present
4. crash of X or whole Linux
The GPU usage is important  -  Dual screen and high resultions are the reasons of more frequent overheating and crashes.

---

### Post by beadrifle on 2010-10-26
I can confirm this on an NVIDIA 8600M card on my HP Pavillion Laptop. Red dots and gibberish pop up on the screen, goes away when I disable visual effects (set it to None). Also the gpu is overheating, I'm using version 173 of the drivers and running gdm version 2.30.5-0ubuntu4 

I am yet to try the latest drivers from the nvidia site, will do and post results.

---

### Post by cascade9 on 2010-10-26
> **beadrifle said:**
> I can confirm this on an NVIDIA 8600M card on my HP Pavillion Laptop. Red dots and gibberish pop up on the screen, goes away when I disable visual effects (set it to None). Also the gpu is overheating, I'm using version 173 of the drivers and running gdm version 2.30.5-0ubuntu4 

I am yet to try the latest drivers from the nvidia site, will do and post results.

The 173.xx drivers work on 8XXX chips, but they arent really made for those chips (173.xx is for the 'FX' or 5XXX series chips). 

You might find your problem is fixed by using nvidia-current, as those drivers were actually made for the 8XXX chips.

---

