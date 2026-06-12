---
title: "FreeNX server"
date: 2010-12-19
forum: General Help
---

### Post by spiky001 on 2010-12-19
Ok I have been using the built in remote Desktop, I have been thinking about installing Freenx, 1 Q dose it run on it,s own like the 1  I have been using OR dose it have to run via ssh?

---

### Post by spiky001 on 2010-12-19
Ok abit of a bump and added info I have ssh installed Then I tunnel vnc through ssh, I would like toknow if Freenx needs me to ssh in and make a tunnel or will it take care of all that itself hope someone understands this

---

### Post by spiky001 on 2010-12-24
Ok I would like some help setting up freenx server I have a few Q I need answering if some one has some time, port number etc

---

### Post by veggen on 2010-12-24
Dude. There's no way anyone will ever bother to read your illiterate posts. Write like a human being and not like a lolcat and someone might even help you.

---

### Post by Grenage on 2010-12-24
> **veggen said:**
> Dude. There's no way anyone will ever bother to read your illiterate posts. Write like a human being and not like a lolcat and someone might even help you.

That's a bit harsh; true, but still.

> **spiky001 said:**
> Ok abit of a bump and added info I have ssh installed Then I tunnel vnc through ssh, I would like toknow if Freenx needs me to ssh in and make a tunnel or will it take care of all that itself hope someone understands this

NX will make use of ssh, so you don't need to manually connect first.  The default port will be 22, unless you changed it.

---

### Post by spiky001 on 2010-12-24
Ok where i,m at, I have the Graphical interface for x11vnc it is asking for a port number, default is 5901, I would like to change this any advice. Ssh has been reasigened a different port number, Do I set port on x11 to that port or one of it,s own, at the moment I,m only using internal lan, But I expect I will need to access it form internet side.

---

### Post by pricetech on 2010-12-24
I've never used freenx, so I can't help you with that specifically, but I have used NX from nomachine dot com and I can tell you that setting it up is a piece of cake.

SSH and VNC are "apples and orange" so there's no relation between them unless you previously set up VNC to run over SSH.

Your SSH port is determined by the configuration file and you'll need to modify both "node.cfg" and "server.cfg" for NX so it uses the same port number.

Don't forget to back up the original files before editing.

and yes you'll get more and better responses by dropping the text / lol lingo.

---

### Post by spiky001 on 2010-12-24
I have set the nxserver conf file port to the same as ssh, but I,m still unable to connect even over localhost. I,m using vncviewer to view remote desktop, I used ```
vncviewer localhost
``` I must of messed up some settings along the way.

I have not set any passwords yet or touched any keys for freenx

---

