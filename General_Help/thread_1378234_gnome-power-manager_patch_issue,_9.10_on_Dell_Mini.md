---
title: "gnome-power-manager patch issue, 9.10 on Dell Mini 10v"
date: 2010-01-11
forum: General Help
---

### Post by inigopete on 2010-01-11
I'm running Karmic on a Dell Mini 10v (Intel Atom) netbook, generally with very few problems and I've been happy with it.

Recently I've had problems with suspend and wake when I close / open the lid - wicd no longer finding any networks, password prompt no longer appears, that sort of thing. A few days ago an icon popped up in the panel which appeared to do nothing, but mousing over it provided the following message:

"Session active, not inhibited, screen idle. If you can see this text, your display server is broken and you should notify your distributor. Please see [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/) for more information."

Following the link, the blog of Richard Hughes appears to quite carefully describe the issue and then provides a patch (or two).

However, being rather a n00b I have no idea what to do with either of the blocks of code he supplies - "man patch" in my terminal brings up "no manual entry for patch".

I know I've posted this in General Help, could someone please give me a few pointers on what I need to do?

Thanks.

---

### Post by inigopete on 2010-01-14
...anyone?

---

### Post by Coward on 2010-02-20
You probably don't have patch installed. Type this if you want to get it:

sudo apt-get install patch

Patch simply changes lines in a text file, adding lines which have a "+" in front and removing the lines with a "-" in front. This means you'd be editing your own copy of the source code. So you have to find the source code first. Finally you have to compile it. I wish I could be more helpful but I'm not an expert myself.

---

### Post by JoeFriday49 on 2010-03-06
Got this message for the first time this morning:     	 	 	 	 	 	  [FONT=DejaVu Sans, sans-serif]Session active, not inhibited, screen idle. If you can see this text, your display server is broken and you should notify your distributor. Please see [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/) for more information.&#8221; 
[/FONT]


[FONT=DejaVu Sans, sans-serif]Been using this Acer laptop for several months...  Will be watching your thread for more advice...
[/FONT]

---

