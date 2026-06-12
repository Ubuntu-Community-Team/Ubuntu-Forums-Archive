---
title: "GIMP not working......due to n00b foulup"
date: 2010-10-06
forum: General Help
---

### Post by jeddycakes on 2010-10-06
Just recently I tried to install something that would run GIMP in full screen rather than lots of little windows. It didn't work and now I have a problem. 
GIMP  2.7.1 will not run on my machine. During the above process (i.e. the  full window thing) I installed a previous version of GIMP, 2.2 as that was what was suggested. I wish I effin' hadn't as that version is stuck like a plague to  my computer.

I ```
sudo apt-get remove gimp
``` and ```
sudo apt-get install gimp
``` to no avail.

I even tried through the software centre.
Any shortcuts I try to run just....hang and then do nothing. When I AltF2 all I get is the crappy old version!
I don't know how to:-
A) Find out where GIMP2.2 is installed,
B) Remove that shizzle.

Its really quite annoying!
Any help would be greatly appreciated. I'll buy beer etc

---

### Post by andrewthomas on 2010-10-06
> **jeddycakes said:**
> During the above process (i.e. the  full window thing) I installed a previous version of GIMP, 2.2 as that was what was suggested. I wish I effin' hadn't as that version is stuck like a plague to  my computer.


How did you install GIMP 2.2?

Was it a .deb?

Where did you get it from?

---

### Post by jeddycakes on 2010-10-06
> **andrewthomas said:**
> How did you install GIMP 2.2?

Was it a .deb?

Where did you get it from?

I got it from [[COLOR="Red"]here[/COLOR]]("http://www.gimpshop.com/download.shtml") and it was a .deb.

[[COLOR="Red"]This[/COLOR]]("http://www.novell.com/coolsolutions/feature/16475.html") was the guide (I'm pretty sure) that I referenced when installing.

I'll admit that I had a few ales as I was doing this lol, so I perhaps wasn't paying as much attention  as I should have been.

EDIT: looking at it, that guide is pretty much completely the wrong thing I should have been looking at :/ 

Cheers for the reply!

---

### Post by andrewthomas on 2010-10-06
post the output of 
```

aptitude show gimpshop
```

---

### Post by jeddycakes on 2010-10-06
```
jed@jeddy-cakes:~$ sudo aptitude show gimpshop
Package: gimpshop
New: yes
State: installed
Automatically installed: no
Version: 2.2.11-1
Priority: extra
Section: checkinstall
Maintainer: giuliastro
Uncompressed Size: 38.5M
Description: GimpShop package

```

Will removing this solve my problem? I feel I need to tread carefully here lol

---

### Post by andrewthomas on 2010-10-06
```
sudo aptitude purge gimpshop && sudo aptitude update && sudo aptitude install gimp
```

post the output of any errors.

---

### Post by jeddycakes on 2010-10-06
Legend....worked perfectly,thanks.

Never shall I drink and Ubuntu. We can all learn from this.

:guitar:

---

### Post by andrewthomas on 2010-10-06
If it is all good. Please mark the thread as [SOLVED]

---

### Post by SeijiSensei on 2010-10-06
You might want to try using the multiple desktops feature in GNOME and KDE to put GIMP on a desktop by itself.  While it won't look like Photoshop, at least it will all be consolidated in one place.

---

