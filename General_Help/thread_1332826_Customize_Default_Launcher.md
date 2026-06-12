---
title: "Customize Default Launcher"
date: 2009-11-20
forum: General Help
---

### Post by airmorris on 2009-11-20
**Customize Default Launcher** 			
 			 			 		   		 		 		OK, I have 25 Acer AspireOne Netbooks running 9.04 remix that I want to roll out to my elementary school. They authenticate with our AD which is real slick. However, I need to be able to set the launcher items to a default set of applications for all users. I can easily customize it on a per user basis but this isn't practical for 90 users on 25 different machines. There must be something I can do, right?

---

### Post by bodhi.zazen on 2009-11-20
Try putting your customizations in /etc/skel

then add a new user, should pull in the defaults form /etc/skel

The files and directories in /etc/skel are exactly as they would be in the home directory, including the . files

look in .config and .local for example.

---

### Post by airmorris on 2009-11-20
I can't find any files in  /etc/skel that look like the menu settings. Is there anywhere else it would be? Thanks for the reply.

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
You can create the files there to make your settings system wide defaults but you'll have to do it on every machine. I would say, then, you could make your configurations of your /home/user/.config and .local folders (in home to make it easier permissions wise) and then copy them to the /etc/skel folder on each machine.

---

### Post by bodhi.zazen on 2009-11-20
> **airmorris said:**
> I can't find any files in  /etc/skel that look like the menu settings. Is there anywhere else it would be? Thanks for the reply.

First you need to identify files to configure your system.

You then put those files in /etc/skel

Without knowing what it is you want to configure it is impossibl eto be more specific. Configuration files can be found in your home directory , they are hidden, or . (dot) files.

Examples .local , .config , .gnome , .gnome2

---

