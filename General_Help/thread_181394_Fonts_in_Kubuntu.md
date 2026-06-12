---
title: "Fonts in Kubuntu"
date: 2006-05-24
forum: General Help
---

### Post by Isoss on 2006-05-24
I have Ubuntu and Kubuntu on different PCs. in Ubuntu I have all my favourite fonts installed. so I need the same fonts on kubuntu. will it be ok if I just copy /usr/share/fonts/ from Ubuntu to /usr/share/fonts/ in kubuntu?

Just making sure this won't cause any damage or corruption!

Hope some one who's 100% sure of this would answer.

Thanks in advance

Isos

---

### Post by Neo Ex on 2006-05-24
The only difference between Ubuntu and Kubuntu is the desktop environment, so you can copy the fonts from Ubuntu and paste it in the same directory in Kubuntu.
If you prefer you can also put the fonts in ~/.fonts.

---

### Post by Isoss on 2006-05-25
I guess you mean /home/isos/.fonts in show-hidden-files mode! I opened it in KDE and all it contains is 5 files, for of them are .ttf and anpther is .dir ... so if I copy all the fonts (which I have actually copied from windows fonts to Gnome /usr/share/fonts/ ) to the ~/.fonts will that make all the applications that have the fonts  preferences take them?

---

### Post by an.echte.trilingue on 2006-05-25
an easier way might be to get your font .debs out of the apt cache on the machine that they are installed in and then use dpkg to install them.

---

### Post by ace2005 on 2006-05-25
In konqueror the fonts show up when you type "fonts:/" into the address bar, there are two folders for system fonts and user fonts, this also works in nautilus but i'm not sure if all the fonts are shown or just the user fonts

You could get copy the fonts you want this way

---

