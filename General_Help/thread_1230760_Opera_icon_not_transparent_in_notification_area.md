---
title: "Opera icon not transparent in notification area"
date: 2009-08-03
forum: General Help
---

### Post by dantata on 2009-08-03
Hey,

I have a problem with the Opera icon on my Xubuntu (jaunty). It is not transparent in the Notification Area:

[[IMG]http://img19.imageshack.us/img19/4724/operatam.th.jpg[/IMG]](http://img19.imageshack.us/i/operatam.jpg/)

I even tried installing KDE, to see if this would remedy the situation, but, sadly, it did not. Anyone got an idea how I can fix that?

Thanks.

---

### Post by physic.dude on 2009-08-03
hummm...
First of all, are you sure it's not selected (highlighted). Secondly, try to fiddle with the theme. Lastly, I am not sure how to change the icon, but you can find it and use GIMP to edit it to transparent. 
 
keep in mind that Ubuntu and all it's programs are in a beta state and the icon isn't always the developers first priority.

---

### Post by dantata on 2009-08-04
Thanks. The thing is that I can't locate the exact opera icon. I checked all icons in /usr/share/icons/hicolor. Tried modifying/deleting them - didn't work.

---

### Post by Menthu_Rae on 2009-08-25
You're not alone mate, I have the same issue under Ubuntu (gnome) 9.04 64-bit and 32-bit on seperate machines.

I have tried a number of builds of opera... sometimes the icon is fine, sometimes it isn't.

I've also tried replacing the opera tray icon in every place I could think of - but alas - no help!

So yeah - sorry this isn't a post telling you how to fix it - just letting you know that you're not alone in your plight.

I believe the changelog for a version a few weeks ago said it had fixed the issue - and it seems like they reverted that change... it may be worth us emailing opera with the relevant bug number:

> Reverted Fix to Bug DSK-243508 (Opera tray icon transparency issue in Qt4 builds with dark themes): Caused other issues. An alternative solution will be found.

[http://my.opera.com/desktopteam/blog/2009/08/20/more-snapshots](http://my.opera.com/desktopteam/blog/2009/08/20/more-snapshots)

---

### Post by dantata on 2009-08-25
Hey.

I recently installed 10.00 Beta 3 and the icon is now transparent.:)

---

### Post by Menthu_Rae on 2009-08-26
> **dantata said:**
> Hey.

I recently installed 10.00 Beta 3 and the icon is now transparent.:)

What build? (Help --> About Opera)

> Version
10.10 Beta

Build
4566

The above still has the issue for me. :(

---

### Post by TheNessus on 2009-08-26
I removed the icon from the notification area because it's not transparent. annoying thing.

---

### Post by dantata on 2009-08-31
The build is 4537. Also, it is the 64-bit version. It may be something else entirely, not the new version of Opera that fixed it. Strange.

Edit: Just updated to Opera 10, build 4585. There icon is new, and the problem is back! :/

---

### Post by Menthu_Rae on 2009-11-05
Just updating this,

With Version 10.10 Beta Build 4694 x86 the icon is *mostly* fixed. There is a small area where it is not transparent (at the bottom of the icon, about 3-4 pixels high and taking the whole icon width).

I'm yet to test under x64 (will do tomorrow). At least they're slowly fixing it ;)

---

### Post by dantata on 2009-11-05
> **Menthu_Rae said:**
> Just updating this,

With Version 10.10 Beta Build 4694 x86 the icon is *mostly* fixed. There is a small area where it is not transparent (at the bottom of the icon, about 3-4 pixels high and taking the whole icon width).

I'm yet to test under x64 (will do tomorrow). At least they're slowly fixing it ;)No change for me (x64, 4694).

---

### Post by Menthu_Rae on 2009-11-05
> **dantata said:**
> No change for me (x64, 4694).

Works fine for me under x64 4694 on 9.10 Karmic, sans the few pixels that are still grey (happens under x86 as per my post above)!

Perhaps **backup your .opera directory somewhere** then try an ```
apt-get remove --purge opera
``` followed by installing the new .deb?

---

### Post by Menthu_Rae on 2009-11-18
Good news everyone, it appears to be **fixed completely** in build 4728! Thank you to everyone at the Opera team! :) Yay!

```
Version
10.10

Build
4728

Platform
Linux

System
x86_64, 2.6.31-15-generic

Qt library
4.5.2

Java
Java Runtime Environment installed
```

---

### Post by dantata on 2009-11-18
Working correctly here as well:

> Version
10.10

Build
4728

Platform
Linux

System
x86_64, 2.6.31-15-generic

Qt library
4.5.2

---

