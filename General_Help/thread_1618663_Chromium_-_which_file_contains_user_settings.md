---
title: "Chromium - which file contains user settings?"
date: 2010-11-10
forum: General Help
---

### Post by TBABill on 2010-11-10
I have the Ubuntu font set in Chromium via the tools>>preferences>>personal stuff settings and I decided to change it to something else. However, even after hitting restore defaults and manually selecting new fonts, the font remains the Ubuntu font. I even went into System>>Preferences>>Appearance and changed the fonts there to something else just to see if it helped, but no luck.

I then did a purge via terminal with apt-get of Chromium, then reinstalled. Same result.

So where is the user file that contains these settings so I can delete it and have the program create a new file with default settings? Or is there an easier way to achieve the same result (default)?

Edit: on this machine I am on 10.04

---

### Post by kerry_s on 2010-11-10
open the file manager, press ctrl+h, go into .config

---

### Post by TBABill on 2010-11-10
Right, but which file is it specifically?

Edit: delete the entire Chromium folder there?

---

### Post by TBABill on 2010-11-10
Deleted Chromium folder in .config, problem solved.

---

