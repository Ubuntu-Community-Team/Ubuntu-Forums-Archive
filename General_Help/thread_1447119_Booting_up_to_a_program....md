---
title: "Booting up to a program..."
date: 2010-04-04
forum: General Help
---

### Post by pepsifx357 on 2010-04-04
Is there a way to strip the window manager from ubuntu along with all of the bloat, to create an evironment, of let's say, firefox.  In other words, you turn on your computer and the only thing that pops up is firefox.  But let's take it a little further to what I would really like.  A Digital Audio Workstation that is so dedicated that the only thing it does is boot up to Ardour and record.

Is any of this possible?

Obviously you would have to start out with something like the basic Debian System and go from there right?

---

### Post by john newbuntu on 2010-04-05
Firefox and DAWs are GUIs.  GUIs can not exist without a window manager, which in-turn relies on X.  Someone please correct me if this statement is wrong.

So, you can strip the WM from a distro but you will have only text-based capabilities and will not be able to run graphical programs.  You can however choose a lightweight alternative though such as openbox or fluxbox.

---

### Post by JiuJitsu500 on 2010-04-05
too true.... a Graphic User Interface requires a windows manager, and fluxbox is a great super-light alternative to GNOME or KDE, openbox too. Xfce is also very lightweight and really doesn't have clutter at all as well.

You could try doing a fresh install of Xubuntu, removing all the programs/packages you do not need, install only the ones you do, and put them in the startup apps.... then just add to it "only in this workspace" so it will be all neat and stuff....

Or look into building your own distro in a virtualbox that does exactly what you want and only that, then create a liveCD and try it :)

But that would be only a pain for a little while. Use BUM to further it too, but do what you like.... X is definately necessary though, you cannot escape it!!!! Unless you go to text only like he said....

---

### Post by pepsifx357 on 2010-04-05
I started experimenting with other window managers like fluxbox.  I didn't like it, nor did I like enlightenment.  Haven't tried XFCE, but I guess it really boils down to, "Is it fast."  So I can't complain as they were very fast.  

If I use A copy of Debian that is the base system and add what I need, how can I repackage it into a live cd?

---

### Post by john newbuntu on 2010-04-06
Remastersys is something I hear a lot to create your own liveCD.  I have'nt used one myself.  But worth a try I guess.

---

