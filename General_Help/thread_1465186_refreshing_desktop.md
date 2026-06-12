---
title: "refreshing desktop?"
date: 2010-04-29
forum: General Help
---

### Post by anaconda on 2010-04-29
Does anyone know how to refresh desktop (from a script?)

I am writing a script, that changes the ~/Desktop to a symbolic link, and points it to whatever folder I want.

I like the idea that desktop is my working directory, and I like to change where Desktop points to.

The script is working well, except that after running the script I have to click on the desktop, and press F5 (or ctrl-R) to get the desktop to refresh, Or I have to open nautilus, and go to ~/Desktop to refresh the files on the desktop. 

Is there a way to achieve the same thing from a command line?

PS. when I get the script to refresh I can share my script to anyone who wants it...
PSS. or I would like to know if there already is an utility for changing where ~/Desktop points to

---

### Post by anaconda on 2010-04-29
Well..
I found one solution

```
gconftool --set /apps/nautilus/preferences/show_desktop --type boolean false
gconftool --set /apps/nautilus/preferences/show_desktop --type boolean true
```

This will hide desktop icons, and show them again, and it DOES refresh the desktop.. It takes a few seconds, but I can live with that.

And of course this will work only in GNOME.

---

