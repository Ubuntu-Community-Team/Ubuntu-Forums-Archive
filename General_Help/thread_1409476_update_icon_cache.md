---
title: "update icon cache"
date: 2010-02-17
forum: General Help
---

### Post by Post Monkeh on 2010-02-17
i was looking for a way to stop my menus taking a few seconds to load my icons when i first open them and found a few guides suggesting using the gtk-upate-icon-cache command, but with the any colour you like icon theme i'm using (stored in my home folder .icons directory) i kept getting a "gtk-update-icon-cache: The generated cache was invalid." fault

i used the inbuilt facility in the acyl script to copy the icons to the usr/share/icons directory and tried the command again, this time using

 sudo gtk-update-icon-cache --force --ignore-theme-index /usr/share/icons/ACYL_Icon_Theme_0.8.1/

but i still get the same error.

i tried with several of the custom icon themes i've installed and only 1 of the first 7 or 8 i tried successfully created the cache (and tbh it was an ugly theme)  is this a general problem with custom icon themes or am i doing something stupid?

---

### Post by lidex on 2010-02-17
Have a look here:
[http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29]("http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29")

---

### Post by Post Monkeh on 2010-02-17
> **lidex said:**
> Have a look here:
[http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29]("http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29")

i saw that, i found one icon theme in the usr/share/icons folder (buuf) causing faults when i used the commands posted there, but i still get errors updating my acyl theme even after removing buuf.

i did find a reference to scalable/emotes in the index.theme which doesn't exist so i deleted the refernce but i still get the error

---

### Post by Post Monkeh on 2010-02-18
anyone?

---

### Post by Post Monkeh on 2010-02-18
well i was able to get the cache to create successfully by deleting a file in the mime folder that looked out of place (didn't have the colour like the rest of the theme)

however the created theme cache file is only about 90kb (most other themes i cached when trying to see what happened were coming in at much larger sizes dependent on the theme)

my places menu now seems to be loading the icons immediately, but the applications/system menus and all sub menus are still suffering from the delay. am i doing something wrong?

---

