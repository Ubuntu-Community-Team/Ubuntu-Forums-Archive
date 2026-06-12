---
title: "Cannot Boot Into Desktop"
date: 2012-04-29
forum: General Help
---

### Post by rookcifer on 2012-04-29
I got rid of Pulseaudio and ALSA because my sound keeps going in and out.  So, I went and got OSS, installed it and everything worked fine until I rebooted.  Now when I get to the password screen for Unity, it freezes.  After I enter my password, nothing happens, it just hangs.  Now I cannot get into my desktop.

I have tried booting from recovery mode, but when I drop to a root shell I cannot navigate to my /home/username directory.  It says no such directory.  I am using LUKS for full disk encryption, but I don't think this is the problem.  I can navigate to /home, but not to /home/username.  If I run a "ls" in /home, it is blank.

All I need is to get into my desktop.  Anyone have any ideas?

EDIT:  I see some people have this issue but only after they installed Ubuntu Tweak.  I have not done that and have not tweaked any graphical settings, so I assume my issue is different from theirs.

---

### Post by rookcifer on 2012-04-29
Forgot about ctrl-alt-F1.  That allows me to get to the shell after the hang.  Then I can kill x and then restart X from the command line.  I can get into the desktop that way but I have no Unity bar nor top bar. 

Screw it, I am backing up and reinstalling fresh from the CD.  I am going to see if the upgrade was the problem or whether it was indeed OSS (which removed Ubuntu-Desktop -- I wonder if that was the problem?)

---

