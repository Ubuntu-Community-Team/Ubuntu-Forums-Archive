---
title: "How to Disable the Insert key"
date: 2011-03-20
forum: General Help
---

### Post by plm.qwer on 2011-03-20
Sometimes the Insert key can be VERY annoying in the following sense:

1. It is close to the Delete and Home key (in many keyboards, not all), so chances are that it often gets mis-pressed. This also depends on how the keyboard is designed. Maybe a good design can avoid such kind of mis-pressing (even with the same layout).

2. A mis-pressing of the Insert key can be VERY disastrous (you can imagine, e.g. when used in command line during a 'rm' process in a rush), although this happens very rarely.

I did not find any option to disable this key in the system configuration, although it seems possible to do this by installing a plugin. But it is not difficult to add such an option in the keyboard setting panel, right? I must say that the current 'keyboard layout options' panel is already quite messy, although I don't know the meanings of most of them.

---

### Post by Krytarik on 2011-03-20
I don't know how to really *unset* a key, meaning that it would have no function at all, if that is possible at all. But how about just mapping it also to the "Delete" key function instead?
```
xmodmap -e "keysym Insert = Delete"
```
You can add those command either system-wide to "/etc/rc.local" or just to your "Startup Applications".

---

