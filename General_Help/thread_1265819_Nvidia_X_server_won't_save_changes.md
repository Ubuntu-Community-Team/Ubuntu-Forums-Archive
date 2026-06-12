---
title: "Nvidia X server won't save changes"
date: 2009-09-13
forum: General Help
---

### Post by hotrod6657 on 2009-09-13
So i've been away from Linux for a few months due to some stuff that just had to be done in Windows but I'm back.  Vista got funky on me for the last time today and I downloaded the latest 9.04 distro and everything was going smoothly.  It detected my graphics card, a Nvidia GeForce 9600 GSO and presented me with restricted drivers.  I chose the 180 version over the old 173 that i remember using in the past since it was marked as being "Recommended" and it installed.

I rebooted and set up my monitors, i have two that I run in extended mode.  NVIDIA X Server utility let me activate the secondary monitor and apply the change, but would not let me save the changes to X.  when i try i get an error saying that it could not make a backup of the current config file.  Now when i reboot the computer only the primary monitor turns on and i have to go back in to the X server thing and reactivate it.

Does any one know what would be causing this?  It would be nice to just get it to work with the Nvidia thing but suggestions as to how i could change my X config file manually to get the monitor how i want it would be helpful too.

---

### Post by DenysT on 2009-09-13
If you are running nVidia settings from the preferences menu it won't let you save anything. Instead open a terminal window and enter "gksudo nvidia-settings" without the quotes of course. Then you can save your settings.

Ubuntu could really use a run-as (ie. sudo or gksudo preface for the command) right click command on the menus.

---

### Post by hotrod6657 on 2009-09-14
boom, i figured there would be something like that but i wasn't sure what to try as the command.  I agree, a run as root option would be great since it's one of the only things that brings people to the terminal on a regular basis.  I actually tried right clicking on it to see if there was that option, must be a carry over from windows lol.

I'll try that and i'm guessing that I"ll be alright now, thanks a ton!

---

