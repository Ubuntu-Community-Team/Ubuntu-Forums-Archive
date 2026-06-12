---
title: "cannot open port 5900"
date: 2010-09-17
forum: General Help
---

### Post by evaristegalois on 2010-09-17
I am trying to access my desktop remotely via VNC. I can already access my computer using ssh, and I managed to open port 22 on my router:

Now I must open port 5900 for VNC, and I think I did exactly the same thing:

Using [http://ping.eu/port-chk/](http://ping.eu/port-chk/) (a port check service), however, my port 22 is OPEN and my port 5900 is CLOSED. Yes, I restarted my router after making the changes. Any ideas?

---

### Post by Gunman1982 on 2010-09-17
Did you check if vnc-server is running on port 5900 on the computer 192.168.0.150?
Execute 'netstat -an | grep LISTEN' to check if you have such an entry:
'tcp        0      0 0.0.0.0:5900           0.0.0.0:*               LISTEN'

---

### Post by evaristegalois on 2010-09-17
No, I don't. I do have this:

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN

for port 22. I didn't install the program vnc-server, instead I followed the instructions here: 

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)

(basically go to System > Preferences > Remote Desktop and choose all the appropriate options).

---

### Post by evaristegalois on 2010-09-20
Problem solved. 

sudo apt-get install vncviewer

Done and all is well now.

---

