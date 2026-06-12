---
title: "How to auto-open aterminal window with current path, pos and dims at startup?"
date: 2009-10-21
forum: General Help
---

### Post by pstein on 2009-10-21
Sorry for this newbie question:
 
Assume I configured a Terminal window with a certain size (dimension) on a certain position with a certain path.
 
How can I tell Ubuntu to automatically open exactly such a Terminal window at startup/login?
 
Peter

---

### Post by bobtfish on 2009-10-21
You can set up a command like this:
```
gnome-terminal --geometry=widthxheight --working-directory="/path/to/directory"
e.g.
gnome-terminal --geometry=75x25 --working-directory="/bin"

```
will open a terminal in /bin that is 75 characters wide by 25 lines high.
To have it start  automatically add it as an entry to System->Preferences->Startup Applications.
Chris

---

### Post by nothingspecial on 2009-10-21
> **bobtfish said:**
> You can set up a command like this:
```
gnome-terminal --geometry=widthxheight --working-directory="/path/to/directory"
e.g.
gnome-terminal --geometry=75x25 --working-directory="/bin"

```
will open a terminal in /bin that is 75 characters wide by 25 lines high.
To have it start  automatically add it as an entry to System->Preferences->Startup Applications.
Chris

and if you use the x flag you can have it start in that location with a certian application running such as screen or dvtm

```
gnome-terminal --geometry=75x25 --working-directory="/bin" -x dvtm
```

---

### Post by pstein on 2009-10-29
> **bobtfish said:**
> To have it start automatically add it as an entry to 
System->Preferences->Startup Applications.
Chris
 
Hmm, I found a menu
 
System->Preferences
 
but no menu
 
System->Preferences->Startup Applications
 
Do I have to enable this menu entry somewhere?
 
Peter

---

### Post by nothingspecial on 2009-10-29
If you are using a previous Ubuntu edition, 8.04 Hardy perhaps, it`s syatem > preferences > sessions

---

