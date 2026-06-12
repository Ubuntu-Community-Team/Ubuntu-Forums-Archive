---
title: "Fonts messed up after installing msttcorefonts"
date: 2010-03-31
forum: General Help
---

### Post by Necis on 2010-03-31
I followed this guide to install Photoshop CS4 for wine, [http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html](http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html).

I got to the part where it asked me to install the msttcorefonts. Now my fonts on ubuntu are messed up. In some spots there are weird white squares where letters should be. How can I fix this?

---

### Post by Necis on 2010-04-02
Could really use some help

---

### Post by eksasol on 2010-04-02
I mean exactly what part of the OS the fonts are working, its it in the menu, the text when you type, or only the Wine apps? That is the font package so it should download a bunch of font packages, was the whole thing installed properly?

 You can try uninstalling it: sudo apt-get remove msttcorefonts

The fonts can also be found in "/usr/share/fonts/truetype/msttcorefonts" which you can delete manually.

You can try: Right click on desktop, choose "Appearance Peferences" -> Fonts, then set a different font.

---

