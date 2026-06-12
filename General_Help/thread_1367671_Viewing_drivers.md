---
title: "Viewing drivers"
date: 2009-12-29
forum: General Help
---

### Post by Nameo0 on 2009-12-29
I just switched to ubuntu and was wondering how you could view the drivers that are installed like you can do in windows by going to "device manager" if it is even possible.

---

### Post by RedSingularity on 2009-12-29
Are you looking for a list of hardware or something like that?

---

### Post by SIGTERMer on 2009-12-29
technically, they're called kernel modules. and there are a lot of them pre-installed with your system. mine has 1939, most of which you'll never use. the kernel only loads the modules it needs for your hardware.

To list all the modules in your system, open a terminal and enter:
```
modprobe -l | less
```

But perhaps your more interested in the modules actually being used by your system. in that case, type:
```
lsmod | less 
```

I'm pretty sure there was a nice GUI for that, but i can't seem to remember what it was.

Hope that helped
Sulaiman

---

