---
title: "Oneiric: Most recent KDE upgrade broke my xserver"
date: 2011-11-01
forum: General Help
---

### Post by MrSLunk on 2011-11-01
Ok so the update today broke my kubuntu laptop.

I kinda need it to finish my thesis by monday :(
I'm running a Dell xps-m1330. graphics card is a 8400gs
Kubuntu 11.10, 3.0.0-13 kernel, nvidia closed drivers.

before the update, i was running kde to it's fullest, 3d accellerated, composting etc.

after the update,
laptop boots to kdm login
after login detials, screen briefly displays nvidia logo, flashes a few times then dumps me back at the kdm login screen.

i have re-installed the nvidia-current drivers, and nouveau and nv are blacklisted and not installed.

/var/log/xorg.0.log shows no errors and only font warnings.
modprobe nvidia displays no output

if i run startx a terminal login i get the same thing and the last few lines of console output are (...s for etc. etc.)
> 
(==) Using system config....
xinit: connection to Xserver lost


Please please please please anyone with suggestions on how to fix this, or even just get it running enough to use kile, okular, inkscape and matlab, would make me a very very relieved person.

Thanks in advanced,
Pete

---

### Post by mister_playboy on 2011-11-05
I also had a graphical problem after recent KDE updates, although in my case I after I ended up on an empty desktop because plasma-desktop was segfaulting and restarting over and over.

Deleting the ~/.kde folder and restarting with a fresh profile solved my problem... worth a try unless someone else knows more.

---

