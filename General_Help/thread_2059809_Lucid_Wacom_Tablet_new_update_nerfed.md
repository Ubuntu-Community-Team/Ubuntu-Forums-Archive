---
title: "Lucid Wacom Tablet new update nerfed"
date: 2012-09-18
forum: General Help
---

### Post by Holotype on 2012-09-18
Hello, I still use 10.04, because I can only get certain scientific programs to run on Lucid. My problem is that after an update a few days ago, my Wacom tablet no longer functions correctly.

[LIST]
Cursor sticks for 5+ seconds after writing
pressure sensitivity is not working
eraser and other 2 buttons on stylus are not working
[/LIST]

After reading about a million forums on the topic and trying everything, I am unable to fix my Wacom tablet (CTE-450). I'm a total noob, but I configured my xorg file initially and everything worked fine. It's just after this update a few days ago that I've had problems. 

What information do you need in order to help me? I can post it. Any help would be greatly appreciated.

---

### Post by arsenic23 on 2012-09-18
Okay, before you do anything I would get a copy of the log for your last update.  Are you using apt or one of the GUI updates that uses it?  Then:
```
tail /var/log/apt/history.log
```

You should see a list of all the packages updated the last go around (hopefully).

After that you need to make sure we know what package is causing the problem.  Hopefully it is something simple like the wacom driver [xserver-xorg-input-wacom].  If it isn't you'll need to figure out what package it is before you try anything else.

If that is it you can look and see if the older packages are available (they should be).  ```
apt-cache showpkg xserver-xorg-input-waom
```

At the bottom of that you should see something like "*Provides:*" and then a bunch of version numbers.  Just go with the 2nd newest version number; copy that down.  Then install that version and lock/pin it.  Depending on what package manager you use the process will be different, so I suggest googling the specifics from there or posting them in this thread.

EDIT:  If you are wondering how to install a specific version of an application with apt-get it's:
```
apt-get install pkg=version
```So it would look something like this if you need to do it for the above wacom package:```
apt-get install xserver-xorg-input-waom=1:0.14.0-0ubuntu2
```

---

### Post by Favux on 2012-09-18
Hi Holotype,	

Welcome to Ubuntu forums!


arsenic23's advice is good but you might want to quick check if the Wacom usb kernel driver is still auto-loading.  Enter in a terminal:
```
lsmod |grep wacom
```
Do you see **wacom** in the output?

---

### Post by Holotype on 2012-09-19
Thank you arsenic23 and Favux. Downgrading worked perfectly. I just wish I would have posted here earlier.

---

### Post by Holotype on 2012-09-19
By the way, you mentioned something about locking/pinning that version. How do I do that? It would be nice to be able to use the update manager without scrutinizing every single update.

---

### Post by arsenic23 on 2012-09-19
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Go down to *Introduction to Holding Pacakges*.   I never use the GUI package managers so I don't even know what the default is in ubuntu anymore.  Is it still synaptic?

---

