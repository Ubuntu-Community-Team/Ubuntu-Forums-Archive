---
title: "Using VNC via ssh tunnel"
date: 2010-03-25
forum: General Help
---

### Post by dizzle118 on 2010-03-25
Hi all

I've recently installed Ubuntu 9.10, installed.  Had a read of [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

I've installed opesSSH and vncserver, using UltraVNC client on windows platform I have configured via putty a new session <username>@<ip of ubunto box> via port 22, then within tunnel I set source port as 5901, destination as <ip of ubunto box>:5901.  Connected to session, typed in password, started vncserver
#vncserver

New '<machinename>:1 (<user>)' desktop is <machinename>:1

Starting applications specified in /home/<user>l/.vnc/xstartup
Log file is /home/<user>/.vnc/<machinename>:1.log

Open UltraVNC client and try to connect to 127.0.0.1:5901

and it fails :-(

What am I doing wrong?  I thank you for your help in advance :-( - I just wanna see my gnome desktop remotely

---

### Post by jimv on 2010-03-25
Unless you changed the default port, you should be using 5900.  Also, there's a neat little app for Windows called "MyEnTunnel" that will open your tunnel automatically (simpler to use than Putty).

[http://nemesis2.qx.net/pages/MyEnTunnel](http://nemesis2.qx.net/pages/MyEnTunnel)

---

### Post by dizzle118 on 2010-03-25
Right - I changed to port 5900

Now I receive this error when trying to connect via UltraVNC.....

> Connection failed - End of Stream

Possible causes:

-Another user is already listening on this ID
-Bad Connection

Any suggestions?

---

### Post by dizzle118 on 2010-03-25
How can I verify what port vncserver is listening on (to prove to myself its 5900) ?

---

### Post by jimv on 2010-03-25
Well, you can open the Remote Desktop viewer on the Ubuntu machine and connect it to itself.  Warning: may create sense of vertigo.

Make sure that you've enabled VNC in System > Preferences > Remote Desktop.

---

### Post by jimv on 2010-03-25
Also, any particular reason why you're trying to go through the SSH tunnel?

---

### Post by dizzle118 on 2010-03-26
Basically to encrypt my connection :)

Managed to get it working, using the VNC client you need to connect to 127.0.0.1:1  - the desktop instance :p

---

