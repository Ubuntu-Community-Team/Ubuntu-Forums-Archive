---
title: "vnc over ssh"
date: 2010-04-26
forum: General Help
---

### Post by spiky001 on 2010-04-26
I have tried to find the answer to this, I use remote desktop which connects to my home server (on Lan) I have seen I can do it via ssh is this possible I need to be able to use network manager on remote machine, to start my mobile broadband conection, I hope this is clear if not I can give more info

---

### Post by anglican on 2010-04-27
> **spiky001 said:**
> I have tried to find the answer to this, I use remote desktop which connects to my home server (on Lan) I have seen I can do it via ssh is this possible I need to be able to use network manager on remote machine, to start my mobile broadband conection, I hope this is clear if not I can give more info

Is [this]("http://vortex.brynmawr.edu/vnc/") what you need?

H

---

### Post by spiky001 on 2010-04-27
Not quite I,m not using windows, I know I can use ssh -X then start Nautilus to view files I wanna know if it's possible to do the same ssh -X then some how view desktop & control desktop

---

### Post by Iowan on 2010-04-27
Dunno if [this]("https://help.ubuntu.com/community/VNC") will help.  I remembered a topic, but it was VPN-SSH.

---

### Post by anglican on 2010-04-28
> **spiky001 said:**
> Not quite I,m not using windows, I know I can use ssh -X then start Nautilus to view files I wanna know if it's possible to do the same ssh -X then some how view desktop & control desktop

On the client computer:

ssh -L 5900:localhost:5900 user@somecomputer

Once you've logged into "somecomputer":

sudo apt-get install x11vnc :wink:
vncpasswd :wink:
x11vnc -q -ncache 10 -display :0 -usepw &

Then back on the client computer start your vnc client and connect to localhost:0.

H

---

### Post by KeyserSoze93 on 2010-04-28
Install x11vnc on your server, SSH in, and run:

```

x11vnc -shared -forever

```

On your client, install xtighvncviewer, and run:

```

xtightvncviewer -via me@my_server localhost

```

---

### Post by 2hot6ft2 on 2010-04-28
It can be done with SSH & Freenx. You can also VNC over it but I don't know any reason why you would want to since FreeNX is more secure and faster. And yes you can view and take control of the remote desktop. It's all in the guide below if you're interested.

---

