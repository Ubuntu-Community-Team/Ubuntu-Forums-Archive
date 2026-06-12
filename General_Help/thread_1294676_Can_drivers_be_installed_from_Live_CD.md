---
title: "Can drivers be installed from Live CD?"
date: 2009-10-18
forum: General Help
---

### Post by munkifisht on 2009-10-18
I am quite new to Linux and Ubuntu, and ran into a problem there. I installed a game. I started it up, and the screen started to flicker, the computer then rebooted itself

Now when I start up, the graphics drivers appear to be corrupted. I get a flickering, the screen is mostly black. There is a thin band of red shapes at the top of the screen, about 10 pixles high. The Ubuntu load sign can be seen, but it is distorted, there are two of them, and it is green, white and purple. The system boots to this point and locks up. It is completely unresponsive.

I can do a workiong command line boot. I can also boot into vista with no problems, so not a hardware issue. I tried to restore to the oldest backup of the graphics drivers with no luck.

I want to avoid doing a fresh install. Is there anyway to install the install disk default drivers again from the command line, and if so can someone explain it to me?

---

### Post by munkifisht on 2009-10-19
.

---

### Post by badger_fruit on 2009-10-19
drivers come as part of the kernel, but if something's gone a bit whappy, you could always try installing the graphic card drivers again from the manufacturer's website .. they're usually more up to date than the ones included in the kernel.

do it just as if you were in windows
browse to website > download > locate > run

they should provide specific drivers for your OS and card though so don't be a gimp and try to install the Vista drivers on Ubuntu ;)

---

### Post by P4man on 2009-10-19
> **munkifisht said:**
> I am quite new to Linux and Ubuntu, and ran into a problem there. I installed a game. I started it up, and the screen started to flicker, the computer then rebooted itself

Now when I start up, the graphics drivers appear to be corrupted. I get a flickering, the screen is mostly black. There is a thin band of red shapes at the top of the screen, about 10 pixles high. The Ubuntu load sign can be seen, but it is distorted, there are two of them, and it is green, white and purple. The system boots to this point and locks up. It is completely unresponsive.

I can do a workiong command line boot. I can also boot into vista with no problems, so not a hardware issue. I tried to restore to the oldest backup of the graphics drivers with no luck.

I want to avoid doing a fresh install. Is there anyway to install the install disk default drivers again from the command line, and if so can someone explain it to me?

When did this start happening? After you did the install of ubuntu or after installing drivers (and which drivers did you install?)

Anyway, its certainly possible from a root shell, but you could try booting in to recovery mode and using the xfix option ( I think its called).

---

### Post by munkifisht on 2009-10-19
Jsut two things, firstly, according to something I read, the ATI drivers do not yet work with V9.04. If this is incorrect, could someone give me instructions on how to navigate via the command line to another drive (I can't get internet access either for some reason). I also tried to do a reinstall of Ubuntu but with no success. What does a reinstall do? Is it not like windows in that it does not format the disc?

---

### Post by P4man on 2009-10-19
> **munkifisht said:**
> Jsut two things, firstly, according to something I read, the ATI drivers do not yet work with V9.04. 

Thats incorrect. Before I expand my answer, can you tell me which videocard you have?

> If this is incorrect, could someone give me instructions on how to navigate via the command line to another drive (I can't get internet access either for some reason). I also tried to do a reinstall of Ubuntu but with no success. 

Slow down..
You can boot from a live cd, and the screen is allright, yes?
So you installed and then the fist boot things were messed up, or after you installed the restricted driver for your videocard?

> What does a reinstall do? Is it not like windows in that it does not format the disc?


It reinstalls :) And in fact, unless you made a seperate /home partition, its even more destructive then windows. It will format the / partition and you'll lose anything on it.

---

### Post by MelDJ on 2009-10-19
edit

---

### Post by munkifisht on 2009-10-19
> **P4man said:**
> Thats incorrect. Before I expand my answer, can you tell me which videocard you have?
Its an ATI Mobility Radeon X700 


> **P4man said:**
> 
Slow down..
You can boot from a live cd, and the screen is allright, yes?
So you installed and then the fist boot things were messed up, or after you installed the restricted driver for your videocard?


I think I saw the same problem a day or two ago, but a reboot seamed to work out the kinks as it were. I had not rebooted in quite a while when the problem appeared again. The computer was probably on for 2 or 3 days straight. As I am looking at linux for the first time, this is a grand experiment for me. An awful lot of programs were installed, I am not sure if I could list them. I did see that before the computer crashed I was experiencing some graphic problems in one of the games I had downloaded, the screen flickered, as if it was on the wrong refresh rate, and before I could shut it down the computer rebooted. 

> **P4man said:**
> 
It reinstalls :) And in fact, unless you made a seperate /home partition, its even more destructive then windows. It will format the / partition and you'll lose anything on it.

