---
title: "Ubuntu 9.10 problem with update"
date: 2010-08-25
forum: General Help
---

### Post by DachaArh on 2010-08-25
I had a problem with update few days ago, among other updates, it was Firefox update, so I selected it too. But update manager stoper at same spot for half hour: setting up firefox..... and no movement, so I closed it...

Now I have new updates coming up and I cant update, I have this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


when I run sudo dpkg --configure -a via terminal I get this error :

> Setting up firefox (3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2~karmic) ...
^Cdpkg: error processing firefox (--configure):
 subprocess installed post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 firefox


so you see I cant update anymore....


any help, please...?

---

### Post by dabl on 2010-08-25
I would try (in the terminal) a sequence of:

```
sudo apt-get update
```

```
sudo apt-get autoclean
```

If it does not put up errors, then try again with 

```
sudo dpkg --configure -a
```

If it still gives the error, then try:

```
sudo apt-get install -f
```

and that might take it the rest of the way.  Then you might as well:

```
sudo apt-get upgrade
``` to make sure you have whatever else is in the queue for your packages.

---

