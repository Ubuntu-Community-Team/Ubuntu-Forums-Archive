---
title: "Usb"
date: 2009-08-10
forum: General Help
---

### Post by Awesom on 2009-08-10
Hi I get this error when trying to open my usb... how can I fix this? 

[IMG]http://img35.imageshack.us/img35/4893/screenshotaex.png[/IMG]

Thanks

---

### Post by quixote on 2009-08-11
It might be some arcane permissions problem, i.e. for some reason the user isn't allowed to mount that drive.  There are permanent solutions to that, but just to see whether that's the problem open nautilus as root and then try to mount that USB drive.  Open a terminal (Start > Accessories > Terminal) and type:```
gksudo nautilus
```Don't close that terminal window until you're done using nautilus as root.  Be very careful while you are using it as root.  You can do absolutely anything to your system as root, including blow it up completely, so just test this out, and then (if it does mount) unmount the drive, and close nautilus.

---

