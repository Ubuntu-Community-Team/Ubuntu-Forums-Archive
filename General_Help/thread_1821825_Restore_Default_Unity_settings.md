---
title: "Restore Default Unity settings"
date: 2011-08-09
forum: General Help
---

### Post by LinuxSavedMyComputer on 2011-08-09
I've had this computer for a few days. I was playing around with it trying to get the multiple desktop cube. I wanted to restore it back, however every setting had dependencies with other settings so now my unity interface is unusable.
the problems are 
-no taskbar and no lancher
-some keycommands don't work(Ctrl-alt-t no longer opens a terminal, it used to)
-can't log off
 how do i restore it to factory settings
I messed it up using CCSM or whatever it's called

---

### Post by Basher101 on 2011-08-09
Reinstalling ubuntu would be the easiest option, but also a last resort (unless you haven't installed many programs or configured alot of things so a reinstall doesn't come in mind)

---

### Post by LinuxSavedMyComputer on 2011-08-09
I could do that but apparently there is a unique partition setup that ignores a part of my hard drive which is damaged (hence the name LinuxSavedMyComputer)

---

### Post by mc4man on 2011-08-09
Open a terminal any way you can or run dialog if that works, (Alt+F2) and run - may take several seconds or more after running
```
unity --reset
```

If need be,  to open a terminal just navigate to /usr/share/applications, scroll down and d. click on the terminal icon
(if you have no access to nautilus then r. click on the desktop > 'Create New  Folder' and use that

---

### Post by LinuxSavedMyComputer on 2011-08-09
Failed, It printed a lot of text then did nothing

---

