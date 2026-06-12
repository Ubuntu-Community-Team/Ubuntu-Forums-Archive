---
title: "Gaming issues =D"
date: 2010-06-29
forum: General Help
---

### Post by Iknownaught on 2010-06-29
Well...
I have another awesome question for you guys ^^
I just downloaded Warcraft 3, quite the oldie yes, but I need to mount it.
First, which is the application to mount images in ubuntu?
Second, PlayOnLinux will enable me to run it, right?
Thanks in advance again ^^

---

### Post by Helios747 on 2010-06-29
Are you talking about a CD image?


Go here

[https://launchpad.net/~cdemu/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/~cdemu/+archive/ppa?field.series_filter=lucid")

Add that ppa to your repositories by following the directions

then run in terminal

```
sudo apt-get update
sudo apt-get install gcdemu
```

Reboot your computer

then add the CD mounter applet to your gnome task bar by right clicking on the taskbar you want to add it to, click "add new item" (or something)

and find the CD emu applet in that list.

Then you can click on that applet to mount CD and DVD images.


if you're just talking about a plain CD you stick in your computer, ubuntu should auto mount it.

---

### Post by Iknownaught on 2010-06-29
Solved xD
Thanks!!

---

