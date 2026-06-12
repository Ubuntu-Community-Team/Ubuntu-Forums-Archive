---
title: "Noob question"
date: 2009-09-28
forum: General Help
---

### Post by Orbaneqtrx5 on 2009-09-28
First of all hello to all..... I'm a noob just switched to Ubuntu gnome 9.04 this week and I need to know if there is any command on the terminal to let you know what are the dependencies of a certain program... thanks in advance

---

### Post by ErikEhlert on 2009-09-28
The dependencies? Do you mean something similar to Task Manager?

Well, I believe if you do Alt+F2 then a bar appears where you can search for programs, next to it is a wrench and a monitor, the monitor opens up the System Activity.

Or maybe you meant something else and now I look stupid.

---

### Post by undecim on 2009-09-28
If you want to install a program from the repositories via a terminal, aptitude will check dependencies (and install them!) for you. For example, the game "tmw" requires the GUIChan library. I can install both of those (and all other tmw dependencies by typing this into a terminal:

sudo aptitude install tmw

If you just want the information (not the installation) you can use the "show" option for aptitude:

sudo aptitude show tmw

and find the line in the output that starts with "Depends: ". Each part of this line lists a package name followed by a specific version (for example "libguichan-0.8.1.1" is for "libguichan" version 0.8.1.1) or a package name followed by a condition: ( example: "libc6 (>=2.4)" means "libc6" must be version 2.4 or better)

---

### Post by undecim on 2009-09-28
also, if you don't like using the terminal, check out "Add/Remove" from the "Applications" menu for installing pieces of common software or "Synaptic Package Manager" from "System" -> "Administration" for installing specific packages.

---

### Post by Orbaneqtrx5 on 2009-09-28
thank you very much for your quick response and sorry for my ignorance but i was thinking that u have to download each dependency 1 by 1... thanks again

---

### Post by Orbaneqtrx5 on 2009-09-28
> **undecim said:**
> also, if you don't like using the terminal, check out "Add/Remove" from the "Applications" menu for installing pieces of common software or "Synaptic Package Manager" from "System" -> "Administration" for installing specific packages.

Yes i know how to do it in synaptic but was just wondering in the terminal

---

