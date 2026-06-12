---
title: "Program start in terminal"
date: 2012-06-03
forum: General Help
---

### Post by z3rO88 on 2012-06-03
Hi, i been looking around the internet and don't know what it is called wondered if anybody can give me advice on where to go tutorial or anything be grateful.

1. I have a menu on my Ubuntu as shown below

[IMG]http://img40.imageshack.us/img40/3182/60978104.png[/IMG]


2. Now I want this program to automatically run in terminal by the menu, but when run it it doesn't load the program and don't understand why not, if can link to any tutorial or anything thanks :)

[IMG]http://img840.imageshack.us/img840/1451/66237601.png[/IMG]

---

### Post by mikewhatever on 2012-06-03
The command should look like this:
```
gnome-terminal -x sudo chkrootkit
```

..there is no need to spesify the full path.

Alternatively -> [http://ubuntuforums.org/showthread.php?t=1498339](http://ubuntuforums.org/showthread.php?t=1498339)

---

### Post by z3rO88 on 2012-06-03
thanks very much i been looking for this everywhere over net, didnt know what it was called

---

### Post by z3rO88 on 2012-06-03
> **mikewhatever said:**
> The command should look like this:
```
gnome-terminal -e sudo chkrootkit
```

..there is no need to spesify the full path.

Alternatively -> [http://ubuntuforums.org/showthread.php?t=1498339](http://ubuntuforums.org/showthread.php?t=1498339)

just tried it an still not working :(

---

### Post by mikewhatever on 2012-06-04
OK, I've got it. The command should be this
```
gnome-terminal -x sudo chkrootkit
```

---

### Post by z3rO88 on 2012-06-06
thanks very much it works yay! what are them type of commands called ?

---

### Post by anaconda on 2012-06-06
shouln't there be 
gksudo instead of regular sudo in that command?

the difference is that gksudo asks password graphically in a window, while sudo asks it in terminal (if terminal happens to be visible)

---

### Post by philinux on 2012-06-06
> **anaconda said:**
> shouln't there be 
gksudo instead of regular sudo in that command?

the difference is that gksudo asks password graphically in a window, while sudo asks it in terminal (if terminal happens to be visible)

chkrootkit is a shell script so sudo is fine.

---

### Post by z3rO88 on 2012-06-07
thank you for help :) very much appreciated

---

