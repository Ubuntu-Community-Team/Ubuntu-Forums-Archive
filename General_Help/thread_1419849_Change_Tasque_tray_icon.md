---
title: "Change Tasque tray icon?"
date: 2010-03-02
forum: General Help
---

### Post by DedMoroz on 2010-03-02
Ive searched all over on where the tray icon is. Id like to change it on my system to the RTM cow icon. Anyone know where the tasque icon for the tray might reside? Thanks!

---

### Post by DedMoroz on 2010-03-02
OK, I figured it out. You need to download a 'Remember The Milk' PNG image off the net (make sure it has transparency also), use GIMP to resize to some different sizes (22x22, 24x24,32x32,48x8 pixels) and you will need to name them as such....

tasque-22.png
tasque-24.png
tasque-32.png
tasque-48.png

Then, open up the terminal and type in:

gksudo nautilus /usr/share/pixmaps

Once nautilus opens up, copy your 4 files above and paste them into your super user nautilus. It will rewrite the green tasque icons in there. So if you want to back up those green tasque icons first before copying your new images into /usr/share/pixmaps, go for it. That should do it. If you had Tasque open and running, close or quit it, then go back into it and you will see your new icon up in the taskbar!

---

### Post by schiwe on 2010-03-19
tnx dude!:P

---

### Post by AspidZent on 2010-08-11
I've tweaked the original tasque icon in order to comply with the ambiance theme... It is a work in progress... maybe a custom icon from scratch for the next time... Here are the attachments...

---

### Post by AspidZent on 2010-08-11
In fact... here it is!!!... some more tweaking... but squared and themified... enjoy...

---

### Post by ampoland on 2012-07-25
I know this is an old thread, but I wanted to say thanks! The icons are great. :D

---

