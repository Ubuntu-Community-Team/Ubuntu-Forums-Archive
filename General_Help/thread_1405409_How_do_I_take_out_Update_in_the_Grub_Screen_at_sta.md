---
title: "How do I take out Update in the Grub Screen at startup"
date: 2010-02-12
forum: General Help
---

### Post by tgaston34 on 2010-02-12
Hi I am brand new to Ubuntu and Linux and I have been doing my regular updates the Ubuntu requires. But now I am getting a little bugged because when there is a new update instead of taking the old one out it leaves it there. So how do I remove these old one 
it says Ubuntu 2.6.31.-17 and I have another one ending in 14 can some one please help me.

---

### Post by Satoru-san on 2010-02-12
> **tgaston34 said:**
> Hi I am brand new to Ubuntu and Linux and I have been doing my regular updates the Ubuntu requires. But now I am getting a little bugged because when there is a new update instead of taking the old one out it leaves it there. So how do I remove these old one 
it says Ubuntu 2.6.31.-17 and I have another one ending in 14 can some one please help me.
Hello welcome to the forums :)

The reason it doesnt remove them is a very good one, if you remove a kernel from grub and something happens to your current kernel you dont have anything to fall back on to fix it. I have Several kernels in my grub, it is a good Idea actually.

If they REALLY bother you that much you can edit /etc/defaults/grub and remove the kernels that you dont need, but I would leave at least one old one like your .17 and just remove the .14. Then you run sudo update-grub

---

### Post by ajgreeny on 2010-02-12
You may soon have a 2.6.31-19 kernel as well, but as Satoru-san has said, it is definitely worth keeping an older one that you know works.

Yesterday at startup with my -19 kernel I experienced my first ever kernel panic and could not boot it at all, even after about three tries.  Luckily I still had a previous one which did boot OK, so using that older one I uninstalled the -19 kernel completely, ie purged it and all its configuration, then reinstalled it straight away.  Next boot it was back to normal with a standard boot into the -19 kernel.

Thank goodness for an old working version of the kernel!

---

### Post by bcbc on 2010-02-12
Try meierfra's guide:[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

You can create a custom menu - I have just windows and the latest ubuntu kernel - without losing the ability to fall back to the full grub menu if something breaks.

You can also remove old kernels through synaptic, but as already recommended, you should keep a couple to fall back on.

---

### Post by JohnL2009 on 2010-02-12
Try Uberclean - does a good job and leaves an old kernel to fall back on.

---

