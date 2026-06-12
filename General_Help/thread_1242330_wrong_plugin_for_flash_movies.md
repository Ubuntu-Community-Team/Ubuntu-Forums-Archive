---
title: "wrong plugin for flash movies"
date: 2009-08-17
forum: General Help
---

### Post by Arminius on 2009-08-17
hey, I can't click on the manual button at [http://wow.curse.com](http://wow.curse.com)

adobe flash plugins are trying to use Swfdec SWF player, when I tell it to use adobe SWF player, it always reverts back to Swfdec which clearly doesn't seem to work.

so any ideas as to the solution?

---

### Post by Tclarkie on 2009-08-17
is it a prob with flash

---

### Post by Arminius on 2009-08-17
well all other flash videos are working fine?

---

### Post by Post Monkeh on 2009-08-17
if you have more than 1 flash player installed, it could be causing problems.

try putting this in a terminal.

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

---

### Post by Arminius on 2009-08-17
thanks it's working fine now

---

### Post by lovinglinux on 2009-08-17
For future reference...

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

