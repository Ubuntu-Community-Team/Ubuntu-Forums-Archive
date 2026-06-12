---
title: "Clear out applications menu probe"
date: 2010-11-20
forum: General Help
---

### Post by lmellor on 2010-11-20
Hi, I recently forced a reset on my applications menu, this system has been updated since at least Intrepid all the way through to Maverick and so I have decided to start having a bit of a clean up.

Having deleted my ~/.config/menus directory and logged out/in, I noticed that I now have a menu for 'Other' within my applications menu, there must be around 200 entries in there, detailing every app I have ever installed through wine (whether they are still installed or not) along with a few others (VMWare player for one example).

My question is quite simply this...

Where are the files located that the computer probes to regenerate this menu?  I'd like to clear the list as much as possible as the same list gets in the way when choosing what program a file should be opened with (it's far easier to choose from a list of currently installed apps than a list of 300 or so possibly installed apps).

Thanks in advance, I do hope that somebody can shed some light onto the subject, I have googled like crazy and I simply cannot find a solution anywhere.

---

### Post by northern lights on 2010-11-20
System > Preferences > Main Menu

---

### Post by lmellor on 2010-11-20
> **northern lights said:**
> System > Preferences > Main Menu

I know how to do this, my problem lies in the fact that if I clear it out of there then reset the menus they come back, I want to get rid of them permanently, it is needless clutter and the programs are no longer on the system.

As the screenshot shows, this will take literally HOURS using alacarte with it's "one at a time" methods.

---

### Post by lmellor on 2010-11-20
found it at last, after much scouring of the hidden directories in my home folder I discovered ~/.local/share/applications/ which contained references to applications that were in the 'other' folder.

At this point I'd like to say that I made the wise choice of renaming them or moving them, I simply deleted them out of frustration, I then deleted my ~/.config/menus folder and logged in/out.

Now my Other folder only has the files I'd like in it, and furthermore if I right click a file and go properties>open with>add I am now presented with a MUCH shorter list of potential candidates.

Go me!

---

