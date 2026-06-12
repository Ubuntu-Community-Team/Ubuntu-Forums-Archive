---
title: "Changing text in starwars screensaver"
date: 2009-10-18
forum: General Help
---

### Post by Ter Rymon on 2009-10-18
[SIZE="4"]**Changing text in starwars screensaver**[/SIZE]

The default setup for this screensaver is nice but would not it be great to have it display any text output you want. Here I'll show you how with a simple example.

Requirements:

xscreensaver-gl-extras
gedit

and root access

First type the following in a terminal:

```
gksudo gedit /usr/share/applications/screensavers/starwars.desktop
```

change the following line in the file

```
Exec=starwars -root 
```

to

```
Exec=starwars -root -program 'cat /usr/share/xscreensaver/config/starwars.text'
```

Save and close editor

in the terminal enter


```
gksudo gedit /usr/share/xscreensaver/config/starwars.text
```


Copy and paste the following into the file:


```
On a computer a long, long time ago...

A battle of operating systems was taking place. The evil empire of Windoze had conquered most of the desktop universe.

A small brave group known as Linux is fighting for freedom against this powerful overlord.

Press any key to join the battle...
```

save and close editor and terminal.

You can have any text output displayed you want by editing the text file or by changing the program the system calls.

---

