---
title: "gtk sudo looks ugly"
date: 2009-08-27
forum: General Help
---

### Post by sandyd on 2009-08-27
i did this before... but im brainwashed currently.
how do you make programs (while running with sudo) run with gtk-engines-qt ?

they look terrible right now

---

### Post by dj-toonz on 2009-08-28
U mean they don't use the GTK theme that your using? & that there just i.e grey & lifeless? i was wondering that myself why as when I do a sudo gedit command, the gedit box is ugly compared to when i use gedit normally, Anybody know why & how to get them looking like normal ? cheers

---

### Post by sandyd on 2009-08-28
bump

---

### Post by Regenweald on 2009-08-28
Is it not gksudo ?

---

### Post by rotwang888 on 2009-08-28
I think the easiest way to do this is to link "your" themes and icons to root's.  If I understand the problem, that is.  You mean when you open, say, Synaptic, or the file manager with "gksudo"?  Try this-
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

---

### Post by Bachstelze on 2009-08-28
More like

```
sudo ln -s .gtkrc-2.0 /root
```

---

### Post by fooman on 2009-08-28
i think its good to leave them ugly/different from the normal users so that you always know when you are using sudo.

forget your using sudo & make a silly mistake....and you could get yourself into quite a mess.

just my 2 cents.  ;)

---

### Post by sandyd on 2009-08-28
so far tried all siggestions, but still no luck :(

---

### Post by sandyd on 2009-08-28
this is the idiotic, but workable way to do it
```

gksudo systemsettings

```Then go into Appearance -> GTK Styles

oh, and thats for KDE 4.3. not sure if it works under kde 4.2 (maybe the program name is different, i don't know)

---

### Post by Bachstelze on 2009-08-28
> **carlee said:**
> so far tried all siggestions, but still no luck :(

My mistake, you must give the absolute path to your .gtkrc, for example

```
ln -s /home/alice/.gtkrc-2.0 /root
```

Of course replace by your actual username. Also, if you get a "file already exists" error, replace [font=monospace]ln -s[/font] with [font=monospace]ln -snf[/font].

*EDIT: that works too, and it's absolutely not idiotic. ;)*

---

