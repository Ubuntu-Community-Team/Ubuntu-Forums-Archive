---
title: "No Display"
date: 2010-02-26
forum: General Help
---

### Post by muliganstew on 2010-02-26
I recently tried to use a secondary monitor on my laptop and was prompted to log in and out.  Now whenever I start up ubuntu I am given the startup logo and then a cursor in the upper left hand corner that is not responsive to keyboard input.

---

### Post by muliganstew on 2010-02-27
bump, please help.  I've tried solutions such as going into recovery mode and running dpkg-reconfigure -xserver -xorg but that doesn't do anything so I'm not sure what exactly is wrong.

---

### Post by muliganstew on 2010-02-27
UPDATE:  So I went into the recovery mode, dropped into the root shell, and then ran startx and got this:

Fatal server error:
AddScreen/ScreenInit failed for driver 0.

It also advises me to view the log file "/var/log/Xorg.0.log", which I did but have no idea how to analyze.

Any ideas guys?

---

### Post by muliganstew on 2010-02-27
Okay, so after looking around I was able to sucessfully edit my xorg.conf file and now it boots properly

---

