---
title: "How to delete all files in a folder"
date: 2009-10-23
forum: General Help
---

### Post by UltraZone on 2009-10-23
I want to empty the contents of the folder /var/log/bootchart/ 

The only way I know is to delete files individually via sudo rm, but after restarting my computer 50 times now this folder is full of stuff and I just want to know how to empty all the files (they're just png files) all at once.

Much appreciated.

---

### Post by rockstarrem on 2009-10-23
Why can't you use sudo rm? 

```

sudo rm /var/log/bootchart/ *

```

The * at the end says to delete all of them.

---

### Post by UltraZone on 2009-10-23
that worked albeit without the space between the last / and the * .

This should be part of the ss64.org description of the rm command. :popcorn:

---

### Post by Bucky Ball on 2009-10-23
Unless you're a terminal junky, the simplest is:

```
sudo nautilus
```

Find the folder you want to empty and kill the files.

---

