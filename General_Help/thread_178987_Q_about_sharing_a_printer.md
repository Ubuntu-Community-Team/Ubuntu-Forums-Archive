---
title: "Q about sharing a printer"
date: 2006-05-18
forum: General Help
---

### Post by l1ght on 2006-05-18
Just got ubuntu installed as a second OS on one of my computers and all went well. The computer that it is on is connect to my printer, which needs to be shared with another computer on the network, one with windows xp on it. I was able install the printer in linux just fine, but the xp machine is not finding it on the network.

So my question is, how can I share the printer attached to my linux computer with the windows one? It is possible, right?


Thanks for your help!

[SIZE="1"]Hopefully this is the right forum to put this in, if not, please move it.[/SIZE]

---

### Post by dachelb on 2006-05-19
If the printer is working on Linux you're halfway there.  The other piece you will need is to configure your linux box as a samba server.  This will allow you to share the printer across the network. 

Once you've installed the samba stuff you may want to track down webmin - it's a web interface that will allow you to configure (among other things) your samba server configuration.  

Configuring a samba server can range from trivial to difficult.  [http://www.samba.org](http://www.samba.org).

---

