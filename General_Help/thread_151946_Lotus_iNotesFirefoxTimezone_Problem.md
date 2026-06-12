---
title: "Lotus iNotes/Firefox/Timezone Problem"
date: 2006-03-28
forum: General Help
---

### Post by ronmarley1 on 2006-03-28
Here's a good one...
At work, we are a Lotus Notes shop.  I use iNotes (web version of Lotus Notes) off campus.  Recently, I got the error below in the screen cap.  If I OK the error, everything works fine; it's just VERY annoying.  In the iNotes preferences, my time zone is Eastern.  In the clock preferences in the Gnome panel, UTC is not checked and the timezone is America/New York (i.e., Eastern).  I did a ```
sudo gedit /etc/default/rcS
``` and UTC is set to "No."  I did a ```
sudo tzconfig
``` and the current timezone is US/Eastern.  I've cleared the browser cache and history.  If I use my wife's XP box (painful...), I don't get the error in Firefox or IE (REALLy painful...).  For some reason, iNotes is getting the wrong timezone from somewhere.  Are the any other places I can check for timezone settings in Ubuntu beside /etc/default/rcS, /etc/timezone and tzconfig?
Thanks in advance

EDIT:  PS, I tried the Epiphany browser and got the same error, so I don't think it's a browser issue...

---

### Post by dcstar on 2006-03-30
[QUOTE=ronmarley1]
....... Are the any other places I can check for timezone settings in Ubuntu beside /etc/default/rcS, /etc/timezone and tzconfig?
Thanks in advance

EDIT:  PS, I tried the Epiphany browser and got the same error, so I don't think it's a browser issue...[/QUOTE]
Right-click the clock time on the top RHS of your screen, select "Adjust Date and Time", have a look at the Time Zone setting.

---

