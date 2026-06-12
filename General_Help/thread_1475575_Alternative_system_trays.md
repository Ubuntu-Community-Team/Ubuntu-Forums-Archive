---
title: "Alternative system trays"
date: 2010-05-07
forum: General Help
---

### Post by MedicineMan on 2010-05-07
In the search to customize my Ubuntu and Debian desktops, I've been looking for an alternative system tray instead of using 'Notification Area'.   

Are there any that you would recommend?  screenlets? AWN? 

Thank you for your help

---

### Post by MedicineMan on 2010-05-07
bump

---

### Post by blchinezu on 2010-05-07
If you don't use gnome-panel anymore than trayer is a good one. You can find it in the lucid repositories.

I've attached 2 screenshots so you cand see an overall preview on how it looks on the desktop and a close-up shot :)

The colors are a bit tarnished as I set a low opacity value with compiz.

---

### Post by MedicineMan on 2010-05-07
Yea, I'm trying to delete panels as much as possible.  I will check out that trayer, as it looks neat.  Do you have a custom config?

---

### Post by MedicineMan on 2010-05-07
I'm assuming you did something like:

```
trayer --edge right|bottom --widthtype request --heightype request
```

---

### Post by MedicineMan on 2010-05-07
If you could hook me up with a sample config/command of kinda what you did there, that would be awesome..  Thats exactly something i was looking for.

Thx again!

---

### Post by MedicineMan on 2010-05-07
Here's what I ended up using.  This is exactly what I wanted. 

```
trayer --edge bottom --align right --SetDockType true --widthtype request --heighttype request --transparent true --tint 0x000000 --alpha 255 &
```

---

### Post by MedicineMan on 2010-05-07
So I got trayer runnin' like a champ.  The thing i'm havin an issue with now, is that the sound applet is showing up in trayer, but'll show up in gnome-panel if i add 'indicator applet'.   Any ideas?

---

