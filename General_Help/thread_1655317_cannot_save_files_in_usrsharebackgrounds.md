---
title: "cannot save files in usr/share/backgrounds?"
date: 2010-12-29
forum: General Help
---

### Post by ohVaNiLLaGoRiLLa on 2010-12-29
How come I cannot save photos into usr/share/backgrounds?  is there somehow i can have my backgrounds that i now have saved in a seperate folder be moved into usr/share/backgrounds? or have my new backgrounds folder be the default one?

---

### Post by karthick87 on 2010-12-29
Those files were owned by root.Just save your files in your home directory and move those files using cp command with sudo in-front.Or you can move those files in the the following way,type the following in your terminal
```
gksudo nautilus &
```It will open nautilus with root prievileges..Just copy and paste your files to **usr/share/backgrounds**

---

### Post by ohVaNiLLaGoRiLLa on 2010-12-29
thanks that worked! but when i right click on the desktop and click change desktop background they do not appear there=[ is there a way to make them show?

edit: i have figured it out! thanks!

---

### Post by karthick87 on 2010-12-29
Mark it as [COLOR=Red][SOLVED][/COLOR]

---

