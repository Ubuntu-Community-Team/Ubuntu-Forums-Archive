---
title: "File permissions"
date: 2006-02-06
forum: General Help
---

### Post by ockertom on 2006-02-06
Ok Have another drive with files on it, It is a ext3 partition, did a chown -R user /folder, can do all the make dirs and stuf, trouble is in my/Music folder 3/4 of the folders and files have a lock on them, I transfererred these files in my name not root, i did a sudo chmod 777 /Music but they are still locked,
 I really do not want to got through this folder and change every file with select all properties and click on write is there an easier way? Once I get this tidied up will be backing em up in nix format :)

---

### Post by Sutekh on 2006-02-06
[QUOTE=ockertom]sudo chmod 777 /Music [/QUOTE]
YOu should have done a
```
sudo chmod **-R** 777 /Music
```
The **-R** makes the chmod command recursive (does for all children folders)

---

### Post by ockertom on 2006-02-06
Groannn always forget one letter hell thanks mate, so changing to sudo and doin that wont work?

---

### Post by Sutekh on 2006-02-06
[QUOTE=ockertom]Groannn always forget one letter hell thanks mate, so changing to sudo and doin that wont work?[/QUOTE]
Changing to sudo?  

Without the **-R** you'll have to change each file/folder individually, witht he **-R** you just use chmod once.

---

