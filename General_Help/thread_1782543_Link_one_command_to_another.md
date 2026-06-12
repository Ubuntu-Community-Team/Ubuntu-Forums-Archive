---
title: "Link one command to another"
date: 2011-06-14
forum: General Help
---

### Post by Concrete Pants on 2011-06-14
Hi! I found somewhere, ages ago, that there is a way to link a terminal command to run a different command... but I have no idea what it was called and all my searches keep finding how to make symbolic links.

What I'm trying to achieve is if you run $foo, the terminal will instead run $~/foo.sh

I would like this to be able to create links between the command $blender and my blender 2.5 installation which is buried in my home folder.

Anyone have any ideas? Ta

---

### Post by blueridgedog on 2011-06-14
```
ln -s /path/to/blender /path/to/location/you/want/it/to/be
```

See "man ln" for more information.

Good luck.

---

### Post by ngrieb on 2011-06-14
Um, like aliasing? alias foo='~/foo.sh'

---

### Post by Concrete Pants on 2011-06-14
> **ngrieb said:**
> Um, like aliasing? alias foo='~/foo.sh'

Haha! :D Thats exactly what I'm after, thank you!

---

