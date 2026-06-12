---
title: "pptview on projector"
date: 2010-10-21
forum: General Help
---

### Post by cannywizard on 2010-10-21
I'm using pptview from the repositories to show a powerpoint file, but when I'm connected to a projector, it insists on showing the show on my laptop screen rather than the projector.

Anyone know how to fix this?

---

### Post by cannywizard on 2010-10-22
Well, I fixed it myself, but for the next guy,

Install Devils pie - an application that allows you to define where windows appear when they open - [http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)
```
sudo apt-get install devilspie
```
Add a script pptview.ds in ~/.devilspie (there are some tips on how to write them on that web page)
Mine looks like
```
(if (contains (application_name) "PowerPoint Viewer" )  (geometry "1280x1024+1440+0") debug )
```start devilspie
```
devilspie
```and tada - works

---

