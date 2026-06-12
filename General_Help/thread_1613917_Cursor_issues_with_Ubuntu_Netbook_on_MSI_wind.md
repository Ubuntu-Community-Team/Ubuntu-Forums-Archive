---
title: "Cursor issues with Ubuntu Netbook on MSI wind"
date: 2010-11-05
forum: General Help
---

### Post by alexmoon on 2010-11-05
My friend is using the latest ubuntu netbook edition on her MSI wind, and is having some serious trackpad issues. The cursor occasionally starts working oddly, as if the left click is being held down, or the left click won't work at all. Are there software issues that I should be looking for here? I've googled and looked around the boards, but I can't work out where to start. Any advice would be most appreciated!

---

### Post by P4man on 2010-11-05
If that is one of those wind;'s with the dreaded sentelic touchpad, you could try these:
[http://sourceforge.net/projects/fsp-lnxdrv/files/](http://sourceforge.net/projects/fsp-lnxdrv/files/)

You can check if those are correct for your machine by opening a terminal and running

```
lsusb
```

or ```
lspci
```

and find the touchpad. It should be a sentilic STL388x. If its not, report the output of the above commands.

---

