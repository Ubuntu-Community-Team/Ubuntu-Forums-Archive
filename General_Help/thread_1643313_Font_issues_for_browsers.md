---
title: "Font issues for browsers"
date: 2010-12-11
forum: General Help
---

### Post by mikerobinson on 2010-12-11
I have a small problem here that I can't figure out. Everything looks fine on my system, except on some sites (e.g. Google and ubuntuforums.com) where ALL the fonts appear bold in all my browsers (FF, Opera and Konq) in both Gnome and KDE. Another strange thing is that it is for this user and not for any other users. Any ideas how to fix this? 

I checked preferences > appearance > fonts and only the window title is using a bold font. Also, in KDE, none are set to bold in the fonts preferences.

---

### Post by AlphaLexman on 2010-12-11
Have you tried changing the font? You may have some font substitution going on!

---

### Post by mikerobinson on 2010-12-11
I found out what my problem was. I had a corrupted (at least that's what I'm calling it) ~/.fonts/arialbd.ttf file. Deleted the file and everyone is happy :)

---

