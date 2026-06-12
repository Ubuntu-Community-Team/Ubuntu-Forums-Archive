---
title: "Stuck at login Screen 10.04 LTS after pulseaudio uninstall"
date: 2010-06-16
forum: General Help
---

### Post by gammonjosh on 2010-06-16
While trying to fix the audio lag problem with skype I have created a new problem.  This is what I did.

Everything was working fine until I uninstalled pulseaudio from Applications>Ubuntu Software Centre>Installed Software.  I removed just about everything pulseaudio.  I than restarted ubuntu 10.04LTS.  When I attempt to login it seems to go black for a sec then kicks me back to the login screen again.  I get no errors.  If I do "ctrl, alt, F1" I can login no problem so I know it's not my password.

Any idea's?

---

### Post by cariboo on 2010-06-16
I would suggest you reinstall the packages you removed to see if that allows you to log in.

One other thing to try is after you have logged in from the command prompt, type:

```
startx
```

The above command should start the desktop, if to many dependencies haven't been removed.

---

### Post by gammonjosh on 2010-06-16
Just so I understand linux has I'm still learning.  If you remove too many dependencies you get locked out of the system?  I have run the startx and it didn't seem to do anything.

---

### Post by gammonjosh on 2010-06-18
when I try "startx" I get the following error.  I've also tried to install pulseaudio and that didn't work ether.

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/ .X0-lock and start again.

Isn't there some type of diagnostic tool I can run?

---

### Post by gammonjosh on 2010-06-18
Found the problem.  I must have uninstalled some lib packages that depended on the desktop package.

1. At the login screen type: CTRL ALT F1 (this will take you to terminal)
2. Logging with your User ID and password.
3. Now type the following:
```
sudo apt-get install ubuntu-desktop
```
4. Reboot and you should be able to login.

---

### Post by penern on 2010-06-19
I had the exact same thing happen when I was uninstalling, in order to reinstall, the audio to fix a Skype sound issue. I got the message, "Your screen graphics card, and input devices could not be detected correctly. You will need to configure these yourself." and could not even get to the login screen. When I found this thread, I tried the suggestion above and it fixed everything. Thank you so much, *$ sudo apt-get install ubuntu-desktop* not only fixed the boot problem but suddenly my sound is working just fine in Skype.  :KS :KS :KS :KS :KS

---

### Post by gammonjosh on 2010-06-22
Glad it helped.  I'm still having my audio problems with Pulseaudio/Skype on my desktop.  But it's working on my laptop fine.  Must be a sound card/pulseaudio problem.  If I remove only pulseaudio server it works, but then I have no control over my sound settings.  Anyone have a solution?

---

