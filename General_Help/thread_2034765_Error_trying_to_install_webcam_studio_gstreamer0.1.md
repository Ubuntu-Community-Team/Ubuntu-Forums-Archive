---
title: "Error trying to install webcam studio: gstreamer0.10-plugins-ugly-multiverse"
date: 2012-07-29
forum: General Help
---

### Post by MonopolyMan on 2012-07-29
Ok so when I try to install WebCamStudio (From a .deb) I get the following error: 

```
Dependency is not satisfiable: gstreamer0.10-plugins-ugly-multiverse
```

Then when I try to install gstreamer0.10-plugins-ugly-multiverse_0.10.14-0ubuntu2_i386.deb it gives me this error. 


```
Breaks existing pacakge 'gstreamer0.10-plugins-ugly' that conflict: 'gstreamer0.10-lame'. But the '/home/joey/downloads/gstreamer0.10-plugins-ugly-multiverse_0.10.14-0ubuntu2_i386.deb'provides is via 'gstreaer0.10-lame'
```

Does anyone have a solution to either error?


P.s This is my first post on this site, I hope to come by more often with more help ;) But for now I just have some questions since I just installed Ubuntu

---

### Post by ric1321 on 2012-08-25
same problem for me dude.

---

### Post by mzaam on 2012-08-25
u may use third party repository to install that software easily,
add getdeb to your repo  list, this is how:
[http://www.getdeb.net/updates/Ubuntu/11.10#how_to_install](http://www.getdeb.net/updates/Ubuntu/11.10#how_to_install)

then install your sftware from anything you like (software-center, synaptic, apt-get, etc)

---

