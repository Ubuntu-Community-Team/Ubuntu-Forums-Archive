---
title: "userlist dialog at startup problems"
date: 2010-07-17
forum: General Help
---

### Post by tristan8276 on 2010-07-17
Hello,

My girlfriend has a Toshiba Satellite Athlon64 laptop, and she can't get it to go past the user list dialog before it logs all the way in.  We've tried her username and password, but every time we enter it, the screen blanks for a moment and then returns to the user list dialog.  I've reset the password by booting to terminal, but it still won't let us past the dialog.

I'd hate to have to reinstall her system.  Is there any way we can get past this?  And, why is it not accepting the password?  I couldn't find an open bug on this issue.

Also, we had just installed OpenShot Video Editor during the same session.  She said she got it from the Synaptic Package Manager.  I'm not sure if this messed with her video settings.  We can see X trying to start after we put the password in, but it keeps going back to the user list dialog.

Actually, I uninstalled OpenShot and gnome-screensaver from the root prompt, just in case they were causing the issue.  I had noticed that the laptop was buggy coming in and out of hibernation.  I wonder if that's causing X not to start properly?  I did check the startup logs and I didn't see any errors there either.

---

### Post by tristan8276 on 2010-07-18
Could this be an issue with gnome-power-manager?

Also, I've tried executing /etc/init.d/gdm restart from root prompt, but the issue is still present.

---

