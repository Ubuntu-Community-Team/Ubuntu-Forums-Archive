---
title: "How to remove an item from Update Manager"
date: 2011-05-11
forum: General Help
---

### Post by Finlandia on 2011-05-11
Hi!

I have Ubuntu 11.04 Finnish. There's Update Manager and a subtitle called "Jakelupäivitykset" - I guess it's "Distribution Updates" in English. Well, below this title are the following lines:

-----
**Transitional dummy package to mame-tools**
sdlmame-tools (Size: 8 kb)
-----

I'm not longer mame user but this line will always appear to the update manager. I can't choose it because the checkbox is disabled. But how can I remove this line?

Thanks beforehand!

-Finlandia.

---

### Post by ianc1 on 2011-05-11
Does it go if you run the following at the command line:```
sudo apt-get purge mame
```Only do this if you are sure you no longer wish to use it.

As far as I am aware this will wipe it from your system.  If the update is related to this package it should disappear.

---

### Post by mcduck on 2011-05-11
> **Finlandia said:**
> Hi!

I have Ubuntu 11.04 Finnish. There's Update Manager and a subtitle called "Jakelupäivitykset" - I guess it's "Distribution Updates" in English. Well, below this title are the following lines:

-----
**Transitional dummy package to mame-tools**
sdlmame-tools (Size: 8 kb)
-----

I'm not longer mame user but this line will always appear to the update manager. I can't choose it because the checkbox is disabled. But how can I remove this line?

Thanks beforehand!

-Finlandia.
You still have that package installed ( you probably didn't uninstall all dependencies of Mame when you removed Mame itself. Running "*sudo apt-get autoremove*" in a terminal should fix that). 

Since you aren't that package any more, just uninstall it and you won't get updates for it.

The package management will always check for updates for every package you have installed, and while there *is* a way to stop updates for a certain package it can usually be assumed that if you have a package installed, you also want to keep it updated (or otherwise you'd uninstall it). Forcing the package to stay at current version would only make sense if you had problems with an updated version of a package you need.

---

### Post by Finlandia on 2011-05-13
> **ianc1 said:**
> ```
sudo apt-get purge mame
```

Thanks!

Indeed, the right command was:

```
sudo apt-get purge sdlmame-tools
```But the incorrect line is now away.


-Finlandia.

---

