---
title: "font installation in openoffice"
date: 2010-09-25
forum: General Help
---

### Post by vinay nadig on 2010-09-25
hi, I needed some help on installing a new font on openoffice 3.2.
the font i needed to install was kannada.
i have installed the truetype kannada font from the software center, but cant find the font in font dropdown list in openoffice.
any help??

---

### Post by irishbreakfast on 2010-09-25
I've installed fonts but not from the software centre but I have a memory of needing to make sure that all instances of oo were closed and then re-opened before it recognized the fonts. But that might have been on another OS, sorry.
Very late, hope I am making sense
Good night

---

### Post by rocknrollmouse on 2010-09-25
Generally, after installing new fonts, you have to log out and log in again to be able to see and use the new fonts. 
Or
At the command prompt enter the following:
```
$sudo fc-cache -fv
```

irishbreakfast's advice about having OpenOffice closed rings a bell, but in honesty I can't remember (I usually install fonts with with apps closed - must be the Windows user in me ;))

---

### Post by vinay nadig on 2010-09-26
> **rocknrollmouse said:**
> Generally, after installing new fonts, you have to log out and log in again to be able to see and use the new fonts. 
Or
At the command prompt enter the following:
```
$sudo fc-cache -fv
```irishbreakfast's advice about having OpenOffice closed rings a bell, but in honesty I can't remember (I usually install fonts with with apps closed - must be the Windows user in me ;))


nope :( no luck yet.. i couldn't find the fonts in the openoffice again. I ran the command and the cache was succesful.. logged in again.. any more ideas???

---

