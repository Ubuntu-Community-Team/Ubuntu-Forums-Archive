---
title: "Gnome panel command line"
date: 2011-01-03
forum: General Help
---

### Post by snowmanman on 2011-01-03
Is there a way I can configure gnome-panel with the command line? I want to be able to write a shell script to switch between my AWN desktop setup and my gnome-panel one.

Also (this is less important) is there an easy way to switch between Gnome and KDE? I would assume no, but if there is that would be cool.

---

### Post by foxmulder881 on 2011-01-03
> **snowmanman said:**
> Is there a way I can configure gnome-panel with the command line? I want to be able to write a shell script to switch between my AWN desktop setup and my gnome-panel one.

Also (this is less important) is there an easy way to switch between Gnome and KDE? I would assume no, but if there is that would be cool.

You can do anything in the command line if you know how. But sorry I can't help you with that.

There is no easy way of switching between desktop environments other than logging out and login in again but with the new desktop environment selected at login window. There's simply too much to be loaded upon login to enable easy switching.

---

### Post by Smart Viking on 2011-01-03
Find the name of the process and then find out a working(and non-destructive) way to kill them with the pkill command.

```

# to kill gnome panel
pkill -15 gnome-panel
#to launch gnome-panel
gnome-panel
#to launch awn
awn-package-name-or-whatever
#to kill awn
pkill -15 awn-package-name-or-whatever

```

Something like that could do it, of course that is not a working script thats only commands that might work, but it shouldn't be very hard to make the script function or whatever, peace out.

---

### Post by lithopsian on 2011-01-03
Most Linux settings are stored in files.  Look in ~/.gconf/apps/panel.  I think all the settings are stored in xml files and there are quite a few of them.

---

### Post by snowmanman on 2011-01-03
My main problem is setting gnome-panel back up again. I want to be able to tell it what to put in each panel. I can find a way to set up and take down AWN and take down gnome-panel. I just can't set up gnome-panel.

Hmm... I've found some XML files that gconf-editor seems to point to. Is there a way I can back them up and have two sets of XML files, one for AWN and one for gnome-panel? Then have a shell script swap them when I want to switch?

My biggest problem with this is that I have no idea what each XML file does or corresponds to.

EDIT: The reason I cannot just kill gnome-panel is: 

1.) Keeping it open allows Alt-F2
2.) It will simply restart itself, the only way to get rid of it is to modify settings to make it invisible

---

