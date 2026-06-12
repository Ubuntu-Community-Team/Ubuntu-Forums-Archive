---
title: "SSH VNC Help"
date: 2009-08-02
forum: General Help
---

### Post by Kai-vana on 2009-08-02
Hi all,

The set-up I have is a laptop running vista that has Putty and a VNC viewer installed, I can SSH tunnel my VNC connection into my Ubuntu desktop running an VNC server fine. What I am now trying to do and I'm not sure if this is possible is forward on the tunnel from my Ubuntu desktop to my WinXP desktop which is running OpenSSH for Windows and an VNC server.

Thanks in advance,

Kai-vana

---

### Post by Kai-vana on 2009-08-03
OK so I worked out the answer on my own.

All I had to do was change the tunnelling setting in Putty from L5900 localhost:5900 to L5900 ipaddressofxppc:5900

then in my vnc viewer connect to localhost:5900

---

### Post by Kai-vana on 2009-08-04
Ok turns out I did not get it working after all, I can get the ssh tunnel to work if my laptop is on the same lan as my widows box but I ssh in from the web I cant set VNC to connect.

---

