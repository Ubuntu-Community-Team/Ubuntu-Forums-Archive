---
title: "WIll uninstalling software from lubuntu corrupt the os"
date: 2012-03-14
forum: General Help
---

### Post by lxde7 on 2012-03-14
I'm wondering if uninstalling software from linux or more specifically my linux os 
(lubuntu) corrupt the os like when in windows 7 if u uninstall programs you may corrupt the registry ???? Any answers or theories watever i just want to know :)

---

### Post by Mark Phelps on 2012-03-14
Linux doesn't have the Windows registry -- which is good or bad, depending on your point of view.

The problem that can be encountered uninstalling apps in Linux distros is the mistake of removing dependencies that other apps need.

For example, lets say an apps needs 10 packages, and 5 of them are already installed.  You don't know that, but when you go to install the basic .deb file you download, it tells you that five packages will be added and five will remain unchanged.

IF you install only using .deb files, then you won't run into any problems uninstalling because the dependencies are known.

But, if you also installed by building executables from source files, or if you mixed your installations between using dpkg, apt, and aptitude, you can run into problems where dependent packages get removed.

---

### Post by Helen McCall on 2012-03-18
If you use synaptic to do all your package maintenance, it will let you see what dependancies will be affected by removing any particular package.

I've been using Debian based systems for 16 years now, without any dependency problems. The Debian package management based on dpkg and Apt, is about the most bomb proof package management system I've ever found.

---

