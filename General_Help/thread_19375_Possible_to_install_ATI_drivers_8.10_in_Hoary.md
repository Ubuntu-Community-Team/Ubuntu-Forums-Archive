---
title: "Possible to install ATI drivers 8.10 in Hoary?"
date: 2005-03-11
forum: General Help
---

### Post by merc on 2005-03-11
I just read a thread in which the Ubuntu devs said that there has been a freeze on Hoary packages, and the newly released ATI drivers, 8.10, will not be included in Hoary, or as an upgrade to Hoary.

I'm not very experienced with linux, and was wondering if there is a way for me to install the new version driver on my computer running Hoary. Since there're well documented ways of installing the ATI drivers in Warty (which Warty officially does not support), I'm assuming there shouldn't be a problem installing the newer ATI drivers under Hoary (which Hoary officially does not support).

If there is, could someone please tell me how? Should I follow the same steps as installing it under Warty (i.e by downloading the rpm from ATI, and running alien) ?

---

### Post by bobmitch on 2005-03-11
[QUOTE=merc]I just read a thread in which the Ubuntu devs said that there has been a freeze on Hoary packages, and the newly released ATI drivers, 8.10, will not be included in Hoary, or as an upgrade to Hoary.

I'm not very experienced with linux, and was wondering if there is a way for me to install the new version driver on my computer running Hoary. Since there're well documented ways of installing the ATI drivers in Warty (which Warty officially does not support), I'm assuming there shouldn't be a problem installing the newer ATI drivers under Hoary (which Hoary officially does not support).

If there is, could someone please tell me how? Should I follow the same steps as installing it under Warty (i.e by downloading the rpm from ATI, and running alien) ?[/QUOTE]

Yup, rpm -> deb conversion is the easiest way.

See my dirty guide [here](http://www.ubuntuforums.org/showpost.php?p=73422&postcount=4)

---

### Post by Goochi on 2005-03-15
I followed those steps I believe I succeeded. How can I see or test they are actually installed and working now ? Thanks.

---

### Post by bobmitch on 2005-03-15
[QUOTE=Goochi]I followed those steps I believe I succeeded. How can I see or test they are actually installed and working now ? Thanks.[/QUOTE]

Use **fglrxinfo**.

If there is mention of Mesa Gl anywhere, you do not have hardware 3d accel.
If it says something like opengl vendor ATI technologies, or something similar, then you are good to go.

---

### Post by Goochi on 2005-03-15
I got this as return.

```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

### Post by bobmitch on 2005-03-15
See my reply in the other ati thread you started for guidance.  I don`t think you removed all existing fglrx drivers from ubuntu before attempting to install the new drivers.

---

### Post by Seatux on 2005-03-16
What's the exact kernel name for the AMD K7 series (on athlon XP)? I'm not too sure about it.  I need to know about it so i can follow the dirty guide.

---

