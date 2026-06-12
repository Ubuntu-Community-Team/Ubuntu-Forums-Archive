---
title: "Keep running after logout"
date: 2009-08-06
forum: General Help
---

### Post by AndyGibo on 2009-08-06
Hi people

Here's my problem, I have an Ubuntu system sitting in the closet under my stairs acting as a file server.  I was hoping to use it to manage my downloads as well but this is where the problem starts, in two parts.

First, I need to remote connect to the system (with a gui) from the log on screen, as no one will be able to physically log on to the system now.

Second, I need the downloads to remain active after I logout of this remote connection.

Any ideas???
Thanks in advance!

---

### Post by dcstar on 2009-08-07
> **AndyGibo said:**
> Hi people

Here's my problem, I have an Ubuntu system sitting in the closet under my stairs acting as a file server.  I was hoping to use it to manage my downloads as well but this is where the problem starts, in two parts.

First, I need to remote connect to the system (with a gui) from the log on screen, as no one will be able to physically log on to the system now.

Second, I need the downloads to remain active after I logout of this remote connection.

Any ideas???
Thanks in advance!

There are HOWTOs on setting up Remote Access, and there is no need to "Log out" when you can simply lock the screen and then disconnect.

---

### Post by AndyGibo on 2009-08-08
I have tried two different ways of setting up a remote connection (xdmcp and vnc).  Both have been able to connect to the system at the login screen but I have not been able to successfully keep any downloads going after I have logged out or locked the screen and disconnected the session.

Any more suggestions?!?!

Just a little more info, the Ubuntu system I am trying to connect to is running 9.04

---

### Post by AndyGibo on 2009-08-09
Bump Bump Bumpety Bump

(Just to remind every1, trying to connect to an Ubuntu 9.04 system remotely, with resumable sessions so that my programs, downloads keep running after I disconnect.  Cheers)

---

### Post by martinbaselier on 2009-08-09
Why don't you just setup a user to login automatically when the system is powered on? 

You can easily enable that in the login properties, under the settings menu.

---

### Post by keithweddell on 2009-08-09
ssh and screen?  Not GUI but probably more powerful.  Don't know though because I don't use remote desktop.

Keith

---

### Post by aesis05401 on 2009-08-09
+1 screen.

This is exactly what screen was designed for.. just not gui.  For those who might be interested:[http://en.wikipedia.org/wiki/GNU_Screen]("http://en.wikipedia.org/wiki/GNU_Screen").

---

### Post by AndyGibo on 2009-08-10
Thanks for the replies.  I know I can enable the user to automatically login but I would have thought that to be a bit of a security risk.  Also I'd prefer the remote connection to start at the login screen in case other users need to login.

I know of "screen" but I need a GUI.  As I've said the system will be used as a download manager, so a GUI will be more useful for browsing the web.

---

### Post by AndyGibo on 2009-08-11
Bump

---

### Post by fsando on 2009-09-12
I'll second your bump.

Being able to keep connection before login/after logout is the default on windows.

There could be several scenarios where this behavior is needed one would be if you make changes to the your account that only take effect after a logout - login others may be if gnome/x crashes and you need to restart x.

---

