---
title: "Need help!"
date: 2009-10-05
forum: General Help
---

### Post by zking on 2009-10-05
Ok I was messing with the configuration editor

Now, i kind of messed something up

I made the window top bar mac style (the minimize,close,maximize buttons on the top left of the window). 

how do i change it back to the top right? 

thanks

---

### Post by elvisd on 2009-10-05
alt + F2
type ```
gconf-editor
```
navigate to ```
/apps/metacity/general
```
check the key ```
button_layout
```
In the description you'll find how to configure it.

Hope this helps

---

### Post by zking on 2009-10-05
> **elvisd said:**
> alt + F2
type ```
gconf-editor
```navigate to ```
/apps/metacity/general
```check the key ```
button_layout
```In the description you'll find how to configure it.

Hope this helps

I changed the value, but nothing happens.

---

### Post by elvisd on 2009-10-05
Are you maybe using emerald as win manager?
Have you tried logging off and on again?

---

