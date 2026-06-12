---
title: "Remove Trash from desktop"
date: 2011-05-17
forum: General Help
---

### Post by borth92 on 2011-05-17
After an update on Ubuntu 11.04 with Gnome 3-Shell: My trash, computer, and home folder are all mounted to the desktop. I cannot find the correct spot in gconf-editor on my own to turn this off. Anyone know how to disable them?

---

### Post by ajgreeny on 2011-05-17
Look in **gconf-editor >apps >nautilus >desktop** and remove the selections that you don't want.

---

### Post by borth92 on 2011-05-18
apps>nautilus>desktop doesn't exist. unter apps>nautilus, all there is is Desktop Metadata and preferences.

---

### Post by borth92 on 2011-05-18
bump

---

### Post by wojox on 2011-05-18
I thought they are in dconf-editor. To install it:

```
sudo apt-get update; sudo apt-get install dconf-tools
```

---

### Post by borth92 on 2011-05-19
Can't seem to find anything in dconf-editor either...

---

### Post by ajgreeny on 2011-05-19
This must be yet another of those changes that makes **unity** and **gnome 3** baffling and unusable to me at the moment.

---

### Post by wojox on 2011-05-19
> **borth92 said:**
> Can't seem to find anything in dconf-editor either...

Maybe it's gnome-tweak-tool. I haven't used Gnome3/Shell in a while.

---

### Post by benerivo on 2011-05-19
Try dconf-editor with org>nautilus>desktop

---

### Post by borth92 on 2011-05-19
got it, it was dconf-editor: org>gnome>nautilus>desktop

---

### Post by matey3 on 2011-05-19
> **ajgreeny said:**
> Look in **gconf-editor >apps >nautilus >desktop** and remove the selections that you don't want.

Thanks for this Useful Post! 
T-up!:cool:

---

