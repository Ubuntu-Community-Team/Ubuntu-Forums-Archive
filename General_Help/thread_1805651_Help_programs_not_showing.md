---
title: "Help programs not showing"
date: 2011-07-16
forum: General Help
---

### Post by ub45 on 2011-07-16
I've recently installed dconf and 7zip but why are they not showing in the menu list.

---

### Post by dino99 on 2011-07-16
they both are internal features and work from the command line (on demand)

---

### Post by ub45 on 2011-07-16
WHY in other words...... why not show in the menu list like all other programs

---

### Post by conradin on 2011-07-16
They dont have icons. They run in the terminal, and in the system, (you can right click and get 7zip file options I think)
But you could make icons for them!
There are a variety of ways to do it:
right click on the gnome panel and select "add to panel.
 then select custom application launcher. Select terminal application from the drop down, and give the comands you wish to run.

an other method could be to write a bash script to do it for you.
you could write a bash script: This is for the command ddate
```
#!/bin/bash
ddate
read

```

then creat an link to the script. Im not sure if you can put scripts in the system path.

---

### Post by ub45 on 2011-07-16
How do I know which commands to give.

---

### Post by conradin on 2011-07-16
Well, it deppends what you want to do...
This isnt windows, and while these programs exist under the same name, performing the same funtions, it doesnt mean they run in the same way. 

you can read the man pages. I recommend getting familiar with the terminal. 
You can also try to describe what you want to do in the forums and we might be able to help you better.

---

### Post by ub45 on 2011-07-16
I want an icon to appear in the menu list concerning 7zip and dconf I don't understand the terminal or commands How do I learn.

---

### Post by oldos2er on 2011-07-16
> **ub45 said:**
> WHY in other words...... why not show in the menu list like all other programs

CLI apps will normally not have an menu entry, because if they did your menus would be a hideous mess.

There are a few ways to find executable files' names. Easiest is just to type **dconf** (for example) into a terminal, and see what happens. Or, find out where all files in the package are, and look for entries in /usr/bin (usually) or perhaps /bin, /usr/sbin, or/sbin: **dpkg -L dconf**

**apropos dconf** will show every possible command option for 'dconf', which you can narrow down using **man <command>** until you find what you're looking for.

---

### Post by oldos2er on 2011-07-16
> **ub45 said:**
> I want an icon to appear in the menu list concerning 7zip and dconf I don't understand the terminal or commands How do I learn.

Archive manager is the GUI front-end for all compression and archive formats.

---

### Post by ub45 on 2011-07-16
Thanks oldos2er

---

### Post by oldos2er on 2011-07-16
You're welcome.

---

