---
title: "Copying from computer to external hd"
date: 2010-08-13
forum: General Help
---

### Post by seandude on 2010-08-13
Due to a long and convoluted adventure with a kernel and trying to fix grub, my computer isn't booting, so I've decided to just do a clean install of Ubuntu 10.04.  I'm currently running from a live CD, and need to make a copy of my /home directory onto an external hard drive.  The only problem is that the computer isn't letting me copy my home directory into the hard drive.  I've tried using the terminal and using sudo, and gksu nautilus, but it won't work.  

How do I copy from my computer's hard drive onto an external hard drive while running from a live cd?

---

### Post by a2020vision on 2010-08-13
You first need to have both hard drives mounted. You should be able to do this simply from going to "places" in the menubar and clicking on each hdd's name (something like "250GB Filesystem", maybe); there are also command-line ways to do this.

Could you try opening a terminal (alt-f2, enter "gnome-terminal") and copying the output of the command "less /etc/mtab" for us? (this is so that we can see what drives are already mounted)

---

