---
title: "can't remove splashy"
date: 2009-09-20
forum: General Help
---

### Post by pickarooney on 2009-09-20
I tried to use splashy but it just doesn't work properly (doesn't adapt to screen size etc.). So I tried removing it via sudo apt-get remove. I then reinstalled usplash.
Splashy says it's removed but when I boot I still get a message that /etc/rcS.d/035splashy cannot fine /sbin/splashy and it defaults to verbose mode.

How can I get rid of all trace of splashy?

---

### Post by SlugSlug on 2009-09-20
you could try 
```
 sudo update-rc.d -f splashy remove 

```


also whats does this look like..

```
cat /boot/grub/menu.lst

```

---

### Post by pickarooney on 2009-09-26
I ran that and on reboot my system was completely screwed up: Loads of illegql file  errors and nothing will mount. Need to reformat now. cheers

---

