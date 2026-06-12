---
title: "Problems moving file"
date: 2009-07-17
forum: General Help
---

### Post by diggedy on 2009-07-17
I created a backup of my system onto a seperate drive in my pc following [ this guide]("http://ubuntuforums.org/showthread.php?t=35087"). Im now trying to move it to the root of my ubuntu installation to carry out a restore but it wont allow me to move it as it says I dont have permission.

Ive tried logging in as root but that hasnt made a difference. Anyone any ideas whats wrong?

---

### Post by Cityscape on 2009-07-17
I've had the same problem...

---

### Post by michy99 on 2009-07-17
What is the exact command you are using and what is the error message?

---

### Post by diggedy on 2009-07-17
im trying to move it using nautilus, dragging and dropping

---

### Post by michy99 on 2009-07-17
Did you open nautilus as root?```
gksudo nautilus
```Note: You can do a lot of damage using nautilus as root. It is best to close it as soon as you have done what you need to.

---

### Post by diggedy on 2009-07-17
it wont allow me to do that, brings up a full screen of errors about how it cant connect to the running instance (nautilus isnt running as im trying this)

---

### Post by diggedy on 2009-07-17
ignore the last one. I booted into a clean install and it ran fine, it must be some widget I have open affecting it.

This worked by the way, much appreciated

---

