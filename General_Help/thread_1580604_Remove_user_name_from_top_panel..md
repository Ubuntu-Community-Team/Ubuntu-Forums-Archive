---
title: "Remove user name from top panel."
date: 2010-09-23
forum: General Help
---

### Post by yerayenrique on 2010-09-23
Hey there,

I would like to know if it's possible to remove the username button on the top panel in UNR10.04, which is very annoying as it works for a program I have already removed and takes up a considerable amount of space:

[[IMG]http://img801.imageshack.us/img801/7748/pantallazohz.png[/IMG]](http://img801.imageshack.us/i/pantallazohz.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Many thanks!

---

### Post by macem29 on 2010-09-23
right click on it and uncheck the lock to panel box, right click again and remove it

---

### Post by yerayenrique on 2010-09-23
> **macem29 said:**
> right click on it and uncheck the lock to panel box, right click again and remove it

I wish it was that simple, unfortunately, these options are disabled on UNR.

---

### Post by yerayenrique on 2010-09-29
Anybody?

---

### Post by hrickh on 2010-09-29
gconftool -s /system/indicator/me/display --type int 0 - For no name

or, to completely remove, uninstall indicator-me (this will remove the ability to change your instant message status - it does no harm in removing it, you just won't have that ability any more).

R.
==

---

### Post by yerayenrique on 2010-09-29
> **hrickh said:**
> gconftool -s /system/indicator/me/display --type int 0 - For no name

or, to completely remove, uninstall indicator-me (this will remove the ability to change your instant message status - it does no harm in removing it, you just won't have that ability any more).

R.
==

So if I do "gconftool -s /system/indicator/me/display --type int 0" I will remove the status button (name and icon to the left) without uninstalling the program? I didn't quite get it.

---

### Post by kerry_s on 2010-09-29
i uninstall indicator-me, log out & back in.

---

### Post by hrickh on 2010-09-29
> **yerayenrique said:**
> So if I do "gconftool -s /system/indicator/me/display --type int 0" I will remove the status button (name and icon to the left) without uninstalling the program? I didn't quite get it.
The best way to illustrate the changes is to actually do them (there's really no harm in changing it - it can easily be changed back).

First try the number "0", then try "1" and finally try "2" to see the differences. It will become clear what each number does. I'm really not trying to be obtuse. Try all three options to see the differences.

R.
==

---

### Post by kerry_s on 2010-09-29
> **hrickh said:**
> The best way to illustrate the changes is to actually do them (there's really no harm in changing it - it can easily be changed back).

First try the number "0", then try "1" and finally try "2" to see the differences. It will become clear what each number does. I'm really not trying to be obtuse. Try all three options to see the differences.

R.
==

it has to be there to actually work. :lolflag:
there is no system-> indicator
(second pic: find-> indicator)

---

### Post by yerayenrique on 2010-09-30
> **yerayenrique said:**
> So if I do "gconftool -s /system/indicator/me/display --type int 0" I will remove the status button (name and icon to the left) without uninstalling the program? I didn't quite get it.

Awesome, simply removing indicator-me worked a charm!

Thanks.

---

### Post by Chareos on 2010-10-11
I'd just wish an option to remove the name, keeping the icon !

---

