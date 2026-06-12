---
title: "Gnome menu question"
date: 2010-06-07
forum: General Help
---

### Post by TheWeakSleep on 2010-06-07
Okay, so i was doing a little bit of cleaning in the main menu, and i removed the default sub-menus under applications. You know, "Internet", "Sound & Video", etc etc. 
My issue is now that theyre gone, anything new that I install doesn't show up in the menu anymore! I tried re-creating the sub-menus, but that didn't help, at least as far as the packages i tested.

I guess what I'm asking is if theres a way to change the default location that applications appear when theyre installed? or do i have to search for everything D:

thanks guys :)

---

### Post by retry32 on 2010-06-07
Well you did a dumb action...
But to make shortcuts you need to do Right mouse click on your desktop > New starter > (Your app)

---

### Post by TheWeakSleep on 2010-06-07
I don't really see how it's dumb. I know how to create a launcher, i was just wondering if there was a way to get it so i dont have to.

---

### Post by WorMzy on 2010-06-07
Try renaming (or deleting, if you prefer) ~/.config/menus and ~/.local/share/desktop-directories. These folders determine the content of your menus. If you want to retain some changes, but undo others, then just examine the contents and make the changes as necessary.

You may need to log out and back in for the changes to take effect.

---

### Post by SlidingHorn on 2010-06-07
> **retry32 said:**
> Well you did a dumb action...
But to make shortcuts you need to do Right mouse click on your desktop > New starter > (Your app)

Telling posters that what they've done is "dumb" is hardly constructive.  

As for the OP, AFAIK, you would have to create the launchers manually.  Someone can feel free to come in and prove me wrong

---

### Post by Barafu Albino Cheetah on 2010-06-07
Recreate menu directories as shown above. 
Nex time to remove something from gnome menu, just check it out in alakarte. Try to do as little changes as possible, because alacarte is as solid as a jelly tower.

---

### Post by TheWeakSleep on 2010-06-07
thanks for the replys guys :) theres over 100 entries in ~/.config/menus so I'll have to sift through those. Otherwise, I'll just be stuck making launchers. But I appreciate the point in the right direction :)

---

