---
title: "Remove items from taskbar"
date: 2006-06-19
forum: General Help
---

### Post by bohboh on 2006-06-19
I use xmms as my media player. I have the plugin installed which creates the system tray icon. Is there a way yo also remove the item from the taskbar? I dont see the point in having a shortcut in the system tray and have it take up space in my taskbar.

Thanks

---

### Post by jazzgossen on 2006-06-19
You can do it (and other nifty window stuff) with devilspie, but I don't know if there's a simpler solution.

[www.burtonini.com/blog/computers/devilspie](www.burtonini.com/blog/computers/devilspie)

---

### Post by linuchsan on 2006-06-19
Right click on it >remove from panel

---

### Post by bohboh on 2006-06-19
[QUOTE=jazzgossen]You can do it (and other nifty window stuff) with devilspie, but I don't know if there's a simpler solution.

[www.burtonini.com/blog/computers/devilspie](www.burtonini.com/blog/computers/devilspie)[/QUOTE]

Devilspis looks cool. But i cannot see any syntax which will allow me to remove an item from the taskbar. 

(Could move it to "workspace right" , the system tray remains on workspace 1,)

---

### Post by Johnsie on 2006-06-19
If the worst comes to the worst you can right click the "taskbar" and then click "New Panel" and create a whole new panel. I'm pretty sure there is a better way to do it though so I'm asking around....

---

### Post by Lord Illidan on 2006-06-19
Can't you uninstall the task-bar plugin?

---

### Post by Johnsie on 2006-06-19
someone told me it might be in terminal: 

**gconf-editor**

and then

 -> apps -> panel -> applets

---

### Post by jazzgossen on 2006-06-19
[QUOTE=bohboh]Devilspis looks cool. But i cannot see any syntax which will allow me to remove an item from the taskbar. 

(Could move it to "workspace right" , the system tray remains on workspace 1,)[/QUOTE]

The author doesn't have any docs, unfortunately, but there's a good manual at wiki.foosel.net. Have a look here: [http://wiki.foosel.net/linux/devilspie#skip_tasklist](http://wiki.foosel.net/linux/devilspie#skip_tasklist)

---

### Post by bohboh on 2006-06-19
[QUOTE=Johnsie]someone told me it might be in terminal: 

**gconf-editor**

and then

 -> apps -> panel -> applets[/QUOTE]

Had a look, not sure what i am meant to be changing. To make sure i made myself clear, when i refer to the taskbar, its actually called the windows list. (Taskbar is what it is called in xp, remnants of xp still reside in my brain :) )

---

### Post by bohboh on 2006-06-19
Sorted. If anyone else needs to know, use this:

[http://alltray.sourceforge.net/]("http://alltray.sourceforge.net/")

Which you can get the latest version from here

[http://files.filefront.com/alltray_067_067_1_i386deb/;5166507;;/fileinfo.html]("http://files.filefront.com/alltray_067_067_1_i386deb/;5166507;;/fileinfo.html")

---

### Post by longinus on 2006-06-19
Left click twice on the icon in the system tray..
Works for progs like Rhytmbox... probably for xmms too.

---

### Post by redgilda on 2006-08-26
> **longinus said:**
> Left click twice on the icon in the system tray..
Works for progs like Rhytmbox... probably for xmms too.
If I left click twice on the xmms icon - it just comes back to the same status I was at before. Left-clicking once removes both xmms both from desktop and from taskbar (but that is not what I want to achieve...)

Id like to keep the xmms main window on desktop (and the icon in tray) but to remove it from the taskbar... hmm I'll try to check out the solutions above... though it's a pity I have to install other programs to do such a small thing :(

---

### Post by rangita on 2008-05-14
> **bohboh said:**
> Sorted. If anyone else needs to know, use this:

[http://alltray.sourceforge.net/]("http://alltray.sourceforge.net/")

Which you can get the latest version from here

[http://files.filefront.com/alltray_067_067_1_i386deb/;5166507;;/fileinfo.html]("http://files.filefront.com/alltray_067_067_1_i386deb/;5166507;;/fileinfo.html")

This is the right answer.  It's in apt for Hardy.

```
sudo apt-get install alltray
```

Then to run audacious, do:

```
alltray --skip-taskbar --sticky -s audacious
```

That will take it out the taskbar, put it on all desktops, and start it un-minimized.  I made an alias with the above, and set my Audacious icon to point to it.

Getting the MP3 player just right is serious business...

---

