---
title: "Cannot install any programs"
date: 2010-07-21
forum: General Help
---

### Post by xpowerfulxx on 2010-07-21
The attachment. I don't remember any updater running before it. It also shows something similar when I try to install a .deb

---

### Post by oldos2er on 2010-07-21
```
sudo dpkg --configure -a
```

---

### Post by xpowerfulxx on 2010-07-22
Worked, but now I get this.

[IMG]http://img823.imageshack.us/img823/8530/butnow.png[/IMG]

---

### Post by nothingspecial on 2010-07-22
A guess here.

You installed ubuntu-restricted-extras and when you got to the bit where you have to accept the java lisence you cancelled it.

Try ```
sudo apt-get install -f
```

When you get to the java bit you have to press the Tab key to move the cursor to "Yes" or "Accept" or whatever it says.

---

### Post by xpowerfulxx on 2010-07-22
> **nothingspecial said:**
> A guess here.

You installed ubuntu-restricted-extras and when you got to the bit where you have to accept the java lisence you cancelled it.

Try ```
sudo apt-get install -f
```When you get to the java bit you have to press the Tab key to move the cursor to "Yes" or "Accept" or whatever it says.
Oh haha when I got to it I tried clicking normally and it didn't work :o

---

