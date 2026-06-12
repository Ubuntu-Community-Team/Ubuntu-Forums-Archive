---
title: "Problem with fonts after installing WINE"
date: 2012-03-02
forum: General Help
---

### Post by evil gnome on 2012-03-02
After I installed wine, all the fonts in chromium and firefox changed. I want the ubuntu fonts back. don't like the new fonts.

---

### Post by Retor on 2012-03-02
Seems there is an issue where installing wine includes Windows fonts. Most web pages tell the browser to attempt to use windows fonts first (verdana, etc) and then whatever it likes afterwards. 

After installing Wine, Chrome and Firefox suddenly found these fonts and applied them. 

You can try to search for ttf-mscorefonts in Software Center and uninstall them. 

Or, you can (atleast in Firfox) go to Tools, Settings, Content, Fonts and colors, Advanced, and deselect "Allow webpages to .." But that would cause all webpages to only use the fonts mentioned above.

In Chrome, you can try to change the settings here: chrome://settings/fonts

---

### Post by evil gnome on 2012-03-02
SIDE QUESTION:
How to disable the ads banner at ubuntu software center? I have no graphic cards third-party driver installer, and the banner slows down the system.

---

