---
title: "GUI not loading on boot (10.04)"
date: 2010-09-29
forum: General Help
---

### Post by alhead on 2010-09-29
I just installed Ubuntu 10.04 on my Eee PC 1015PEB.  I had my computer connected to an external monitor, and I had disabled my laptop display.  Upon rebooting the machine, I only see the command line: the gui does not load.  I am logged into my username, and I can use the command line.

I have tried gnome-wm, startx, and gdm.  Using gnome-wm gives the error message "Couldn't open display" and says "DISPLAY is not set."  startx says "no screens found."  gmd says "Failed to acquire org.gnome.DisplayManager: Connection ":1.17" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file."

Does anyone know what I've done, or how I can fix this short of a reinstall?  I just installed it tonight, so I wouldn't lose much, but I'd like to avoid it.

Thanks

Edit: failsafe graphic mode also says "no screens found."

---

### Post by luvshines on 2010-09-29
What does 'runlevel' command say ?

---

### Post by alhead on 2010-09-29
Thanks for the reply.

runlevel says N 2

---

### Post by alhead on 2010-09-29
Booting from a live USB works just fine, so I may just reinstall.

---

### Post by luvshines on 2010-09-29
And echo $DISPLAY ?

---

### Post by alhead on 2010-09-29
Thanks for your reply, but I gave up and reinstalled.  DISPLAY was not defined.  I tried setting it to :0.0 (which was what printenv DISPLAY gave me while using the live USB) and exporting, but that didn't work.

---

