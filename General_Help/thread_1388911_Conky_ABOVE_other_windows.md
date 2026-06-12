---
title: "Conky ABOVE other windows"
date: 2010-01-23
forum: General Help
---

### Post by TheNessus on 2010-01-23
Heyas.

How do I make conky be above other windows, instead of below?

thanks :)

---

### Post by scouser73 on 2010-01-23
You're better off asking that here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by TheNessus on 2010-01-23
> **scouser73 said:**
> You're better off asking that here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

way ahead of ya buddy :)
though, asking in both places might be good as well.

---

### Post by Ginsu543 on 2010-01-23
Give this a try. In your .conkyrc file (or whichever config file you have conky call at startup), there should be a setting called "own_window_hints". Try setting this to "undecorated,**above**,sticky,skip_taskbar,skip_pager" (without quotes or bold). This also requires you to have "own_window" set to "yes".

---

