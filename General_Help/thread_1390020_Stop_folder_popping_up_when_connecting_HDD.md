---
title: "Stop folder popping up when connecting HDD"
date: 2010-01-25
forum: General Help
---

### Post by thedon_1 on 2010-01-25
I have an external hard drive that i keep my media on for use with XBMC.

The problem is that when media centre is on and i attach the hard drive, Ubuntu's file browser pops up with the contents of my drive and this is over XBMC.

When using a remote i am left stuck as i can't alt+tab out of the file browser.

How do i disable this?

---

### Post by thedon_1 on 2010-01-25
bump

---

### Post by thedon_1 on 2010-01-25
Anything?

---

### Post by jocko on 2010-01-25
Try this:
1. To open gconf-editor, run this in a terminal:
```
gconf-editor
```2. Disable the key apps/nautilus/preferences/media_automount_open.

---

### Post by danastasio on 2010-01-25
or add an entry in your /etc/fstab file with the noauto option.

---

### Post by gadolinio on 2010-01-25
If i get it correctly, you want ubuntu to refrain from opening the file browser when you insert a new media. 
If this is the case, open the file browser, go to edit menu, then preferences. A window showing some tabs will appear. Go to the last one; at the bottom there's a check-box saying something like  "examine media after being introduced". Uncheck that box, close the window, and that's it.
Hope you fin this useful...

---

### Post by thedon_1 on 2010-01-25
Thanks guys, i appreciate it

---

