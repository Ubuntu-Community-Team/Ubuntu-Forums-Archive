---
title: "About ME!!"
date: 2010-11-25
forum: General Help
---

### Post by 2uRcJQ34G1 on 2010-11-25
Hello,

I have a very basic problem. Whenever I click on About Me(System->Preferences), I cannot see any information editing window. However, the mouse pointer does show the system is budy doing something, nothing shows up and then the pointer returns to default as if the system is no longer busy. What can I do to change my personal info?

Cheers.

---

### Post by howefield on 2010-11-25
Try starting it from a terminal, you might get a clue in the output as to what is wrong.

The command is

```
gnome-about-me
```

---

### Post by WorMzy on 2010-11-25
Can you open a terminal and run
```
gnome-about-me
```

If it spurts out an error message, post it here; preferably within code tags.

---

### Post by 2uRcJQ34G1 on 2010-11-25
This is the error I get:


(gnome-about-me:3994): libebook-WARNING **: e-book.c:2229: cannot activate book: Failed to execute program /usr/lib/evolution/e-addressbook-factory: Success


(gnome-about-me:3994): libebook-WARNING **: e-book.c:2229: cannot activate book: Failed to execute program /usr/lib/evolution/e-addressbook-factory: Success


about-me-properties-ERROR **: Failed to execute program /usr/lib/evolution/e-addressbook-factory: Success
aborting...
Aborted

---

### Post by howefield on 2010-11-25
Have you uninstalled Evolution by any chance ?

---

### Post by WorMzy on 2010-11-25
Strange error..

Try reinstalling evolution-data-server.

```
sudo apt-get install --reinstall evolution-data-server
```

---

