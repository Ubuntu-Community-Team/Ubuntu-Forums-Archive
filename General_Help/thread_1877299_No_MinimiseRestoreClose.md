---
title: "No Minimise/Restore/Close"
date: 2011-11-07
forum: General Help
---

### Post by fleamour on 2011-11-07
I reinstalled Xubuntu 11.10 thinking the above was caused by one hack too far.  However it happened again.  The system takes an age to shut down then when rebooted the desktop icons are positioned too high under top bar & every window is missing Minimise, Restore & Close function.

I uninstalled HPLIP Toolbox as this was the last app installed, but if it was at fault, things have still not reverted to normal.

EDIT:  Also Chromium no longer respects the top bar when opening & will not resize to screen when hitting Restore.

:confused: :-k :confused:

---

### Post by hwttdz on 2011-11-08
Are you using compiz?  Sounds like you have the place windows plugin disabled.  Try firing up ccsm and checking the enable box for "place windows".

In the meanwhile you can move windows by holding the alt key and clicking anywhere in the window with the mouse.

---

### Post by elliotn on 2011-11-08
I also don't have the min, max, close button in ubuntu

---

### Post by scottbomb on 2011-11-08
It sounds like your windows manager isn't launching -  xfwm4. It should be in your session startup list. When this happened to me, I fixed it by opening terminal and typing ```
xfwm4 & 
```

---

### Post by fleamour on 2011-11-08
> **scottbomb said:**
> It sounds like your windows manager isn't launching -  xfwm4. It should be in your session startup list. When this happened to me, I fixed it by opening terminal and typing ```
xfwm4 & 
```

Problem is Alt F2 or Terminal itself, both do not accept any text input in current state.

:( :confused: :(

---

### Post by Toz on 2011-11-08
At the login screen, type Ctrl+Alt+F1 then login at the text screen. If you delete your sessions cache, it will be re-created on next login and xfwm4 will be run. Source: [http://forum.xfce.org/viewtopic.php?pid=22180#p22180]("http://forum.xfce.org/viewtopic.php?pid=22180#p22180").

After you've logged in at the text screen, then:
```
mv ~/.cache/sessions ~/.cache/sessions.BAK
```
...(lets save it just in case)

Ctrl+Alt+F7 and log in to the GUI.

---

### Post by fleamour on 2011-11-08
@Toz, your sane advise has saved me before now!

Thanks!

The PC in question is at my mother's house so will be a while until I can try your suggestion.  But I am glad I posted now.  

Should I report a bug?  If so, what package?

---

### Post by Toz on 2011-11-08
No worries. I'm not sure the bug report would get the attention unless you could identify the root cause (this is one of the most reported complaints about xfce). If you could post a copy of the ~/.xsession-errors file when you are having the issue (before you fix it), we can have a look and see if anything sticks out as a possible cause.

---

