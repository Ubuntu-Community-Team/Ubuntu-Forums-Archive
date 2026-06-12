---
title: "Docky issues, messes up screen."
date: 2011-02-24
forum: General Help
---

### Post by MourningsEnd on 2011-02-24
Well look at attachment..how can I stop that?

---

### Post by wiggly81 on 2011-02-24
you need to enable composting, if your graphics card allows for it

[http://ubuntuforums.org/showthread.php?t=1467570&page=1](http://ubuntuforums.org/showthread.php?t=1467570&page=1)

[http://setupguides.blogspot.com/2010/10/fixing-docky-compositing-error-in.html](http://setupguides.blogspot.com/2010/10/fixing-docky-compositing-error-in.html)

those links may help you

---

### Post by MourningsEnd on 2011-02-24
Didn't work..thank you though.

I guess I'll just uninstall it.

---

### Post by MARP1961 on 2011-02-24
Install AWN and try that out.

---

### Post by Habitual on 2011-02-24
Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!

Done.

---

### Post by Habitual on 2011-02-24
> **MARP1961 said:**
> Install AWN and try that out.

Not really an answer b/c AWN needs compositing also, at least if you want a semi-transparent dock.

-1

---

### Post by wiggly81 on 2011-02-24
simDock runs without compositing if that is of any help

---

### Post by MourningsEnd on 2011-02-24
simDock was horrible...

gconf-editor didn't work in Run? :s  Man nothing ever works for me. D:

---

### Post by wiggly81 on 2011-02-24
have you checked to see if you have any additional drivers that need to be activated there could be a graphics driver that needs installing/activating, this could solve the issue..

go to: 
System > Administration > Additional Drivers

---

### Post by MourningsEnd on 2011-02-24
All that is there is my GeForce 8400 GS Drivers.

There's the Recommended one(I have that one installed) and the Version 173 one.

---

### Post by Habitual on 2011-02-24
Just turn on Desktop Effects.

---

### Post by MourningsEnd on 2011-02-24
How do I do that?

Sorry, I'm new to Linux; says on Forums there is no stupid question so... :)

---

### Post by MourningsEnd on 2011-02-25
Bump?

---

### Post by MARP1961 on 2011-02-26
I repeat, try AWN. It installed on my seven year old desktop and worked well. Granted it is a simple 2D dock, nothing fancy but it works without any special desktop effects (which my graphics hardware can't cope with anyway).

---

