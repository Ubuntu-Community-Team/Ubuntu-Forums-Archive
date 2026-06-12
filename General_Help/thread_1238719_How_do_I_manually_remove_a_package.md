---
title: "How do I manually remove a package?"
date: 2009-08-12
forum: General Help
---

### Post by Atomic Fusion on 2009-08-12
Like, I don't want to remove this package using apt-get, I want to delete the files from the file system myself. I know that I would remove every file that is added from the data.tar.gz inside the .deb, but other stuff is added, the content file, and there is a listing for Synaptic somewhere, where would I go/ what would I do to remove these?

Thanks,
Stephen

---

### Post by scouser73 on 2009-08-13
Use this command: **sudo apt-get remove --purge "Package Name"**

---

### Post by Keith Hedger on 2009-08-13
Removing files manually is probably not a good idea but if you need to know what was installed and where open synaptic select the package and got to Package->Properties->Installed Files for a complete list of what was put where.

---

### Post by CatKiller on 2009-08-13
> **Atomic Fusion said:**
> Like, I don't want to remove this package using apt-get, I want to delete the files from the file system myself.

Why? It seems like unnecessary work to me.

> **Keith Hedger said:**
> Removing files manually is probably not a good idea but if you need to know what was installed and where open synaptic select the package and got to Package->Properties->Installed Files for a complete list of what was put where.

+1

Or ```
dpkg -L *packagename*
``` if you want to do it from the command line.

---

