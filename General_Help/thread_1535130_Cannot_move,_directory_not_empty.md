---
title: "Cannot move, directory not empty?"
date: 2010-07-20
forum: General Help
---

### Post by fred2028 on 2010-07-20
I'm trying to move a folder via

sudo mv ioncube /usr/local/bin/

but it says something cannot move since directory is not empty. What do I do now?

---

### Post by gordintoronto on 2010-07-20
gksudo nautilus

---

### Post by philinux on 2010-07-20
> **fred2028 said:**
> I'm trying to move a folder via

sudo mv ioncube /usr/local/bin/

but it says something cannot move since directory is not empty. What do I do now?

It should probably go in /opt directory

---

### Post by fred2028 on 2010-07-21
> **gordintoronto said:**
> gksudo nautilus
 What do I do after that?
> **philinux said:**
> It should probably go in /opt directory
 You sure that will work? I am following this guide
 
[http://ubuntuforums.org/showthread.php?t=1068139](http://ubuntuforums.org/showthread.php?t=1068139)

---

### Post by wojox on 2010-07-21
Why don't you copy it for now to be on the safe side:

```
sudo cp -r ioncube /usr/local/bin/
```

---

### Post by fred2028 on 2010-07-21
> **wojox said:**
> Why don't you copy it for now to be on the safe side:
 
```
sudo cp -r ioncube /usr/local/bin/
```
 OK thanks, that worked!

---

