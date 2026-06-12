---
title: "n00b need help failed to start the x server"
date: 2006-02-20
forum: General Help
---

### Post by Chimona on 2006-02-20
I just installed breazy, and can't load os. it says failed to start x server, and i have no idea how to get to the configuration file. please be very specific in your response, i'm very new to linux.

---

### Post by RAOF on 2006-02-20
It would be good to know what sort of graphics card you have.  If you know, excellent.  If you don't, well, we'll help you find out.

Once it says "failed to launch x-server", press Ctrl-Alt-F1.  This should get you to a terminal login, saying something like
```
Ubuntu Breezy 5.10 and some other stuff
username:

```
Type in the username you set up during install, followed by the password when it asks for it.  It **won't** give any indication that you're typing in the password (not even '*'s), but it will be working.  You'll then get to a command prompt, looking something like:
```
chris@RAOF:~
```
Type in "sudo dpkg-reconfigure xserver-xorg"
It will ask for a password.  Type yours in.  Like the login, you'll get no feedback.

dpkg-reconfigure will ask a lot of questions.  Unless you know better, the defaults are fine, **except** when it comes to selecting the graphics driver.  There'll be a long list of drivers (ati, nv, trident, etc) - you want to select the "vesa" driver - this is a fail-safe driver that should always work.  

Once you're done, type "sudo /etc/init.d/gdm restart".  You should now get a graphical login screen, and your GUI should work.  We can start refining stuff from there :)

---

### Post by anirban.sam on 2006-02-20
from a console type, sudo dpkg-reconfigure xserver-xorg

---

### Post by Chimona on 2006-02-21
every time i type sudo it gives me this error, "unable to look up <hostname> via gethostbyname() "

---

