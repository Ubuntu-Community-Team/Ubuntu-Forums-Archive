---
title: "Panel disappeared in Ubuntu 10.04!"
date: 2011-10-09
forum: General Help
---

### Post by Rytron on 2011-10-09
Hi.

Today I booted into Ubuntu 10.04 and the panel has disappeared!

I tried deleting these...
.gconf
.gconfd
.gnome
.gnome2
.metacity
...and logging out/in but it did noting. Please help!

I had 1 panel at the bottom. I noticed that the CheckGmail pop-up appeared at the top of the screen but no panels are to be seen.

:confused:

---

### Post by Frogs Hair on 2011-10-09
If you can get into a terminal using Crtl + Alt + T try the following commands. If the first doesn't work try second or third if applicable.   

Reset Panel: 
```
killall gnome-panel
```

Reset Metacity:
```
metacity --replace
```

Reset Compiz if Installed:
```
compiz --replace
```

---

### Post by binary00mind on 2011-10-09
I never lost my panels, always have backups. 

It seems you are not the only one with this problem. 

check this threads, there is no definite answer but worth digging. 

link one: [COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1483781[/COLOR] 

link two: [COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1503448[/COLOR]

I bet that there are a lot more threads about this one.

---

### Post by steveneddy on 2011-10-09
Interesting...

---

### Post by Rytron on 2011-10-09
> **Frogs Hair said:**
> If you can get into a terminal using Crtl + Alt + T try the following commands. If the first doesn't work try second or third if applicable.   

Reset Panel: 
```
killall gnome-panel
```

Reset Metacity:
```
metacity --replace
```

Reset Compiz if Installed:
```
compiz --replace
```

This is odd!
```
$ killall gnome-panel
gnome-panel: no process found
```

Update: I just ran this command and 2 panels are available.
```
gnome-panel
``` :)

I added gnome-panel to startup applications. I presume that is the best solution. I'd like to know why this happened though. Is it a bug?

---

### Post by ajgreeny on 2011-10-09
What do you mean by "two panels are available"?  Do two appear on your screen, one top and one bottom, and are they, or is one at least, set up like your old lost one with the same applets etc etc?

If so It would seem likely that somehow or other you have lost some or all of your gnome-panel configurations in ~/.gconf and now gone back to the default.  If you have a backup of your /home folder you may be able to copy back the **/home/*user*/.gconf/apps/panel** folder and get back to your original setup.

---

### Post by Rytron on 2011-10-09
> **ajgreeny said:**
> What do you mean by "two panels are available"?  Do two appear on your screen, one top and one bottom, and are they, or is one at least, set up like your old lost one with the same applets etc etc?

If so It would seem likely that somehow or other you have lost some or all of your gnome-panel configurations in ~/.gconf and now gone back to the default.  If you have a backup of your /home folder you may be able to copy back the **/home/*user*/.gconf/apps/panel** folder and get back to your original setup.

Yes, the 2 panels like default. I setup my lone bottom panel quickly enough so it is not a problem. Thanks for the tip.

---

