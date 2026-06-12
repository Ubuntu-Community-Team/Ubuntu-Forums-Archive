---
title: "GUI Messed Up"
date: 2006-04-11
forum: General Help
---

### Post by matchboxfiend on 2006-04-11
Hello!

I'm fairly new to Ubuntu 5.10 (been using Linux for a bit longer but on Fedora Core 5) and I love it!  THe features are excellent and the usability is friendly.  I have run into a problem that isn't making too much trouble but I would like to fix.  For some reason the overall GUI of my desktop gets strange lines running down it and the toolbars get distorted with image corruption.  Big black rectangles and the lot.  

I'm running a Compaq Presario SR1403WM with what I believe to be a built in SiS760 graphics thingy.  I'm really not all that knowledgable in Computer Guts and I got this computer at Wal-Mart so I expect a certain level of crapiness.  ;) 

Anyway, has this probelm occured before and if so, is there a way to fix it?  I currently have a blue line running across my screen and it's highly annoying. :mad:

---

### Post by greenstar on 2006-04-11
If you have a cheap or old monitor, you may need to set custom HorizontalSync & VertRefresh rates in /etc/X11/xorg.conf

For instructions see this post:
[http://www.ubuntuforums.org/showpost.php?p=910338&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=910338&postcount=2")

Read down to here:
**Refer to my xorg.conf below. The parts which are important here will be highlighted in [COLOR=Red]red[/COLOR]**[B].

[/B]Then skip to this part:
[B]If your monitor picture is looking like scribbles going back and forth across your screen, try this:

[/B]Be sure to save a backup of your xorg.conf file before editing so it will be easier to recover if this doesn't correct your problem or makes it worse.

Hope this helps.

Greenstar

---

