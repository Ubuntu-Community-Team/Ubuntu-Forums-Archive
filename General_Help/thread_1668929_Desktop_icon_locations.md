---
title: "Desktop icon locations"
date: 2011-01-17
forum: General Help
---

### Post by Soulcage on 2011-01-17
Does anyone know where ubuntu (10.10) stores the locations for all the desktop icons? This includes partitions, cd/dvd, flash drives. Sometimes the icons are on top of each other and I want to be able to reset them.
Incase the organize desktop by name doesn't work right. It didn't when I last used it.

I figured it out what I wanted more or less.
```
rm -r ~/.gconf/apps/nautilus/desktop-metadata
```

---

### Post by vidtek on 2011-01-17
Don't know the answer to your query, but this is a good thread to pose my little issues.....

10.10 KDE4 I have a HTPC setup with my boxes in the garage next door so I can have loud fans etc, and hard wired everything into my lounge setup.  My projector using HDMI displays the Ubuntu screen for my main computer and sound is via co-ax interface. It all works well until I logout and then for some reason all the fonts are at about 24 dpi and I just can't read them on the big screen.
If for some reason I want to login to a terminal only or into Gnome, I have to try and remember where they were in the menu list, and I invariably get it wrong.  Also I have 4 desktops and the icons have disappeared from three of the desktops in KDE4 - really weird.
Tony.

---

### Post by Script Warlock on 2011-01-17
desktop icons was located at /usr/share/applications

---

### Post by flipper T on 2011-01-17
/usr/share/icons....surely?

ps don't call me shirley :)

---

