---
title: "Collaborative editing set up the easy way (gedit, infinote)"
date: 2011-04-21
forum: General Help
---

### Post by aaaaalex on 2011-04-21
After reading about a [plugin for collaborative editing for Gedit]("http://www.tendenciadigital.com.ar/english/linux-open-source/how-to-set-up-and-use-gedit-collaboration-plugin-with-infinoted-server.html") and actually finding a [PPA]("https://launchpad.net/~pspsampsp/+archive/gedit-plugin-collaboration") that already provides the plugin I decided to make a little script that eases the fiddling about with the set up. This is intended to be able to quickly fire up a collaborative editing session. Once you punch a hole into your router for infinotes port you can code away with your friends around the globe. 

It will install and set up the infinote server (optional) and the plugin to Gedit - as an alternative you can of course use gobby. The server can then be started and stopped via Unity's Dash - I don't need it running all the time. 

The Script can be found [here]("http://www.aykay.info/infinoted/install_infinoted.sh").

Here is how to run it:
```
wget http://www.aykay.info/infinoted/install_infinoted.sh
chmod +x install_infinoted.sh
./install_infinoted.sh
```

Enjoy :D

---

