---
title: "No xmodmap.it file!"
date: 2006-06-20
forum: General Help
---

### Post by Neo Ex on 2006-06-20
Hi. I have installed XGL, and some keys doesn't work (AltGr, the /, * and - buttons on the keypad etc.). I've read I have to issue
```
xmodmap /usr/share/xmodmap/xmodmap.it
```
at Compiz startup, but... I don't have /usr/share/xmodmap/xmodmap.it! So, it doesn't work.
I know there is another command,
```
setxkbmap -model pc105 -layout it -variant basic
```
but I get
```
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault
```
What can I do? It's not a big problem, but I would like to write [, ] and @ without doing copy-paste...
Thanks.

---

### Post by Neo Ex on 2006-06-20
Nobody can help me?

---

### Post by firehead on 2006-06-21
install **gnome-applets-data** et voilà, you'll get plenty of xmodmap files installed into /usr/share/xmodmap...have fun.

---

