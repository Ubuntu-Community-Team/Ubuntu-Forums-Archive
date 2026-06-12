---
title: "unistall whole program?"
date: 2011-06-11
forum: General Help
---

### Post by shooninjo on 2011-06-11
Hey. I wonder if there is a way to completely remove all packaged that were installed during an installation of a program or do you manually need to remove them all? I mean if I delete the program some packaged just as "lib" and "data" is still there, and I don't want to accidentally delete anything that I wasn't supposed to delete aswell, so is there a way to just delete everything that was installed from the beginning?

---

### Post by 3rdalbum on 2011-06-11
The packages that get pulled in as dependencies get marked as such, and the "orphaned packages" can be removed using a simple command:

```
sudo apt-get autoremove
```

Check the list of what it's going to delete BEFORE pressing the 'y' key, very occasionally it makes mistakes. If you find a package in there that you want to keep, just mark it as manually installed by running:

```
sudo apt-get install packagename
```

Then run the autoremove command again.

---

