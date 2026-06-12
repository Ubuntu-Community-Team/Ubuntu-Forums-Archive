---
title: "Nvidia binary drivers stopped working"
date: 2006-03-17
forum: General Help
---

### Post by dashnak on 2006-03-17
Hello, I've been having some really unnerving problems with my 3d drivers in Breezy...
Everything was working fine up to some 3 1/2 weeks ago, and then I downloaded all new updates and stuff...
One of them was a kernel update, and everything went fine.... However, I didn't reboot my PC for like another week...
And then, when I did, instead of the Nvidia logo; my screen did some weird thing where it showed black in the top half and then white in the bottom half and then the the other way around, then it would crash and say that my X couldn't be started....
I played around with sudo dpkg-configure xserver-xorg and found out that after reconfiguring everything would start Ok, although I had to do it everytime I rebooted... 
And it wasn't an option, because then my sister would be unable to spawn another login screen to enter her account without having to kill mine...
So I unistalled every Nvidia related thing and went back to using the nv driver...
Some days ago I tried again, and those things still happen....
However, now after I say ok to the crashing notice and everything and login to my account via CLI, if I issue startx everyhting works AGAIN and I have 3d, still leaving my sister out int he cold though...
So, I was wondering if anyone could help me with this, I'm really desperate, since I need to do some work in blender and other 3d stuff, and my sis uses the PC when I'm at school...

---

### Post by dashnak on 2006-03-18
Mhhh, well.... Thanks anyway...

---

### Post by jesse on 2006-03-18
Have you tried using automatix to automatically reinstall the nvidia driver?

---

### Post by astoltz on 2006-03-18
[QUOTE=dashnak]And then, when I did, instead of the Nvidia logo; my screen did some weird thing where it showed black in the top half and then white in the bottom half and then the the other way around, then it would crash and say that my X couldn't be started....[/QUOTE]
Usually when it can't start the X server, it gives you the option of looking at the error message (you might have to select an 'OK' button).  Does this happen with your's?  If so, it would help if you could post the error message.

---

### Post by Ramses de Norre on 2006-03-18
Or from terminal do less /var/log/Xorg.0.log and less ~/.xsession-errors

---

### Post by dashnak on 2006-03-18
The /var/log/Xorg.0.log file doesn't exactly mention any errors, but it stops at this line:
"(II) Initializing extension GLX"
And .xsession-errors doesn't show anything that I think I recognize as an error related to this matter...
This is too weird...

---

### Post by dashnak on 2006-03-18
Sorry for bumping this, but I'm really desperate, hehe

---

### Post by astoltz on 2006-03-18
So what happens when you get the message that X couldn't be started?  Is there any other info after that?

---

### Post by Zeroangel on 2006-03-18
Have you tried reinstalling nvidia-glx according to the guide? You also have to make sure to comment out the glx entry in /etc/X11/xorg.conf if you do that.

---

### Post by dashnak on 2006-03-19
After saying that X couldn't be started, it says that I check if everything's correctly configured and that GDM will be disabled until I fix that...
As for reinstalling according to the guide, I'm pretty sure that's what I've been doing, however; I'd really thank you if you could be a little more specific on that, just to make sure - you know?
Thanks

---

### Post by dashnak on 2006-03-19
Also, if I comment the GLX extension, my X starts without a hitch, but, obviously, without any acceleration whatsoever....

---

### Post by dashnak on 2006-03-21
Ok, I finally fixed it...
Turns out that inside /etc/initr.d/ there were two scripts named nvidia-glx and nvicia-glx-legacy, since I use the legacy driver, I assumed there was no reason at all for nvidia-glx existing, so I removed the execution permissions from it and now everything works just fine...
Edit: After doing that, I simply realized that if I either renamed or deleted nvidia-glx then I wouldn't have to see the useless error message it caused when booting and halting, hehe....

---

