---
title: "Program install problem"
date: 2011-02-26
forum: General Help
---

### Post by dwoodyatt on 2011-02-26
I recently installed Ubuntu 10.10 on a new computer, no other OS.  Everything was going fine until now.  When I try to install packages from the Software Center it asks me to authenticate, no problem, then I get a dialog box that says "Requires installation of untrusted packages" and will not continue. If I remember before I would click OK and it would install.

---

### Post by thefasterblueone on 2011-02-26
Try running:

```
sudo apt-get update
```

---

### Post by dwoodyatt on 2011-02-26
when I do apt-get update I get:
E: The method driver /usr/lib/apt/methods/deb-ftp// could not be found.
E: The method driver /usr/lib/apt/methods/deb-src-ftp could not be found.
E: The method driver /usr/lib/apt/methods/deb-ftp// could not be found.

---

### Post by thefasterblueone on 2011-02-26
Ok. try this:

```
sudo dpkg --configure -a
```

---

### Post by dwoodyatt on 2011-02-28
> **thefasterblueone said:**
> Ok. try this:

```
sudo dpkg --configure -a
```


Solved--Thanks

---

