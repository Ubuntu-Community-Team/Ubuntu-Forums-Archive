---
title: "New cursor doesn't fully function"
date: 2010-10-23
forum: General Help
---

### Post by SunnyDan on 2010-10-23
I need some help, I am currently redoing my setup and have installed a new cursor called Vienna3Ubuntu. I extracted it to the .icons folder, went to preferences and found it, it the cursor options list, right where it should be, but when I applied it, it only works kinda half way, the normal cursor won't change at all, and the other cursors only work in by browser and when I am reszing windows and such. Why won't the cursor work like it should? I am using compiz and I wonder if that has something to do with it. I have already tried restarting, relogging, reinstalling, and fiddling with general options in compiz. Help would be appreciated.

---

### Post by Jebtrix on 2010-10-23
Works fine, needs to be extracted to /usr/share/icons as root. Not sure what you mean by .icons folder

---

### Post by Jebtrix on 2010-10-23
Since your having problems maybe trying creating a Vienna3Ubuntu.theme file in /etc/X11/cursors with

```
[Icon Theme]
Inherits=Vienna3Ubuntu
```

Then delete the /usr/share/icons/Vienna3Ubuntu/index.theme file.

---

