---
title: "How can I get rid of the extra bar near screen top?"
date: 2012-05-24
forum: General Help
---

### Post by RogerDavis on 2012-05-24
Ubuntu 12.04

How can I get rid of the extra bar near screen top?

The one that wastes screen space is the one that stupidly announces what app I'm in... as if no one knew!

---

### Post by Dennis N on 2012-05-24
Sounds like you are talking about the Unity panel. If so, the answer is you can't and still use the Unity desktop. You could use another desktop environment - LXDE or XFCE for example. In those, panels can be added, moved, or deleted.

---

### Post by jocko on 2012-05-24
> **RogerDavis said:**
> Ubuntu 12.04

How can I get rid of the extra bar near screen top?

The one that wastes screen space is the one that stupidly announces what app I'm in... as if no one knew!
Wastes space, how? In other DEs every application have it's own menu bar on top of the window, in unity they all share the one single fixed menu bar at the top of the screen. Either you add a menu bar at the top of the window, wasting some of the space that could be used for the content of the window, or you add a fixed bar at the top of the screen that will hold all application menus, wasting some of the space you could use for making a window taller. Either way there is exactly the same space available for the actual window content...

---

### Post by raja.genupula on 2012-05-24
a picture can explain better . so try to capture with screenshot .

---

### Post by MadmanRB on 2012-05-24
Yeah I dont get it either, the top panel is far from an issue (though the launcher is a different story)

---

### Post by RogerDavis on 2012-05-24
I can't do screenshots right now, I'm getting ready to travel asap.  But to see what I mean, start Firefox.  Look right above the File Edit View History Etc..  That whole line just says where I am, just like the Navigation Bar two lines down - like deja vu all over again.  Might as well have two Launchers...  Only I don't have to worry about that one any more.

BTW, I'm using Gnome, but I don't think it makes a difference.  I'm done with disUnity !!!

Thanks!

---

### Post by DavidSommen on 2012-05-24
> **RogerDavis said:**
> I can't do screenshots right now, I'm getting ready to travel asap.  But to see what I mean, start Firefox.  Look right above the File Edit View History Etc..  That whole line just says where I am, just like the Navigation Bar two lines down - like deja vu all over again.  Might as well have two Launchers...  Only I don't have to worry about that one any more.

BTW, I'm using Gnome, but I don't think it makes a difference.  I'm done with disUnity !!!

Thanks!
Normally there is nothing right 'above' File edit view history etc... so please do post a screenshot when you have the time, something's not right.

---

### Post by josephmills on 2012-05-24
```
sudo apt-get build-dep unity
```
```
bzr branch lp:unity
```
alter the "panel" and what ever else you want.
and compile
then push and merge a request too developers so they can see what you are talking about.

---

### Post by MadmanRB on 2012-05-24
> **RogerDavis said:**
> 

BTW, I'm using Gnome

Are you using gnome shell or classic?
If classic you are in luck, win key(super)+alt and right click will help you remove non needed panels and app apps into the panel you want to keep

---

