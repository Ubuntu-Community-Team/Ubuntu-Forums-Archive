---
title: "compiz causes changing background extremely slow"
date: 2011-08-12
forum: General Help
---

### Post by hyfanious on 2011-08-12
I use "Desktop Drapes" to change my backgrounds frequently
I use compiz also
I considered that compiz causes changing background extremely slow
how can I fix this?

---

### Post by sahabcse on 2011-08-12
Try to do the following in xorg.conf

"sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf. 

Regards
Sahab

---

### Post by hyfanious on 2011-08-12
> **sahabcse said:**
> Try to do the following in xorg.conf

"sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf. 

Regards
Sahab
  
```
sudo gedit /etc/X11/xorg.conf
``` opens an empty file
and as a matter of fact I have not such file in my system ! :(

---

### Post by sahabcse on 2011-08-12
please let me know your ubuntu version

---

### Post by hyfanious on 2011-08-12
> **sahabcse said:**
> please let me know your ubuntu version
10.04 lucid LTS that is written in my side bar information ;)

---

### Post by sahabcse on 2011-08-12
Please have a look on 

/usr/share/X11/xorg.conf.d

---

### Post by hyfanious on 2011-08-12
> **sahabcse said:**
> Please have a look on 

/usr/share/X11/xorg.conf.d

just same
I guess I saw this file somewhere before
But I can't recall where now
I am looking for

---

### Post by hyfanious on 2011-08-12
I found somthing
but it is a directory not a file
and these are its contents:
```
05-evdev.conf  10-synaptics.conf  10-vmmouse.conf  10-wacom.conf

```

---

### Post by hyfanious on 2011-08-12
any other suggestion?

---

### Post by CatKiller on 2011-08-12
It's not Compiz that does it. The transition animation is just poorly executed. It got better in subsequent releases. TBH, having Compiz draw the desktop rather than Nautilus might perform better, although I never tried it; as I understand it, not using Nautilus means that you don't get Desktop icons.

xorg.conf stopped being created by default a while ago in favour of the automatic methods. It will still be used if it's there, though. There are plenty of posts with a minimal skeletal xorg.conf around.

EDIT: You should use gksudo for graphical applications. It doesn't make much difference with gedit, but it's a good habit to get into.

---

### Post by hyfanious on 2011-08-12
> **CatKiller said:**
> It's not Compiz that does it. The transition animation is just poorly executed. It got better in subsequent releases. TBH, having Compiz draw the desktop rather than Nautilus might perform better, although I never tried it; as I understand it, not using Nautilus means that you don't get Desktop icons.

but when I set compiz off transition animation works fine
what do u mean by "having Compiz draw the desktop rather than Nautilus might perform better"?
and at last creating xorg.conf can help me or not?

---

### Post by hyfanious on 2011-08-12
how do I fix this?

---

### Post by CatKiller on 2011-08-12
> **hyfanious said:**
> but when I set compiz off transition animation works fine
what do u mean by "having Compiz draw the desktop rather than Nautilus might perform better"?
and at last creating xorg.conf can help me or not?

That's interesting. When I was on Hardy, turning off Compiz made no difference at all.

Compiz has the option to draw your Desktop wallpaper. It lets you have different wallpaper on each workspace, and so on. Because it's all accelerated it's possible that out might work better. As I said, I haven't tried it. I just stopped changing wallpaper until sometime after it had been fixed.

I have no idea if changing your xorg.conf will help. I'm not familiar with the option you were given and I'm on my phone so it's not like I can check.

It's not polite to bump your thread more than once a day.

---

