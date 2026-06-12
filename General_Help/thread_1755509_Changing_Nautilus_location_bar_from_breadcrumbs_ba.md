---
title: "Changing Nautilus location bar from breadcrumbs back to text in Ubuntu 11.04"
date: 2011-05-11
forum: General Help
---

### Post by Cyynic on 2011-05-11
Hi there,

I've been searching around google to find a solution to the default location bar setting being breadcrumb buttons instead of the text path I prefer.

I wanted to post a link to this work around for anyone else trying to solve the same problem.



Here is a way to always use a text-based location bar. Simply paste this in a terminal:
```
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry true
```

To switch back, paste this in a terminal:
```
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false
```

[URL="http://www.webupd8.org/2010/05/use-text-mode-location-bar-in-nautilus.html"]http://www.webupd8.org/2010/05/use-text-mode-location-bar-in-nautilus.html
[/URL]



Admins, please shuffle this message to whatever thread it would be most appropriate for, I'm just hoping that in 6-12 months when I upgrade again I'll be able to find it quick and not have to search for 20 frustrated minutes...

---

### Post by seawolf167 on 2011-05-11
For those out there that don't want to paste a command they can't understand, you can do this via the GUI just the same as the previously posted command

```
[ALT][F2]
gconfig-editor
->apps
------>nautilus
----------->preferences
---------------->always_use_location_entry [check this box]
```

---

### Post by hatalar205 on 2011-05-11
Thanks. I have been looking for this.

---

### Post by hsweet on 2011-11-24
I just tried that in 11.10 and nothing changed.  Any idea why not?

---

