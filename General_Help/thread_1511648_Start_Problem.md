---
title: "Start Problem"
date: 2010-06-17
forum: General Help
---

### Post by Dartfira on 2010-06-17
I start the pc then it comes the Normal Start Ubuntu page, where you can log by the username and password. I insert them then the monitor became black and then it comes again the ubuntu log page.
I tried to remove the nvidia driver but the only thing that change is that now ubuntu starts in Reduce Graphic Modality (excuse for my bad english).
What can i do?

---

### Post by Dartfira on 2010-06-17
up

---

### Post by Dartfira on 2010-06-18
up

---

### Post by gdonwallace on 2010-06-18
Sounds like you may be entering the wrong username or password.

To test this, when it boots up, hold down CTRL+ALT and press F1, this will take you to a terminal login.  Use the same username and password here.  If you can't login; then you know its something with that username and password.  If you can login, then there may be a deeper issue, either with Xconf or ubuntu itself.

You can also try to start X from the command line.  If you can get logged in; type **sudo startx** and that should start up the Gnome desktop for you.  If it can't, this will also display any error messages that you are not able to see from the login screen you generally use.

Good luck.

---

### Post by Dartfira on 2010-06-18
> **gdonwallace said:**
> Sounds like you may be entering the wrong username or password.

To test this, when it boots up, hold down CTRL+ALT and press F1, this will take you to a terminal login.  Use the same username and password here.  If you can't login; then you know its something with that username and password.  If you can login, then there may be a deeper issue, either with Xconf or ubuntu itself.

You can also try to start X from the command line.  If you can get logged in; type **sudo startx** and that should start up the Gnome desktop for you.  If it can't, this will also display any error messages that you are not able to see from the login screen you generally use.

Good luck.
The password is correct.

I try to use sudo startx but the only thing that I see is the arrow on a black desktop.

In the start the ubuntu console says you need to configure manually the monitor, graphic module.

---

### Post by Dartfira on 2010-06-19
up

---

### Post by dino99 on 2010-06-19
thats let me think about video not activated: boot into recovery mode, or edit the boot line and add video=vesa

you might give more details about your config

---

