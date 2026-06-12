---
title: "Help Installing"
date: 2006-05-29
forum: General Help
---

### Post by wb7ubb on 2006-05-29
I want to install a program in the terminal window and a part of the instuctions say:

make
make install

When I type in make then Enter, it says bash: make: command not found

I'm logged in as SU

Is there a replacement command for make? Or can I install these programs from the desktop. In Synaptic I cann't seam to be able to browse to where the folder that has the installation files.

---

### Post by aysiu on 2006-05-29
Try this ```
sudo aptitude update
sudo aptitude install build-essential
``` and try again.

---

### Post by wb7ubb on 2006-05-30
Thanks, got the make command. Now I can start installing some of the programs from my Red Hat over to Ubuntu.

---

### Post by wb7ubb on 2006-05-30
Ok, now I'm trying to get **Sendmail** installed. It seams to error with this message **(Can not locate an M4 program). **What would be my next step?

---

