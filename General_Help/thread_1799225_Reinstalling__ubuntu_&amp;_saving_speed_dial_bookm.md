---
title: "Reinstalling  ubuntu &amp; saving speed dial bookmarks"
date: 2011-07-07
forum: General Help
---

### Post by diandal on 2011-07-07
Ok, like the title says, im wanting to reinstall ubuntu 11.04 but do not want to lose all my speed dial bookmarks. As i can see i have 3 options but would rather have the 4th by being able to just reload my speed dial settings.

1. copy all my speed dial bookmark sites to firefox bookmarks and turn on home sync so i have a copy of all sites

2. copy all my speed dial bookmark sites to firefox bookmarks and use xmarks(foxmarks)

3. write down all my speed dial sites and start afresh when i reinstall

4. reinstall ubuntu and then speed dial and somehow by magic my settings are there ???

if only firefox had like a log in facility and wether you had to reboot or use another pc all your personal settings could be there

---

### Post by lovinglinux on 2011-07-07
Just backup ~/.mozilla folder. Inside that folder is a firefox folder, which holds you Firefox profiles, which holds all your Firefox settings. More info at [http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups](http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups)

When you install Ubuntu again, make sure to create a separate partition for home, so you can install Ubuntu without loosing personal files and settings.

---

### Post by diandal on 2011-07-07
thanks for that, but bit complicated for me-lol 

will just write down all my bookmarks and re do it, phew, but ta

---

### Post by Megaptera on 2011-07-07
Why not use Xmarks to back them up? Free, easy to use ..."Install Xmarks on each computer you use, and it seamlessly integrates with your web browser and keeps your bookmarks safely backed up and in sync.

Xmarks will sync across browsers too. Today we support Firefox, Chrome, Internet Explorer, and Safari (Mac OS)."

[http://www.xmarks.com/about/features](http://www.xmarks.com/about/features)

---

### Post by lovinglinux on 2011-07-07
> **diandal said:**
> thanks for that, but bit complicated for me-lol 

will just write down all my bookmarks and re do it, phew, but ta

Just copy the mozilla folder to a flash drive or CD, reinstall Ubuntu and copy the folder back. Is a lot easier and faster than writing down the bookmarks. Besides you also keep passwords and other settings.

If you can't see the mozilla folder, then hit CTRL+H to show hidden files.

---

### Post by martinthebandit on 2011-07-09
The easiest way I found to do it was just to email the links to myself, a little long winded maybe but it worked

---

### Post by pqwoerituytrueiwoq on 2011-07-09
plug in a flash drive
```
cp -R ~/.mozilla /media/[Press Tab Key]
```
after installing ubuntu DO NOT OPEN FIREFOX YET
login and plug the flash drive back in
```
cp -R /media/[Press Tab Key]/.mozilla ~/
```

if yuo open the file browser (HOME under places)
press [Ctrl]+[H]
and drag/drop .mozilla to the flash driver and back into the home folder after install before opening firefox

---

