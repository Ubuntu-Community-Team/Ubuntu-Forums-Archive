---
title: "VNC Viewing"
date: 2010-06-20
forum: General Help
---

### Post by rensell on 2010-06-20
I've recently got my server (xUbuntu, SAMBA, CUPS) all "up and running" and today have installed x11vnc and set to autostart at my login. 

I'm able to use VNC Viewer (realVNC) to connect to my sever. However, if I close VNC and then need to connect again, I get an error saying the connection has been refused. I'm wondering how I go about "logging out" with VNC but leaving the account logged in on the server and allow myself to connect with VNC again.

I've set this server up in order to get away from my XP Pro as a server setup, which allows me to use RDP to make connection after connection with no problem and the user doesn't have to connected logged in either.

Thanks in advance,
-R

---

### Post by davidmohammed on 2010-06-20
try starting with

x11vnc -forever

or maybe

x11vnc -shared

type man x11vnc to find out what those options do and which one is best for you.

---

### Post by rensell on 2010-06-20
Thank you very much. I decided to add -forever over shared because I don't want simultaneous connections.

---

