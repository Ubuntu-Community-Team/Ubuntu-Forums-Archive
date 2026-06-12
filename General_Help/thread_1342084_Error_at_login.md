---
title: "Error at login"
date: 2009-11-30
forum: General Help
---

### Post by lulirondissone on 2009-11-30
Hi! I had recently installed Karmic in a brand new computer, and I have 2 errors at login:

Error 1: "There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
Error 2: Nautilus could not create the following required folders: /home/user/Desktop, /home.user/.nautilus"

I know that there are other post with this errors, but I didn't find them together and I didn't have the same problem as they had.

For error 1, if I say "OK", nothing bad happens, I can log in perfectly and everything works fine.
For error 2, if I say "OK", I can log in but then the desktop is set up as default and nothing works.

For error 1, I tried "sudo apt-get install gnome-panel", but it says that I have the latest version, so, no help there. Tried ""chmod 775 /etc/gconf/gconf.xml.system" but dind't work either. (Bugs #269244 and #269215).


For error 2, I tried log in on the oldest version of Karmic available at the initial list (when the computer starts, I have two options, version 9.10.14 and 9.10.15). If I choose the .14 version, the Nautilus error dissapears.


Any help? 



Thanks!

---

### Post by avi0 on 2009-12-03
I have also seen a error number 1

---

