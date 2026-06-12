---
title: "A update I don't need"
date: 2006-04-19
forum: General Help
---

### Post by megahertza on 2006-04-19
I checked update manager today and 3 new updates where available. 1 was the the 1.0.8 firefox update. I've installed the 1.5.x firefox. Can i prevent this new update from showing up in the update manager

---

### Post by 5-HT on 2006-04-19
[quote=megahertza]I checked update manager today and 3 new updates where available. 1 was the the 1.0.8 firefox update. I've installed the 1.5.x firefox. Can i prevent this new update from showing up in the update manager[/quote] 
If you don't want to update 1.0.7 to 1.0.8: Open synaptic, highlight 1.0.7, go to the 'Package tab', and select 'Lock Version'.

---

### Post by megahertza on 2006-04-19
Thanks dude, worked fine

---

### Post by dmizer on 2006-04-19
this did not work for me.  i went through and marked everything firefox related in my synaptec and still apt-get upgrade is showing:
```
dmizer@injapan:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  firefox firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
what am i missing?

just in case you think i'm absolutely daft ... here's a shot of my synaptic:

---

### Post by dcstar on 2006-04-20
[QUOTE=megahertza]I checked update manager today and 3 new updates where available. 1 was the the 1.0.8 firefox update. I've installed the 1.5.x firefox. Can i prevent this new update from showing up in the update manager[/QUOTE]
Ubuntu Breezy still uses Firefox 1.0.x core components for various functions, if these updates have security or bug fixes you could have a more stable system if you install them.

If you don't mind a little data traffic, install them.

---

### Post by OffHand on 2006-04-20
The updates shouldn't mess up your 1.50.x. 
I had no problems whatsoever. You might want to backup your bookmarks etc
just in case.

---

### Post by Jagot on 2006-04-20
I updated from 1.0.7 to 1.0.8 despite having 1.5.0.2 installed.  It all worked fine and 1.0.8 did not take over.  Only thing that happened was that my lovely Firefox icon changed back to the default Ubuntu one but that was easily solved.  I agree with dcstar with regards to other parts of Ubuntu utilising components of FF, hence why I went ahead with it.

---

