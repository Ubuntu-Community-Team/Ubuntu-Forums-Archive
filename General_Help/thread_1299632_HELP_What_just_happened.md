---
title: "HELP: What just happened???"
date: 2009-10-24
forum: General Help
---

### Post by WolfyAU82 on 2009-10-24
I've just installed the 64bit Kubuntu 9.10 RC and bashed this in...

```
sudo apt-get install evolution
```

Does this mean Evolution Mail installs onto my system?

---

### Post by cameronedwards on 2009-10-24
yep as far as i know. still you should search it to make sure that the program is on the cache first

```
apt-cache search evolution
```

---

### Post by infinitejones on 2009-10-24
It should do... it will install a lot of other stuff too because Evolution is a Gnome application that uses a lot of extra packages that wouldn't have been installed in Kubuntu yet. But once it's all finished doing what it's doing, Evolution should be installed.

Why not give it a go... if it's not what you want or it doesn't work, you can always do
```
sudo apt-get remove evolution
```
to remove the main evolution package, and then
```
sudo apt-get autoremove
```
to remove the extra Gnome packages that are no longer needed.

---

