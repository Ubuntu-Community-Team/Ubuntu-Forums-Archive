---
title: "Cannot &quot;Click To Make Changes&quot;"
date: 2010-01-08
forum: General Help
---

### Post by JackRock on 2010-01-08
I am trying to do a few items with the Users Settings, and I would like to change a few of them.  I try to click on the button that says "Click to Make Changes" (see attached screenshot), but it does nothing.

In 9.04, IIRC, it asked me for my password and then let me make the changes.  In 9.10, it doesn't do a thing.  Am I doing something wrong?

---

### Post by JackRock on 2010-01-12
Can anybody help on this one?

---

### Post by Leppie on 2010-01-12
try completely removing the system tools: 
```
sudo apt-get purge gnome-system-tools 
sudo apt-get install gnome-system-tools
```

on some systems it seems to install with some problems, reinstalling (completely remove and then install) may solve it.

---

### Post by JackRock on 2010-01-16
Thanks for the tip, but it didn't work.  I'll probably just deal with it (I can still get around it by opening it with gksudo in the terminal).  I'll do a complete clean install with Lucid, when it's out of testing.

---

