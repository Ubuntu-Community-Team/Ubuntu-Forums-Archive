---
title: "How do I get rid of Nepomuk?"
date: 2010-05-30
forum: General Help
---

### Post by Rytron on 2010-05-30
Hi.
I don't know what program Nepomuk came with. I thought I got rid of it but this keeps popping up on startup [picture attached].

---

### Post by germanix on 2010-05-30
No expert on this, but as far as I know this is part of the Semantec desktop integrated into KDE. It is integrated into kdelib and kdebase. You should be able to find it under your installed software packages and remove it.

---

### Post by Rytron on 2010-05-31
I notice that removing Nepomuk in Synaptic caused many other programs to be removed.

Instead I ran this and removed the item that had Nepomuk:
 
```
gksudo nautilus /usr/share/autostart
```

All seems okay now!

---

### Post by Rytron on 2010-05-31
Well that didn't work. The blasted Nepomuk thing is again popping up when I log in! ::mad:

---

### Post by Rytron on 2010-06-02
Is there any way to banish this Nepomuk and not interfere with other KDE programs. I never saw this silly Nepomuk program in previous versions on Ubuntu!

I have noticed it in System Monitor under the processes tab. I stopped/killed it and it has not bothered me since!

---

