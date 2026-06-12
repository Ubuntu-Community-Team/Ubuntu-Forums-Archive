---
title: "nautilus sllllooooowwwww"
date: 2009-12-15
forum: General Help
---

### Post by burgechris on 2009-12-15
Ok....been dealing with this ever since I upgraded to Karmic (AMD64).  One of my profiles is having an issue with nautilus being extremely slow.  Part of this may be the amount of files in the general desktop that it opens to (a couple of hundred files) but this was never a problem before.  The other profiles have about 20-30 files max but are getting slower.

Anywho, when the profile loads, it takes forever because nautilus controls the desktop (at least I think).  I've resorted to using Thunar and Dolphin but is there a way to do one of the following. 

1) speed up/debug nautilus

or 

2) default to use Dolphin or Thunar as my file manager.

I really, really like nautilus (maybe it is the sick side of me...LOL) but the slowness is killing me.

Thanks,
Chris

---

### Post by philinux on 2009-12-15
Change from list mode to icon mode. Also try just using the default columns in list mode.

---

### Post by SlugSlug on 2009-12-15
I had this prob, do u have tweak ubuntu installed??  that maybe the cause - I think i fixed mine by adding the X PPA in software sources.

---

### Post by burgechris on 2009-12-15
Okay, Icon might be a little faster but it doesn't seem to be that much.  :(

---

### Post by burgechris on 2009-12-15
I did a search for tweak on Synaptic and it doesn't appear to be installed unless you are talking about something else.  :P

Thanks,
Chirs

---

### Post by SlugSlug on 2009-12-15
ubuntu-tweak is what I was on about -- if its not there then its not the issue with you

---

### Post by philinux on 2009-12-15
> **burgechris said:**
> Okay, Icon might be a little faster but it doesn't seem to be that much.  :(

Ok then try deleting the .thumbnails folder in your home folder.

---

### Post by burgechris on 2010-02-14
As a note, the nautilus slow issue disappeared about 5 days afterwards.  Thanks for all of the replies and sorry for taking so long in responding.  Holidays and a new birth threw me off for a while!  :)  

I do not know what fixed it except for maybe regular updates ?!?

---

### Post by kio_http on 2010-02-14
Try thunar the xfce file manager.

```
sudo apt-get install thunar
```

---

### Post by OliW on 2010-02-14
Turn off previews?

---

