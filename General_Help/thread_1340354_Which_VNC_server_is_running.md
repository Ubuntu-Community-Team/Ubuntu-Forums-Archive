---
title: "Which VNC server is running?"
date: 2009-11-28
forum: General Help
---

### Post by dabbi2000 on 2009-11-28
this may sound stupid but I'm lost...

I'm already connecting successfully to a local computer by vncviewer...

I want to configure the vnc server but cannot find out how because I don't know what vnc server is serving vncviewer on client computers, how to find out?

It's a standard Karmic koala setup...

---

### Post by aleb on 2009-12-24
What does this command print?
```
ps aux | grep vnc
```

---

### Post by bodhi.zazen on 2009-12-24
On an ubuntu desktop the VNC server is Vino

It is under System -> Preferances -> Remote desktop.

You connect the same as with any other VNC server.

See :

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

