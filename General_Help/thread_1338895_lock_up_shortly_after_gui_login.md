---
title: "lock up shortly after gui login"
date: 2009-11-26
forum: General Help
---

### Post by Buggin on 2009-11-26
Ubuntu 9.10 - been running fine for a couple months... clean install.

Today while logged in and doing a few things. I think I had a browser open, amarok, vuze, a terminal. Nothing much really. The whole computer just froze. No mouse, no num lock on the keyboard, pwr button on pc is ignored (normally will shut down when i press it), etc... non responsive. 
I hit reset and rebooted. logged in and things seemed fine. Starting getting back to what I was doing and it froze again. vuze and my browser were using java so at first i thought that was the problem because both times i had just tried to use one of them. i was wrong though, because i can turn the thing on, log in to gnome, and within a minute it locks up.

if I ctrl-alt-F1 and login it works fine.

I tried creating a new user account from CLI and then logging in with that account and the exact same thing happens even if I don't press another button after logging in. If I give it a minute and try to move the mouse it's locked.
I ran top one time to see what was happening and to be honest i didn't see much going on at the time. aptd was running at the top of the list when it froze. I looked through syslog too... didn't see anything.

I need help guys... I didn't think this could even be a problem with linux. Tell me what you need and I'll post it. I've got my laptop so I can ssh in to the other one and get whatever you need to see.

---

### Post by Buggin on 2009-11-27
UPDATE

I installed xubuntu-desktop and I can log in there with no freeze
so apparently the problem is with gnome or something related... still need help

i like gnome... kde and xfce really aren't for me

just tell me what you need and i'll post it

---

### Post by Buggin on 2009-11-27
Please!?

---

### Post by Buggin on 2009-11-28
final bump

failsafe gnome also crashes in under a minute... even if i don't do anything

i'm not sure what it trying to load but i distinctly heard the hard drive read (or write) and then boom frozen

---

### Post by Buggin on 2009-11-30
ok i lied one more bump


still can't find anything in the logs... xfce is still running fine... gnome is still freezing in under a minute of login

i'm still hopelessly lost and in need of some direction

---

### Post by Spectre5 on 2009-12-01
Are you sure that XFCE doesn't freeze - are you actually staying in XFCE for more then just a few minutes?  Log into XFCE and use it for awhile (open stuff, etc) to be 100% sure that it doesn't also freeze.  If XFCE also freezes, then it sounds like a RAM problem to me...

Which log files are you checking?  Check each log file in /var/log for errors/warnings, etc...

I used to have a problem similar to this (on a VERY old computer)...removing one stick of RAM fixed the problem (bad RAM or bad RAM slot on the mobo was my best guess for that problem).

---

### Post by ashu. on 2009-12-01
> **Spectre5 said:**
> Are you sure that XFCE doesn't freeze - are you actually staying in XFCE for more then just a few minutes?  Log into XFCE and use it for awhile (open stuff, etc) to be 100% sure that it doesn't also freeze.  If XFCE also freezes, then it sounds like a RAM problem to me...

Which log files are you checking?  Check each log file in /var/log for errors/warnings, etc...

I used to have a problem similar to this (on a VERY old computer)...removing one stick of RAM fixed the problem (bad RAM or bad RAM slot on the mobo was my best guess for that problem).
no its not a ram problem i had same problem n asked for help not one solution worked if u have another account try login with it else try login as root at gui n create another account 
[which is what i did] try it

---

### Post by JoyousDeath on 2010-01-01
I am having a similar problem, though the gui locks up much quicker. I have about a one second window for moving the mouse before it refuses to register anything, even the power button. I'm going to clean out the computer and remove a ram chip to see if those are the causing problems.

---

### Post by JoyousDeath on 2010-01-01
Me again. I cleaned my computer of cobwebs and removed the ram (one at a time of course) and tried using each one individually, no success.

Any help would be greatly appreciated.

Edit:

Silly me I forgot my specs. 
OS is Ubuntu 9.10, version 8.04 worked fine as long as you didn't run specific programs, so I don't think it's a matter of ram.

---

### Post by Groundswell on 2010-01-01
i know this isn't an answer anyone wants to hear, but it really sounds like hardware. try disabling all desktop effects, because if xubuntu is workin fine, and gnome is crashin, it sounds like video hardware problems. (if i remember xubuntu doesn't use any 3d acceleration, been 3 years since i've touched it) if you have room on your hardisk to do so, try other desktop environments, if it is video problems, kde will crash you, fluxbox will run fine. also try 3d apps when loaded in xubuntu, wine or linux native, just make sure they're using some opengl, if they cause hard lock too, you can bet your dollar its video hardware :(

---

### Post by JoyousDeath on 2010-01-01
Upgraded files via ctrl+alt+F1 which didn't help.
Also, my graphics card is integrated.
"Vga compatible controller: Intel corporation 82945G/GZ Integrated Graphics Controller {Reb 02}".

=

If it is a hardware issue, it's odd that I was able to have desktop effects on with minimal problems in 8.04, but ah well, could you walk me through disabling desktop effects in the ctrl+alt+F1 menu?

---

### Post by JoyousDeath on 2010-01-01
I have no idea what happened, but the problem seems to have been solved (for now).

I tried a few commands that did nothing in ctrl+alt+F1, and upon leaving the console I was greeted to a desktop that didn't freeze on me.

Will post later if problems arise again.

---

### Post by JoyousDeath on 2010-01-03
I'm back, the original computer having this problem is fine (Two days without an accident). However I installed Ubuntu on a completely different machine (9.10 installation disk) for a friend and the same problem persists on his. I'm trying to go through all the motions I did in ctrl+alt+del, though to no avail. Another problem; when I boot up it gives me an error about bad sectors in the hard disk. Anyone know anything about that?

Edit:
Problem subsided for now, apparently it wasn't the things I did in the console (ctrl+alt+del) just that I stayed in the console long enough (perhaps there were auto-config files that needed to finish?) Though there is still a warning about there being bad sectors on my hard disk (though I think that's another problem entirely).

Edit2:
It seems the console only staved off the problem for a few minutes. Right now I'm just letting it sit at the console for a while to see what happens. (Note: it doesn't lock up when in the console)

---

