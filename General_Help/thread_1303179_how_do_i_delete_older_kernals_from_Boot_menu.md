---
title: "how do i delete older kernals from Boot menu?"
date: 2009-10-27
forum: General Help
---

### Post by eival on 2009-10-27
i recently did a dual boot installing windows first then ubuntu, but now the list is starting to get longer, right now i have 3 different kernals but each kernal also has 2 different versions, so theres like 6 listed, then windows at the bottom.

how can i delete those older kernals, and for future updates, how can i make the new kernal overwrite the current one automatically?

---

### Post by XDevHald on 2009-10-27
You can delete these in Synaptic by typing **linux** without quotes and locating the older kernels and doing a **Mark for Complete Removal**. This will update the menu.list and will be noticable by next boot.

---

### Post by alphaniner on 2009-10-27
That is based on your /boot/grub/menu.list file.  You can edit the file to remove or comment out the entries for the old kernels (that's what I do), but be sure you know what you are doing.

There may be friendlier/safer ways to go about it though.

---

### Post by oldfred on 2009-10-27
The old kernels do not take up a lot of space but there are instructions for housecleaning. It is easy to limit the number of kernel shown on the grub menu. Two is recommened so when a new kernel is updated you have a fall back just in case the new one does not work.

It is a setting in menu.lst but the easiest way is to down load SUM or StartUp Manager from the repos using synaptic.

HOWTO: Grub Menu Kernel Display Options && StartUp-Manager info
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by eival on 2009-10-28
thanks for all the replies.:popcorn:

---

