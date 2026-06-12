---
title: "Problems with VNCServer"
date: 2010-09-20
forum: General Help
---

### Post by bspear on 2010-09-20
Hello, 
I am having an issue with Ubuntu 10.10 and VNCServer.  I can connect to my Ubuntu box remotely with VNC, but if I type any character anywhere, it closes out the window I was typing in.  I dont seem to have a problem clicking and opening windows and applications, I just cant type anything into them without the window closing.  Has anyone seen this behavior and know what the fix is?  Thanks.

---

### Post by sedawk on 2010-11-05
Same issue here

Client: XP, RealVNC, 4.1.3
Server: Ubuntu 10.10
Client connects via cygwin + ssh + ssh-port-forwarding.

When I press 'd' the active windows minimizes, when I press it
again the window resizes to previous state.
Problems started after upgrading to 10.10.

So far I had no chance to test it with a different client,
that is on my list ...

---

### Post by alienprdkt on 2010-11-05
try installing nomachine much faster VNC solution! Have been a big fan for 4 yrs. Works great! Very easy to use.


[http://www.nomachine.com/download-package.php?Prod_Id=2069]("http://www.nomachine.com/download-package.php?Prod_Id=2069")

windows client

[http://www.nomachine.com/download-package.php?Prod_Id=2131]("http://www.nomachine.com/download-package.php?Prod_Id=2131")

mac client

[http://www.nomachine.com/download-package.php?Prod_Id=2130]("http://www.nomachine.com/download-package.php?Prod_Id=2130")

---

### Post by areeda on 2010-12-19
Anybody figure out what's going on here.

I can't get to the nomachine.com site otherwise I'd give that a try.

I'm trying to connect from a 10.04 to a 10.10 system and can't do anything that requires the letter d be typed.

One other thing.  When you start vnc it creates the file xstartup in ~/.vnc
In there is 
exec /etc/X11/xinit/xinitrc
 which you need for a normal desktop.  Only problem is you can't exec a shell script.  It should be
. /etc/X11/xinit/xinitrc

10.04 doesn't have this issue.  It's something on the server side.

Joe

---

### Post by areeda on 2010-12-19
OK I found the answer in this [linux expresso blog]("http://linuxexpresso.wordpress.com/2010/10/17/howto-ubuntu-vnc-encoding-server/")

> One other important thing, for some bizarre reason, the d key defaults  to closing all windows open on the desktop. Strange yes, but easily  fixed. Login to your VNC server, click System>Preferences>Keyboard  Shortcuts and scroll down to &#8220;Hide all normal windows and set focus to  the desktop&#8221;. Click the D entry, and hit backspace to disable it.I will file an issue.

One more thing.  Kill the server and restart it.

Joe

---

