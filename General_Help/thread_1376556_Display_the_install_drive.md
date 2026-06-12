---
title: "Display the install drive"
date: 2010-01-09
forum: General Help
---

### Post by Stupendous man on 2010-01-09
Hi Guys,
I finally got Ubuntu to install and run properly. I installed it as a "windows program" from within Vista.

After booting, I notice that the harddrive onto which I have it installed is not shown as a choice for me to view the contents of. 
I made it as part of a 750GB drive I have, but that drive does not show up in the list of available drives. 
There are other programs and files on there I would like to access. Is there a way to force it to be shown?

---

### Post by CallumFR on 2010-01-09
> **Stupendous man said:**
> Hi Guys,
I finally got Ubuntu to install and run properly. I installed it as a "windows program" from within Vista.

After booting, I notice that the harddrive onto which I have it installed is not shown as a choice for me to view the contents of. 
I made it as part of a 750GB drive I have, but that drive does not show up in the list of available drives. 
There are other programs and files on there I would like to access. Is there a way to force it to be shown?

When you use Wubi to install ubuntu it puts your installation drive at /host :)

---

### Post by Stupendous man on 2010-01-09
Ok, so then to see that drive, I would do what exactly?
Forgive my ignorance, but Ubuntu is alien to me...

---

### Post by SecretCode on 2010-01-09
Click the Places menu and see if there is a "Host" item anywhere in it.

---

### Post by CallumFR on 2010-01-09
If you go to Places > Computer > File System (might be called something different?) and then there should be a directory called "host" that you can just click into.  Alternatively, if you start up a terminal you can just do something like:

cd /
cd host

and that should get you there :)

---

### Post by Stupendous man on 2010-01-09
Ok, that did it. 
Thanks for the help folks.

---

