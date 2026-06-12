---
title: "Start Nautilus in Split-Pane mode"
date: 2010-07-05
forum: General Help
---

### Post by wearyroad on 2010-07-05
Is there a way to start nautilus already set in split-pane mode, every time you open a new nautilus window?

---

### Post by Elfy on 2010-07-05
Last time I looked into this I got this far, nothing appears to have changed so I would guess not at the moment.

[http://ubuntuforums.org/showthread.php?t=1435333](http://ubuntuforums.org/showthread.php?t=1435333)
[https://bugzilla.gnome.org/show_bug.cgi?id=608431](https://bugzilla.gnome.org/show_bug.cgi?id=608431)

---

### Post by veggen on 2010-07-05
Sadly, no. There simply is no way to do that. Lame.

---

### Post by oOarthurOo on 2010-11-26
I wanted to do this myself, and came across a launchpad bug that got me started in the right direction, so I thought I'd post the solution here as well. 

It's true that there's no built-in solution, however a workaround is fairly trivial and works pretty good depending on how closely you time it (via the sleep number).

xsendkeys is what we use to send a fake keypress, and it's found in the lineakd package. At least, it is on Debian and I hope things are still similar enough between the two distros that this will be helpful. ;)
```
sudo apt-get install lineakd
```

Now we create a script to do the work, and put in somewhere sane.
```
sudo nano /usr/bin/nautilus_split-view
```
Copy and paste this into the script
```
#! /bin/sh
/usr/bin/nautilus --no-desktop --browser & sleep 1 && xsendkeys +F3
```
Save and close, then make it executable
```
sudo chmod +x /usr/bin/nautilus_split-view
```
Now test it by pressing Alt+F2 on desktop to run 
```
/usr/bin/nautilus_split-view
```
If it works, just update your shortcuts using alacarte to point to it. For myself i've got two keyboard shortcuts, Windows key + F runs /usr/bin/nautilus_split-view, and Windows key Alt + F runs /usr/bin/nautilus. 

If it doesn't work try increasing the sleep time by 0.5 increments. 

Best,
AM

<rant>
Let's hope gnome devs don't find a way to disable this workaround to protect their ideal mode of operation or whatever philosophical argument they used to remove this feature. 
</rant>

---

