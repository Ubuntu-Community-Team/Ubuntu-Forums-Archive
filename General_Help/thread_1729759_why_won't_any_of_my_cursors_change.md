---
title: "why won't any of my cursors change?"
date: 2011-04-15
forum: General Help
---

### Post by Spyderkid on 2011-04-15
If i try and select a new cursor it doesn't change?

it just stays on the defualt. However if the mouse is on the select one (the hand) or when you have it over text it makes a sort of shape like an 'I' it has the new cursor that i have selected. only when the cursor isn't doing anything is it the defualt and won't change

help

---

### Post by TeoBigusGeekus on 2011-04-15
Are you using compiz?
There is a bug in Lucid and Maverick; you change your mouse cursor theme but it won't "stay".
A workaround is to go to /usr/share/icons/default
There is a file there called index.theme (if I remember correctly).
Edit it and change the line
```
inherits (Name of theme)
```
to
```
inherits ExactNameOfDesiredMouseCursorTheme
```
Sorry for the generic answer, I'm not on an ubuntu machine right now.

---

### Post by Spyderkid on 2011-04-16
it changed the defualt however i still have the same problem that the standard cursor it the DMZ White. and the other ones like the waiting cursor or the text cursor are the new defualt?

---

### Post by TeoBigusGeekus on 2011-04-16
Have you restarted the pc?

---

### Post by Spyderkid on 2011-04-16
yep

---

### Post by Spyderkid on 2011-04-17
anyone? it didn't work.

---

### Post by Spyderkid on 2011-04-18
fixed the problem :)

you have to change the cursor under general in compiz

---

