---
title: "No Sound, On Xubuntu"
date: 2012-02-10
forum: General Help
---

### Post by archx on 2012-02-10
so i recently installed xubuntu but no sound, i tried going into the alsamixer and it looks like this:

[http://imgnow.tk/u/62870113.png](http://imgnow.tk/u/62870113.png)


I think i have no volumne because it is set to '00' but arrow keys dont allow me to change, they do nothing. Can anyone help me with this???

---

### Post by Rodney9 on 2012-02-10
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Rodney

---

### Post by ajgreeny on 2012-02-10
I think the latest version of xubuntu uses pulseaudio, but doesn't include **pavucontrol** package, which I think is needed to configure pa properly.

Try installing it with synaptic or apt-get and then open pulseaudio volume control from the sound & video menu and play around with that for a while;  it may get your sound working properly.

---

