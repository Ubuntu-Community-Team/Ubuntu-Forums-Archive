---
title: "Aptitude wants to remove GNOME"
date: 2009-11-19
forum: General Help
---

### Post by GCoffee on 2009-11-19
Hi,

no idea what I did, but I uninstalled some programs I don't use anymore, and then suddenly the whole GNOME went wierd, like add/remove being taken off menu and stuff.

So I went to aptitude, and in basic it says:

My whole gnome installation to be removed because it is no longer being used

then I hit something else by accident and the 230 packages has (worryingly) gone down to 52 to be removed

I don't know if they've been removed already or what..

Any help appreciated, specifically on how to get these packages off the "to be removed" list.

Cheers,
GC.

---

### Post by SPr on 2009-11-19
```

sudo aptitude keep-all

```

---

### Post by GCoffee on 2009-11-19
Ok, thanks, no errors turned up after running dpkg --configure -a

DO I reboot now.. or logout or something?

Cheers,
GC.

---

### Post by SPr on 2009-11-19
There's no need. Just carry on with what you were doing.

---

### Post by GCoffee on 2009-11-19
Ok, but the menu hasnt changed yet :S

---

### Post by GCoffee on 2009-11-19
As in:

terminal wont launch from menu, but firefox will, and some stuff is missing off it like add/remove programs.

---

### Post by SPr on 2009-11-19
> **GCoffee said:**
> Ok, but the menu hasnt changed yet :S

In that case I would suggest backing up Ubuntu (search the forums for backup solutions) and try
```

sudo aptitude reinstall gnome-core 

```
If that somehow makes things worse you'll still have the backup to return to the previous state.

I don't know what you uninstalled or even how you uninstalled it but you will always get warnings about other packages that will be removed when uninstalling programs. If you have *any* doubt about what is to be removed do not remove them.

A backup made before removing the programs would have saved you time.

---

### Post by GCoffee on 2009-11-19
Yeah, I didn't realise uninstalling inkscape would have quite so many damaging effects, inkscape and a few cd and media tools I didn't need.

---

### Post by GCoffee on 2009-11-19
When I typed sudo aptitude reinstall gnome-core it said not installed, so i'm installing it now.

This is actually a server install, but I installed gnome for the sake of usability.. It was all working fine before though.

Anyway, hopefully this'll sort it :)

---

