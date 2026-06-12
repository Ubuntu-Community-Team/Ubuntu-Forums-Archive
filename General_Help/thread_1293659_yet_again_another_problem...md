---
title: "yet again another problem.."
date: 2009-10-17
forum: General Help
---

### Post by what, what? on 2009-10-17
well i was installing [frostwire]("http://www.frostwire.com") and it was taking much longer than it should have to installed, so i had to restart my computer and try again (because i couldnt close the installer) and first thing i did was try to install frost wire again, but on this screenshot it says that there is another set up thing open:

[IMG]http://img136.imageshack.us/img136/848/screenshotox.png[/IMG]

but on the bottom you can easily see that i have nothing else open.

Any help with this?

please?

---

### Post by mac9416 on 2009-10-17
Try running this. It'll finish off the canceled installation:

```
$ sudo dpkg --configure -a
```

Good luck!

---

