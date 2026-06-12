---
title: "Which flash for firefox, ubuntu 10.04 64bit"
date: 2010-07-05
forum: General Help
---

### Post by Ojustaboo on 2010-07-05
Hi people.

Running 10.04 Ubuntu desktop.  

When on a website that requires flash, it gives me the choice of three.

Adobe Flash
Swfdec SWF player
Gnash SWF Player

Which one do you recommend please?

Thanks

---

### Post by howefield on 2010-07-05
I would recommend installing flashplugin-installer with Synaptic Package Manager which will install a 32 bit version of Adobe flash.

If you go down this route and have problems with the buttons, you might need to do the following. 

In terminal type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
``` 

and add the following before the last line.

```
export GDK_NATIVE_WINDOWS=1
```

---

### Post by Ojustaboo on 2010-07-05
Many thanks for the quick and helpful response.

---

### Post by cpmman on 2010-07-05
Go to Tools in Firefox and install Flash-aid

---

### Post by Ojustaboo on 2010-07-05
Many thanks

---

