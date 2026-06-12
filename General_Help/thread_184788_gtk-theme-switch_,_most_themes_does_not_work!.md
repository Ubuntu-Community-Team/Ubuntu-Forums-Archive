---
title: "gtk-theme-switch , most themes does not work!"
date: 2006-05-30
forum: General Help
---

### Post by Biffy on 2006-05-30
I am using fluxbox. First i start up the app with "switch2" . Now i can choose themes. A lot of themes! So i choose clearlooks. When clicking apply nothing happens, and i get this error message:

```
/home/larsson/.gtkrc-2.0:2: Unable to find include file: "(null)/Clearlooks/gtk-2.0/gtkrc"
```

I was trying most of the themes out, and not many of them works. They are all returning the same error message. What to do?

---

### Post by Biffy on 2006-06-06
Bump!

---

### Post by dmizer on 2006-06-07
i think it just needs a symbolic link.  it's looking for your theme in "/Clearlooks/gtk-2.0/gtkrc", but it is not there.  so find out where it is by doing something like:
```
whereis gtkrc
```
and it will tell you where it's located.  once you find it, just create a symbolic link between it's actual location and /Clearlooks/gtk-2.0/gtkrc.

if you can't find gtkrc anywhere, are you sure you have installed gtk2.0?

---

### Post by Biffy on 2006-06-07
[QUOTE=dmizer]i think it just needs a symbolic link.  it's looking for your theme in "/Clearlooks/gtk-2.0/gtkrc", but it is not there.  so find out where it is by doing something like:
```
whereis gtkrc
```
and it will tell you where it's located.  once you find it, just create a symbolic link between it's actual location and /Clearlooks/gtk-2.0/gtkrc.

if you can't find gtkrc anywhere, are you sure you have installed gtk2.0?[/QUOTE]

> larsson@ubuntu:~/.fluxbox $ whereis gtkrc
gtkrc:

Yes i think gtk2 is installed. I am using Nautilus, Epiphany, Firefox, Gaim and so on. No problems there.

---

### Post by dmizer on 2006-06-07
try "whereis Clearlooks" ... not sure if that will help or not, but this is reaching a point where i would have to install it myself to try to help you solve the problem, and i have alot on my plate right now.

---

### Post by Biffy on 2006-06-08
```
larsson@ubuntu:~ $ whereis clearlooks
clearlooks:
larsson@ubuntu:~ $ whereis Clearlooks
Clearlooks:
```

Gives me nothing. Thanks for replying tough. :)

---

### Post by bearfrog on 2006-11-24
I have the same problem as the original poster and have been searching around for the solution.  I can copy the themes to a ~/.themes folder and make them work or manually edit the .gtkrc-2.0 file to use the correct path but these methods just seams stupid.

here is my .gtkrc-2.0 file.. 

# -- THEME AUTO-WRITTEN DO NOT EDIT
include "(null)/Crux/gtk-2.0/gtkrc"

include "/home/bearfrog/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

switch2 knows about the theme path because it propagates the selection list box with them so what is the (null) there for?? aghghhhgh

Any help would be marvellous.

---

