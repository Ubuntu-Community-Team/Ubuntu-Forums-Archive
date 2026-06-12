---
title: "How To Fix - Vuze Not Opening"
date: 2010-10-02
forum: General Help
---

### Post by Maheriano on 2010-10-02
I finally got a minute to look into this and found a fix for it which worked on both of my machines. There's a known bug that upgrading to the latest version of Ubuntu breaks the operation of Vuze so here's how to fix it. Type the following into a console and hit enter after each one.

```
sudo apt-get remove libswt-gtk-3.5-java
```
```
sudo apt-get install libswt-gtk-3.5-java
```
```
sudo apt-get install vuze
```

And you're done. It'll work from now on.

---

