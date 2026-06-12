---
title: "how to overwrite ubuntu"
date: 2010-04-27
forum: General Help
---

### Post by Markjo12 on 2010-04-27
hay guys
well i;m new to ubuntu and i have messed around with some system files and i need to reinstall the whoe OS and i was wondering how i could do this becuase i also have windows 7 installed.
remeber i;m very new to this so please show me in the most simple way possable

---

### Post by goldshirt9 on 2010-04-27
as you have windows 7 installed you could delete and format  the ubuntu partition in disc manager and then just reinstall ubuntu.

---

### Post by Rubi1200 on 2010-04-27
Hi,
please also provide some more information, the more the better because then people here can offer better suggestions/advice.
For example, are you dual-booting or did you set up Ubuntu from within Windows with Wubi?
This kind of information helps us help you.

---

### Post by Markjo12 on 2010-04-29
i'm sorry for the lack of information provided.
i'm  dulbooting, i installed it from the disck when i was running it, its shearing storage with windows 7 so i dont want to formatted my hardrive in case i overwrite windows.

---

### Post by gadolinio on 2010-04-30
> **Markjo12 said:**
> i'm sorry for the lack of information provided.
i'm  dulbooting, i installed it from the disck when i was running it, its shearing storage with windows 7 so i dont want to formatted my hardrive in case i overwrite windows.

I understand that you installed ubuntu in its own partition. Confirm this: You started the computer with the CD inserted, chose "try ubuntu without making changes to the system" and then installed it, or directly chose "install ubuntu". I mean, you didn't insert and use the CD while using windows, right?
Well, in that case you have ubuntu in its own partition. So you might well install it again just like you did before. There's a step in which you're asked where to install ubuntu; chose the same partition that has the messed up system. You should see a bar representing your hard drive, and coloured segments one of which says Windows 7, and another one that says "ubuntu 9.10" for example. Choose the part that says ubuntu. Ask here if you need more help. As long as you don't touch Windows in that bar during the installation steps, I don't see how you could destroy it.

(All this assuming you really need to reinstall, or really want to do it).

Good luck!

---

### Post by Markjo12 on 2010-04-30
> **gadolinio said:**
> I understand that you installed ubuntu in its own partition. Confirm this: You started the computer with the CD inserted, chose "try ubuntu without making changes to the system" and then installed it, or directly chose "install ubuntu". I mean, you didn't insert and use the CD while using windows, right?
Well, in that case you have ubuntu in its own partition. So you might well install it again just like you did before. There's a step in which you're asked where to install ubuntu; chose the same partition that has the messed up system. You should see a bar representing your hard drive, and coloured segments one of which says Windows 7, and another one that says "ubuntu 9.10" for example. Choose the part that says ubuntu. Ask here if you need more help. As long as you don't touch Windows in that bar during the installation steps, I don't see how you could destroy it.

(All this assuming you really need to reinstall, or really want to do it).

Good luck!
hello gadolinio
thanks for your reply your exactly  right, i have just downloaded ubuntu 10.4 and plan on overwriting the old ubuntu i hope this work. i will update you on whats going on after

---

### Post by Markjo12 on 2010-04-30
hay
i have just tryed to install ubuntu from iso image disc i burned and i cant seam to over write it

---

### Post by sdowney717 on 2010-04-30
the old ubuntu partition needs to be deleted for the ubuntu installer to install the new version. The ubuntu setup disc should give you the option to delete it. Dont delete the windows partition.

You can also boot windows and use disc manager to delete the old ubuntu partition. Then boot the ubuntu installer and install it into the free space.

---

### Post by gadolinio on 2010-04-30
> **sdowney717 said:**
> the old ubuntu partition needs to be deleted for the ubuntu installer to install the new version. The ubuntu setup disc should give you the option to delete it. Dont delete the windows partition.

You can also boot windows and use disc manager to delete the old ubuntu partition. Then boot the ubuntu installer and install it into the free space.

Right. I don't remember exactly how the installer gives you that option, but you can delete the partition where you have the current ubuntu, and that space becomes "unassigned" or something like that. Then, you can tell the installer to create a new partition in which it then installs ubuntu.

This website, though mainly in Spanish and for Ubuntu 9.10, has some screenshots you may find useful:
[http://www.glatelier.org/2009/10/instalando-paso-a-paso-ubuntu-karmic-koala-9-10/](http://www.glatelier.org/2009/10/instalando-paso-a-paso-ubuntu-karmic-koala-9-10/)
There's one under the title "Creating the partitions" that shows the step where you erase the ubuntu partition you now have and then create a new one. ("Borrar" means "erase", "Añadir" means "Add").

---

