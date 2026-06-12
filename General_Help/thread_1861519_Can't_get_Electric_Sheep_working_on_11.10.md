---
title: "Can't get Electric Sheep working on 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Niva on 2011-10-15
I just went through the mess of installing the xscreensavers but for some reason Electric Sheep is not showing up in the menu where I can select which screensaver I want working.

Can someone post a complete instruction on how to enable electric sheep in oneric please?

---

### Post by trukker on 2011-10-16
Same here :-(

---

### Post by Niva on 2011-10-16
Well I still haven't been able to resolve this issue, I might have to resort to some hackery soon.  However, I did find out Electric Sheep is available for windows and mac too.  Love that screensaver.

---

### Post by Niva on 2011-10-16
OK found an answer here:

[http://askubuntu.com/questions/61305/electricsheep-screensaver-wont-start](http://askubuntu.com/questions/61305/electricsheep-screensaver-wont-start)

This is along the lines I was thinking after everything was installed.

from terminal > gedit ~/.xscreensaver

Add the following line to the bottom of the list of screensavers.  Make sure that it has **--root 1** which looks a bit out of place.

GL: electricsheep --root 1 \n\

You can then select it from the list and configure it appropriately.  Good luck!

---

### Post by faldrich on 2011-10-26
This probably works for a standard call to the screen saver.  But, what about "lock screen"?   I've grown used to using electricsheep for that -- and it appears I no longer can with 11.10.   

Or, is there a way to fix that?


Thanks.

---

### Post by Niva on 2011-11-09
Faldrich I'm not sure if you got your issue resolved.  Electric sheep is just a screensaver app which is accessible through xscreensaver as configured on my machine.  Through the xscreensaver controls you can specify if you want to lock the screen when the screensaver kicks in.  

I'm not sure though you might be talking something else.  Good luck.

---

### Post by dik909 on 2011-11-09
the key is to open ~/.xscreensaver (gedit ~/.xscreensaver) 

at the bottom of the screensaver's list you'll have to add: 

GL: electricsheep --root 1 \n\ 

otherwise you'll not be able to see it in xscreensaver

---

### Post by scristopher on 2012-01-05
ive tried this but upon starting xscreensaver-demo it overwrites my file killing the line i just added, would be awesome to be able to use

---

### Post by frytek on 2012-03-19
> **scristopher said:**
> ive tried this but upon starting xscreensaver-demo it overwrites my file killing the line i just added, would be awesome to be able to use

are you sure you are using pure, real xscreensaver? not gnome/kde built-in screensavers which only use xscreensaver modules (ssavers) but are just a part of gnome/kde environment? 

i tried the above solution on xubuntu 11.10 which uses real xscreensaver and it worked.

---