Ah

---

### Post by munkifisht on 2009-10-19
> **P4man said:**
> When did this start happening? After you did the install of ubuntu or after installing drivers (and which drivers did you install?)

Anyway, its certainly possible from a root shell, but you could try booting in to recovery mode and using the xfix option ( I think its called).

I may have tried to install the ATI drivers. I have tried the xFix Option but with no success.

I may just bite the bullet on this one and start from scratch. I don't have any important info on said machine, just time invested in setting up. Could someone gimme some tips as to how to backup my system to prevent this type of thing from happening again though?

---

### Post by P4man on 2009-10-19
> **munkifisht said:**
> Its an ATI Mobility Radeon X700 

Ok, the x700 is no longer supported by ATI, so you cant get binary drivers from them for recent releases of linux, but your card is supported by the opensource drivers which are fairly decent -and which are installed by default, no need to download or install anything.

> I think I saw the same problem a day or two ago, but a reboot seamed to work out the kinks as it were. I had not rebooted in quite a while when the problem appeared again. The computer was probably on for 2 or 3 days straight. 
As I am looking at linux for the first time, this is a grand experiment for me. An awful lot of programs were installed, I am not sure if I could list them. I did see that before the computer crashed I was experiencing some graphic problems in one of the games I had downloaded, the screen flickered, as if it was on the wrong refresh rate, and before I could shut it down the computer rebooted. 

Hmmm.. dont want to jump to conclusions, but this doesnt sound good. Im thinking hardware problem (gpu overheating?) or something corrupted. But thats just a hunch, lets see first.

If you boot off the cd, does everything look and work normally? If not, then it is almost certainly a hardware failure. If the live cd or usb stick works fine, then lets find your xorg log file. Go to places > name of your harddisk. That opens the filemanager

browse further to /media/nameofyourharddisk/var/log
and locate the file called Xorg.0.log

Attach it to a post here.







Ah

---

### Post by P4man on 2009-10-19
> **munkifisht said:**
> I may have tried to install the ATI drivers. I have tried the xFix Option but with no success.

I may just bite the bullet on this one and start from scratch. I don't have any important info on said machine, just time invested in setting up. Could someone gimme some tips as to how to backup my system to prevent this type of thing from happening again though?

our posts crossed. If you tried forcing the wrong drivers, I guess it would explain. You could try reverting to the old by booting the recovery console and selecting a root shell. then type this.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by munkifisht on 2009-10-19
> **P4man said:**
> our posts crossed. If you tried forcing the wrong drivers, I guess it would explain. You could try reverting to the old by booting the recovery console and selecting a root shell. then type this.

```
dpkg-reconfigure xserver-xorg
```

YOU LEDGEND!!! Thunderbirds are go, worked right away

---

### Post by P4man on 2009-10-19
Good Im glad to hear. 
Now remember your card has been obsoleted and you will never ever need to download other videodrivers (for linux) than the ones you already have out of the box. Nothing else will work.

---

