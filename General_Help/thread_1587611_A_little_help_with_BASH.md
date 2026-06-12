---
title: "A little help with BASH"
date: 2010-10-03
forum: General Help
---

### Post by Tootiecat on 2010-10-03
I'm writing a post-install script to run on the computers I'm working with.  Most of it is written, but I'm a noob when it comes down to it.  I'd like to know how to disable the system from showing the lockscreen after being idle.  Could someone show me how to do this from the command-line?

Ubuntu 10.10 Maverick Meerkat

---

### Post by oregonbob on 2010-10-03
Take a look at
[http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/](http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/)

---

### Post by nothingspecial on 2010-10-04
Try

```
gnome-screensaver-command -i
```

---

### Post by foxerious on 2010-10-04
Thanks for the link!

```
gconftool-2 --set /apps/gnome-screensaver/lock_enabled --type bool 0
```

The code above disables the screensaver from triggering a lockscreen.  :)

---

