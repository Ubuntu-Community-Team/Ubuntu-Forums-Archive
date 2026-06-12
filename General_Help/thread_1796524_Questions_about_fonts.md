---
title: "Questions about fonts"
date: 2011-07-03
forum: General Help
---

### Post by xj0hnx on 2011-07-03
I have a folder with over 1500 fonts, I would like to move them to my /usr/share/fonts folder so that they can be used. Some are from Windows, some are just random extras. I've installed the msttcorefonts, but there are quite a few missing that make some wen pages look different.

How can I go about putting the fonts from my folder, into the appropriate /usr/share/fonts folder to be used? And how can I move them all? I can't drag and drop them, and mv FONT_NAME /usr/share/fonts for all of them will take a month or two. Is there a way to elevate my self to be able to just drag and drop them all? And which folder would they need to go into for them to be used in  Chrome and Firefox?

---

### Post by Toz on 2011-07-03
If you want everyone who logs into the computer to access the fonts, then you should install them to **/usr/share/fonts**. If its just for you, then create a .fonts folder in your home directory and put them there. If you are putting them into .fonts in your home directory, then you can just use your file manager to copy/paste or move.

---

### Post by Toz on 2011-07-03
This might help as well: [https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")

---

### Post by xj0hnx on 2011-07-04
> **Toz said:**
> If you want everyone who logs into the computer to access the fonts, then you should install them to **/usr/share/fonts**. If its just for you, then create a .fonts folder in your home directory and put them there. If you are putting them into .fonts in your home directory, then you can just use your file manager to copy/paste or move.


I'm the only one that uses this computer, thanks for the info and link.

---

### Post by plane123 on 2011-07-04
Thanks for sharing .

---

### Post by CatKiller on 2011-07-04
> **xj0hnx said:**
> How can I go about putting the fonts from my folder, into the appropriate /usr/share/fonts folder to be used? And how can I move them all? I can't drag and drop them, and mv FONT_NAME /usr/share/fonts for all of them will take a month or two. Is there a way to elevate my self to be able to just drag and drop them all?

Computers are good at repetitive tasks. You wouldn't need to do them one by one at the command line... :)

If you wish to drag-and-drop then you'll need a file manager window running as root, which is easy enough.```
gksudo nautilus
``` will do it.

EDIT: If it's just you using the computer then having them in your Home folder will make it easier to remember to move them to a new computer if you upgrade at some point in the future.

---

