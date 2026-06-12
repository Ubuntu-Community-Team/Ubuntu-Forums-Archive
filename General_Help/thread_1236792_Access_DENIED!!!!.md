---
title: "Access DENIED???!?!?!?!"
date: 2009-08-10
forum: General Help
---

### Post by ArmenianLeader4 on 2009-08-10
I'm trying to move some GIMP brushes and Python scripts into folders like ```
~/usr/share/blender/scripts/blender
``` and when I do it by just click and drag it says permission denied. I also tried using the command```
 mv ~/Documents/Python/ script.py ~/usr/share/blender/scripts/blender
``` the feedback it gives is ```
~/usr/share/blender/scripts/blender is not a directory
```

any ideas?
i just want to be able to use GIMP and blender the way I want ! >:O

---

### Post by wojox on 2009-08-10
Open a terminal:
```
gksudo nautilus
```

Then your root.

---

### Post by ArmenianLeader4 on 2009-08-10
Y thank you

---

### Post by zkriesse on 2009-08-10
To run a command usually at least in your case you probably would want to use the sudo command first...run your command but just with sudo in front of it. sudo means that you are root

---

### Post by alfu on 2009-10-06
-

---

### Post by Vaphell on 2009-10-06
there is nothing wrong with that - linux is serious about security and actually enforces user rights. You perform your daily tasks as an ordinary user, there is no reason why your system should allow you to do whatever you want without elevating your priviledges if you have not configured the system to allow it by default.
Sudoing is a safeguard - it requires some knowledge, effort and implies that you know what you are doing. Windows 'click ok to continue whatever the hell it means' in UAC does very little to increase security, people don't read warnings.

---

