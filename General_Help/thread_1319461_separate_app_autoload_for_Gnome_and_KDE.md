---
title: "separate app autoload for Gnome and KDE"
date: 2009-11-08
forum: General Help
---

### Post by tjk on 2009-11-08
I'm wondering if I can somehow separate the applications that start for KDE from those that start in a Gnome session?  For example: Currently Gnome-Do starts for both KDE and Gnome, and I would like it to only start with Gnome. Incidently, when I check in KDE's autostart and session settings, Gnome-Do is not present (and not shown to be running - but starts at login and is in the process list).

---

### Post by pritamps on 2009-12-30
Goto ~/.config/autostart and edit with your favourite text editor gnome-do.desktop

Add this line somewhere in the file:

```
OnlyShowIn=GNOME;
```

This will make sure gnome-do only shows up in gnome. I'm looking for a more efficient way...but this works!

---

### Post by jbrown96 on 2009-12-30
In KDE what happens a lot is session restore. When you exit KDE, it will remember what programs are running and autostart them next time. There seems to be a bug (been around for a long time) where programs will always get restored. This may be happening in KDE, but I don't think that Gnome does this by default. System Settings-->Advanced (tab)-->Session Manager, then "Start with an empty Session."

Pritamps is probably right, but the KDE restore session may still occur unless you do what I wrote.

---

### Post by tjk on 2009-12-30
Thanks for the fix pritamps!! :)

> **pritamps said:**
> Goto ~/.config/autostart and edit with your favourite text editor gnome-do.desktop

Add this line somewhere in the file:

```
OnlyShowIn=GNOME;
```

This will make sure gnome-do only shows up in gnome. I'm looking for a more efficient way...but this works!

---

### Post by pritamps on 2010-01-01
> **jbrown96 said:**
> In KDE what happens a lot is session restore. When you exit KDE, it will remember what programs are running and autostart them next time. There seems to be a bug (been around for a long time) where programs will always get restored. This may be happening in KDE, but I don't think that Gnome does this by default. System Settings-->Advanced (tab)-->Session Manager, then "Start with an empty Session."

Pritamps is probably right, but the KDE restore session may still occur unless you do what I wrote.

That is true. I had to change that option as well.

I found a nice way to change the option for multiple files:

```
echo OnlyShowIn=GNOME |tee -a FILELIST
```

This will add the line to all the files in FILELIST (separated by a space)! You can even use wild-cards .... Very cool!

You probably also want to do this for the files in /etc/xdg/autostart as well...That's an autostart directory as well. To do the above there, use

```
echo OnlyShowIn=GNOME |sudo tee -a FILELIST
```

since the files there are not accessible without sudo

---

