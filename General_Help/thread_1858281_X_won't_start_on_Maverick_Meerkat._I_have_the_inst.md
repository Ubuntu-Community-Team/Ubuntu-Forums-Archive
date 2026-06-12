---
title: "X won't start on Maverick Meerkat. I have the installation disc and everything..."
date: 2011-10-12
forum: General Help
---

### Post by Stanoz on 2011-10-12
I use a HP Tx2 laptop. I run Maverick Meerkat. I was surfing the web with my Globacom 3G modem here in Owerri, Nigeria, (which is actually a HUAWEI Mobile Broadband E173 modem) and got a little carried away and pulled it out of the USB port without shutting the system down first. Now, my computer doesn't seem to be able to start the X Windowing System anymore!
When I choose Ubuntu from grub, I get the initial purple Ubuntu flash screen with the five dots. After that the computer just freezes!
So, I proceed to reboot and to choose "Ubuntu...recovery mode" this time around from the grub menu; and this takes me to the Recovery Menu. Nothing really helps me here, except the 'resume' option which dumps me at a bash prompt.

Trying 'startx' tells me that:
...Parse error on line 20 of section In in file /usr/share/X11/xorg.conf.d/10-evdev.conf
        "In" is not a valid section name.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
...
ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directore (errno2): unable to connect to X server
xinit: No such process (errno3): Server error.

Please how do I solve this problem? I have my original Ubuntu installation disc that I got from one of my LinuxFormat magazine discs, that is LXFDVD139.

Thank you.

-- Stanley Bob-Carl Ozoemena

---

### Post by mastablasta on 2011-10-12
have you tried launching an older kernel by chosing it in grub menu?
 
Edit: or you never updated it ?!

---

### Post by Stanoz on 2011-10-12
I never updated it. :0(

---

### Post by Stanoz on 2011-10-12
I, some minutes ago,  tried to backup xorg.conf so I could replace it and still not take the risk of losing it entirely should something go wrong. But I discovered that it  wasn't there! That's funny. So, I copied /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf

But now, I get YET ANOTHER ERROR in addition to the earlier xinit error lines! 
Now, the computer tells me:
xauth: error in locking authority files /home/stanley-bob-carl-ozoemena/.Xauthority

Please help this newbie!
(I'm tearing my hair out again!)

---

