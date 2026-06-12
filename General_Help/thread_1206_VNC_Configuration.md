---
title: "VNC Configuration"
date: 2004-10-19
forum: General Help
---

### Post by thebigfatgeek on 2004-10-19
I have Ubuntu installed as a standalone webserver, hidden in a dark closet somewhere. I configured it for remote VNC access from my normal house PC (XP) and need to be able to get to it with VNC. It used to work but recently just gives me a connection timeout error. It is in a DMZ to test, so it is not a port issue I think.

I can login using SSH so should be able to connect and configure VNC again via that route, but I have no idea how to start (newbie)

Can anyone help?

Regards

Pieter

---

### Post by homerhomer on 2004-10-19
make sure that vnc is not asking for permisson on the box

I know that by default that vino does this. to change go to command prompt and type : sudo vino-preferences  


Good luck

---

