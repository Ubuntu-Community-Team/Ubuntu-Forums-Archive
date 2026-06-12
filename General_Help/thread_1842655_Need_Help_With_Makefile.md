---
title: "Need Help With Makefile"
date: 2011-09-11
forum: General Help
---

### Post by JDacapo on 2011-09-11
I'm trying to install this driver for my Hanvon Artmaster tablet, and I'm having trouble even using the makefile. When I used the 'make' command in the folder, it would give me this error stating that the folders didn't exist. I decided to make those folders using the sudo mkdir command, but then when I tried to run the makefile again, I would get this error:


make -C /lib/modules/2.6.38-11-generic/build M=/home/gina/Downloads/hanvon modules
make[1]: Entering directory `/lib/modules/2.6.38-11-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.


Is there any easy way that I can compile a program and install it? I'm still new to Linux and even though I've had some experience with DOS and UNIX terminal commands, it's still giving me fits. I really would like it better if I could just 'sudo apt-get install' the hanvon driver like I've done with other programs. Is there a way I could do that instead of this messy make-file runaround?

EDIT: The program I am having problems with was downloaded from here: [http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/)

and the three files in the tgz file are:

hanvon.c
Makefile
README

Is there any way that I can make this program cooperate?

---

