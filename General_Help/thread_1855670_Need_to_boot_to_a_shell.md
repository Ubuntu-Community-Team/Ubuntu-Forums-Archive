---
title: "Need to boot to a shell"
date: 2011-10-06
forum: General Help
---

### Post by bartmc on 2011-10-06
OK, im developing this kiosk application and really trying to lock down the OS so the user can't tiker. I have disabled the screen switching, drop to a terminal via ALT-CTRL-Fx by using the xorg option DontVTSwitch, I configured the system to auto login and go directly to an lwm session (this has no launchers, toolbars, desktop icons, nada, doesn't start an xterm or anything). Only problem is, I forgot to lanuch ANYTHING when the system starts up so now I'm auto logged into a blank lwm session and have disabled my hot keys to drop me to a shell, IIRC there's a way to pass paramters to GRUB at startup to boot to a console.... HALP!!!

---

### Post by jazzon on 2011-10-06
ahhhhhhhh.......
Yuk thats as bad as me the other day running usermod to change my groups and dropped all groups cept a powerless one!  Couldnt even sudo to fix it.


Does it not launch anything at all or just nothing graphical.  I.E.  Can you ssh in from another machine?

---

### Post by bartmc on 2011-10-06
It boots directly into an lwm session, lwm is as bare bones as bare bones gets for a window manager, the idea is to run it with gnome or something else, I don't want to do that. My application has password protected provisions for launching an xterm so that techs can debug issues BUT I FORGOT TO LANUNCH IT! Basically all I can do is use the mouse to click nothing. I never setup ssh, maybe it's on by default,  let me see if I can get in that way.

---

### Post by patryk77 on 2011-10-06
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

I do believe this is what you are referring to, but it may not be possible since you probably do not know the root password?

Your best bet would probably be to run from a Live CD and make modifications there.

---

### Post by matt_symes on 2011-10-06
Hi

On the grub boot screen select the kernel you want to boot into and press e to edit the kernel command line.

Remove the words 'quiet splash' and add the word 'single' to boot into single user text mode or 'text' to boot into multi user text mode.

Then you press ctrl + x to continue booting - IIRC but it should say somewhere on the screen what you need to press to continue booting as i might be wrong here.

Kind regards

---

### Post by bartmc on 2011-10-06
Alright I figured it out if someone is as stupid as me in the future.. Hold down the SHIFT key while booting, then select the recovery mode option, at the next prompt select netboot. that got me to a shell where I could edit the xorg.conf to re-enable my hot keys. Oh I always set the root password so I knew that. Thanks.

---

### Post by bartmc on 2011-10-06
The part i was needing to know was to hold shift down to get the grub screen.

---

