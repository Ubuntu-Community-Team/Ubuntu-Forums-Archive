---
title: "Mozilla Fireox Themes"
date: 2010-06-14
forum: General Help
---

### Post by Jonny87 on 2010-06-14
Im just wondering if anyone knows where firefox stores its themes and if its possible to copy them so that I can put them on to another computer.

---

### Post by ubunterooster on 2010-06-14
You have to copy the whole profile. T[COLOR=Red]his will overwrite all of the old Firefox profile bookmarks, settings [COLOR=Magenta]passwords[/COLOR], and preference[/COLOR]s:
1,home folder with hidden folders shown

2,firefox folder

3,profile folder to copy to new firefox's location

4, the line of profiles.ini that needs to be changed to the new profile

---

### Post by lovinglinux on 2010-06-14
Use Quick Backup feature of [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) extension to export your theme. Keep in mind that copying your theme doesn't include customizations. If you want to include buttons positions and toolbars, you will need to copy the file **localstore.rdf** from your profile.

---

