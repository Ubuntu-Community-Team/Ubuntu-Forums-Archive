---
title: "Laptop keyboard and touchpad suddenly stopped working on at login screen (xwindow)"
date: 2009-07-27
forum: General Help
---

### Post by frankquestion on 2009-07-27
Hello,
a few days ago, my laptop's keyboard and touchpad stopped working at the gdm login screen, which render my computer almost useless. If I boot in recovery mode and go straight to the console, then the keyboard works flawlessly but it'll stop working if I run "startx". They both work under Windows and I've booted with an older kernel but it was without success. Also, I cannot access the terminals with ctrl-alt-F*, the caplocks key has no effect at all.

I have ran the update manager around the time the problem appeared and I suspect an update to dbus-x11 is responsible for my problem as I've read threads of people having a similar problem in the past, sometimes caused by dbus-x11 not forwarding the inputs. None of the solutions offered in the threads fixed this problem.

I am not a linux guru so I really have no idea of what to do next. I think I could rollback the dbus-x11 package but I don't know how to do this from the command line.

Any answer will be very appreciated; I am currently travelling around the world and I badly need to use my ubuntu OS as this is my only computer at the moment. Thanks in advance!

EDIT: The following thread fixed my problem under the current and previous kernels: [http://ubuntuforums.org/showpost.php?p=7251902&postcount=8](http://ubuntuforums.org/showpost.php?p=7251902&postcount=8)

---

