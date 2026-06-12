---
title: "fresh installed 5.10, did updates, (kernel updated) now 2 kernels show in grub!"
date: 2006-04-20
forum: General Help
---

### Post by syxbit on 2006-04-20
any ideas?
how do i get rid of the old one?

---

### Post by Mishal on 2006-04-20
You have installed the newer version of your kernel as a result of the updates.

Go to Synaptic and search for the older version (look out for the version number of both in grub) and 'Mark for Complete Removal'.

Hope that helps :)

---

### Post by syxbit on 2006-04-20
thanks, but could you be a little more specific
i'm in the synaptic pack manager, bu not sure what do delete
i did a search for "kernel" and "linux kernel"
there's tons of stuff

---

### Post by Mishal on 2006-04-21
In Synaptic, press Ctrl+F to bring up the 'find' dialog box and type in 'linux-image'

A list of available kernels that are available in the repositories are displayed only two of which **with version numbers** will have a green mark beside them, indicating that these are the kernels installed on your PC. Right click on the older version and 'mark for complete removal'.

To be certain, there may be two other items with the green mark beside them but they will have no version numbers in their names. Just ignore them.

If you still have problems, I will post a screenshot but at the moment I am feeling lazy :)

---

### Post by elamericano on 2006-04-21
or you could just remove the items from grub by editing /boot/grub/menu.lst. Scroll down and delete whatever entries you want. (be sure to backup, in case you change your mind.) Then run grub afterwards.

Who knows? While you're there you may decide you want a new timeout. Just be careful with the boot loader 'cause you can lock yourself out if you decide to experiment.

---

### Post by Mishal on 2006-04-21
Yes, that works too but he will have an unused kernel sitting in his hard disk for nothing, eating up disk space. Each kernel takes up about 52 MB.

---

