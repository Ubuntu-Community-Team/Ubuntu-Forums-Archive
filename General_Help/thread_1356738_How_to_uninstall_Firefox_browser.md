---
title: "How to uninstall Firefox browser"
date: 2009-12-16
forum: General Help
---

### Post by kyqinqiqin on 2009-12-16
Now I didn't thinking using Firefox browser in ubuntu. But I don't how to uninstall.
Where it is in the floder? What's the file of name? - -!

---

### Post by whiteychs on 2009-12-16
apt-get remove firefox

From what I remember with my quick stint with Ubuntu, I believe that should work.

---

### Post by Wardje on 2009-12-16
You can open a terminal and type:
```
sudo apt-get remove firefox
```
or remove firefox in the software center
or in synaptic package manager

---

### Post by philinux on 2009-12-16
> **whiteychs said:**
> apt-get remove firefox

From what I remember with my quick stint with Ubuntu, I believe that should work.

```
sudo apt-get remove firefox
```

Why bother uninstalling it. Hardly uses much disk space.

---

### Post by whiteychs on 2009-12-16
> **philinux said:**
> ```
sudo apt-get remove firefox
```

Why bother uninstalling it. Hardly uses much disk space.

Ah, I should have figured a default user didn't have sufficient rights.

---

### Post by shaon3343 on 2009-12-16
I think this should work
sudo apt-get purge firefox-3.5 

to do this in a different way you can go to system--> admin--> synaptic package manager , and search for "firefox" and remove it.

---

### Post by shaon3343 on 2009-12-16
I think this should work
sudo apt-get purge firefox-3.5 

to do this in a different way you can go to system--> admin--> synaptic package manager , and search for "firefox" and remove it.

---

### Post by heyniceaddress on 2009-12-16
Hmm

---

