---
title: "Gnome 3 (Gnome-Shell) window raise behaviour"
date: 2012-06-11
forum: General Help
---

### Post by zcacogp on 2012-06-11
Chaps, 

Is it possible to configure Gnome 3 (Gnome-Shell) such that the focus is sloppy (i.e. the window under the mouse is focussed), but it only raises on a click on the window title bar? 

I can (easily) configure it such that it does sloppy focus, but the window raises whenever I click anywhere in it. I particularly only want it to raise if the title bar is clicked on. Is this possible? 

(Also - an aside - what's the difference between "Sloppy Focus" and "Mouse Focus"?) 

Thanks, in advance, for any help. 


Oli

---

### Post by zcacogp on 2012-06-14
Anyone? 

All help welcomed - thank you. 


Oli.

---

### Post by zcacogp on 2012-06-14
OK, I think I may have solved this one. 

You can make gnome-shell run with sloppy focus and only raise a window when the titlebar is clicked on (as opposed to raising when any part of the window is clicked in.) For me, this is very good news as it is precisely the way that I want the machine to run ... 

Install dconf-editor, using: 

# sudo apt-get install dconf-tools

Then run it using 

# dconf-editor

Navigate to org / gnome / desktop / wm / preferences, and turn off "Auto-raise" and also turn off "Raise-on-click". This last setting has some pretty dire warnings attached to it, and I will wait and see what terrible calamity I bring upon myself by setting it ... !


Oli.

---

### Post by ngolian on 2012-08-07
Thanks for posting about the location of the option, I couldn't find it myself.

Assuming the "buggy behaviour" is also inherited from metacity, it mainly consists of it trying to hide new windows behind existing ones, it's not as bad as raise on click. I'll stop now or it will just be a rant against GNOME being sabotaged by its own developers in an attempt to make points that have already been proven wrong.

---

### Post by ArgAthens on 2013-02-04
Thanks for posting this, this is exactly what I was looking for!

---

