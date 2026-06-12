---
title: "add start up program using console"
date: 2009-10-08
forum: General Help
---

### Post by dunskii on 2009-10-08
Hello all,

I'm in the process of building a htpc using a basic install of ubuntu 9.04 (no gnome) and xbmc.  Everything is working great. So for la pièce de résistance i decided to add a wiimote for navigation.  

I can get it working fine if I run the command wminput -c xbmc 00:19:1D:83:38:FC each time I boot up.

But so it all loads automatically on start up i need to add the command  wminput -dc xbmc 00:19:1D:83:38:FC to the list of startup programs.

How would this be done via the console as I can't Systems, Preferences, Sessions, Add. :confused:

Thanks in advance
d

---

### Post by sedawk on 2009-10-08
You can add the call to 
/etc/rc.local 
or take a simple startup script in
/etc/init.d/...
as a template for your own script.
Then create a symbolic link from e.g.
/etc/rc3.d/ to your startup script 
in /etc/init.d and it should start
during next startup.

---

### Post by dunskii on 2009-10-08
sweet, thanks heaps sedawk

now for stage 2, getting a usb tv tuner and installing mythtv

d:guitar:

---

