---
title: "how can i make gnome-shell default?"
date: 2009-09-25
forum: General Help
---

### Post by chriskin on 2009-09-25
well,how can i make gnome-shell default?

---

### Post by MelDJ on 2009-09-25
preferred applications then system?

---

### Post by chriskin on 2009-09-25
> **MelDJ said:**
> preferred applications then system?

there is only a terminal choice there

gnome-shell is the development version of gnome 3.0 . (!)

---

### Post by jastonas on 2009-11-01
Same question here

---

### Post by chriskin on 2009-11-01
> **jastonas said:**
> Same question here

the only possibly solution i thought of was to add "gnome-shell --replace" at startup, but that's not exactly the official way, if there is any

---

### Post by bostrt on 2009-11-12
I don't know if this is the proper way but I used gconf-editor and set /desktop/gnome/session/required_components/windowmanager to gnome-shell, it seems to work fine.

---

### Post by chriskin on 2009-11-13
thanks for the idea :)

---

### Post by pshirishreddy on 2010-03-30
Open gconf-editor 
go to Desktop>gnome>session>RequiredComponents

and replace compiz or gdm with gnome-shell

---

### Post by jastonas on 2010-05-11
My required components consist of default session (gnome settings daemon), idle delay and required_components_list (windows manager, panel, filemanager), so what should I change? I have lucid lynx 10.04

---

### Post by Dessicus on 2010-05-11
I'm using Lucid as well, Gconf desktop>gnome>session>required_components should look like the image

replace gnome-wm with gnome-shell

[IMG]http://img34.imageshack.us/img34/3677/screenshotconfiguration.png[/IMG]

---

### Post by MrWestwood on 2010-05-28
I have installed Gnome-shell and done all of the above in gconf but I still have normal gdm when I reboot. When I run gnome-shell --replace in terminal gnome shell runs but the terminal window must stay open or I kill gnome-shell. Any advice?

---

### Post by jastonas on 2010-05-29
you could make an executable. Right click on desktop>create document>empty file
Write the "code" there
```
gnome-shell --replace
```
Save it. Right click it, properties, permissions, allow executing of file.
Run it :)

---

### Post by -humanaut- on 2010-05-29
> **chriskin said:**
> well,how can i make gnome-shell default?

Here's how I did it in gconf-editor go to Desktop -> Gnome -> Session Replace windows manager with gnome-shell and replace panel with Mutter. But don't restart after that because there's still a config file that will confuse the system hit alt+f2 type: gksu nautilus


then go to /usr/share/gnome/autostart and create a gnome-shell file in it. If there's already one for metacity rename it and in the command section type gnome-shell

then reboot and GDM will boot you into gnome-shell
I'm gonna tell you though I was using the git version and for whatever reason my harddrive suffered a pretty catastrophic failure.

---

### Post by L815 on 2010-06-05
> **MrWestwood said:**
> I have installed Gnome-shell and done all of the above in gconf but I still have normal gdm when I reboot. When I run gnome-shell --replace in terminal gnome shell runs but the terminal window must stay open or I kill gnome-shell. Any advice?



Use:
```
gnome-shell --replace &
```

This will put the process in the background, allowing you to close the terminal and still have gnome-shell running.

---

