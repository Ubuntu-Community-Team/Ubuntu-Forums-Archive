---
title: "How to Reset Compiz To Default Settings"
date: 2012-08-08
forum: General Help
---

### Post by w201 on 2012-08-08
Just trying to find out if this is a legit command to reset compiz to default settings;

gconftool-2 --recursive-unset /apps/compiz

There's also a "reset to defaults" button under preferences, does that do the same thing?

Thanks!

---

### Post by w201 on 2012-08-08
Did a little searching and found this which worked for me, but you may want to read the warnings before you run those commands.

```

gconftool-2 --recursive-unset /apps/compiz-1 
gconftool-2 --recursive-unset /apps/compizconfig-1 
unity --reset

```

Source:
[http://www.webupd8.org/2011/04/how-t...-icons-or.html]("http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html")

---

### Post by johannesri on 2012-08-19
After:
gconftool-2 --recursive-unset /apps/compiz-1
Unity is crashing and I had to kill x-Server

---

### Post by w201 on 2012-08-20
According to the source, you have to run all three commands.

---

