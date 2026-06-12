---
title: "problem with wine"
date: 2011-06-21
forum: General Help
---

### Post by shovon1424 on 2011-06-21
hi everyone,i,m absolutely new at ubuntu.i use ubuntu 10.10 maveric.i installed wine to run some .exe files.i ran wineconfig and set everything to default.still when i clicked the .exe file to open it with wine program loader,the mouse pointer rotates and waits for a while,then nothing happens.i tried changing the permission of the .exe file to executable,that too didn,t help.please help.i want to use ubuntu.greetings.

---

### Post by kilowattradio on 2011-06-22
> **shovon1424 said:**
> hi everyone,i,m absolutely new at ubuntu.i use ubuntu 10.10 maveric.i installed wine to run some .exe files.i ran wineconfig and set everything to default.still when i clicked the .exe file to open it with wine program loader,the mouse pointer rotates and waits for a while,then nothing happens.i tried changing the permission of the .exe file to executable,that too didn,t help.please help.i want to use ubuntu.greetings.

Open up a terminal window (Gnome Terminal) and type the command

```

wine /path/to/file.exe

```
Wine may output any faults that it finds in the terminal window. 
Wine does have a compatibility list of windows software that you can check:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by shovon1424 on 2011-06-22
:pthanx

---

### Post by gizmo720 on 2011-06-22
Right click on it and select "open with wine"

---

