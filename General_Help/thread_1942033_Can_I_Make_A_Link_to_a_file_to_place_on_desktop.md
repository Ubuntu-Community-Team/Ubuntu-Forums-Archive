---
title: "Can I Make A Link to a file to place on desktop?"
date: 2012-03-16
forum: General Help
---

### Post by SergioQ on 2012-03-16
I did right click the file, and there is a Make Link option, but it is greyedout.

So is this a rights thing?
Can't figure it out.

Any hints would be nice ;-)

Thanks ahead, as always

---

### Post by jerome1232 on 2012-03-16
The "Make a Link" in nautilus tries to make the link in whatever directory your currently in, which you probably don't have rights to do. Easy way to this

do (note you can drag the file into your terminal to paste it's full path into the terminal)

```
ln -s /path/to/file ~/Desktop
```

---

### Post by kc1di on 2012-03-16
> **SergioQ said:**
> I did right click the file, and there is a Make Link option, but it is greyedout.

So is this a rights thing?
Can't figure it out.

Any hints would be nice ;-)

Thanks ahead, as always

Hi if you want to placed a program launcher on your desktop simply copy it's file from /usr/share/application to your /home/desktop folder. or copy any folder you want to show on the desktop to  they will the appear on the desktop to /home/desktop file.
This is assuming your running unity desktop.

---

### Post by SergioQ on 2012-03-16
The ln -s was the way to go.  Thanks guys

---

### Post by CatKiller on 2012-03-17
Middle-click & drag.

---

### Post by jerome1232 on 2012-03-17
> **CatKiller said:**
> Middle-click & drag.

Did not know that, I learn something new every day, thanks!

---

### Post by harimurugan on 2012-03-17
> **SergioQ said:**
> I did right click the file, and there is a Make Link option, but it is greyedout.

So is this a rights thing?
Can't figure it out.

Any hints would be nice ;-)

Thanks ahead, as always

use cairo dock it will b more useful when u want to keep link for so many files and folders..

---

