---
title: "Make a smaller kernel"
date: 2009-07-08
forum: General Help
---

### Post by Genun on 2009-07-08
Hi, I've been looking at the forums and using them when i can but this is my first post. I've been using Ubuntu for over a year, but only now am I starting to learn more than the basics. Glad to be here already.

I just built my first kernel and now I need to make it as small as possible. How would I figure out what I need and don't need? I know I should go through the config file, but what needs to stay and what needs to go?

---

### Post by Mighty_Joe on 2009-07-09
> **Genun said:**
> I just built my first kernel and now I need to make it as small as possible.

Is there any particular reason to?  If you compile everything as modules, they can be loaded and unloaded at will and the kernel will only be as big as it has to be. 
Messing with the kernel is unnecessary unless one is either planning on doing kernel development or creating a custom distribution for a particular set of hardware.  If you run into problems, it's hell to figure out if the problem is an application bug, bad hardware or some kernel module that you forgot, a kernel dependency you didn't know about or a module that has to be compiled in the kernel or not compiled in the kernel or loaded before some other module. And $DIETY help you if you post to the forums for help and don't mention that you have a custom kernel!
My advice: if you are just starting out, save yourself a world of hurt. Don't mess with the install on your computer.  Install [virtualbox]("http://www.virtualbox.org/"), install Linux there and mess with that install.  Then if you screw things up, you can just roll back your changes or reinstall without wiping your "real" computer.  
[Gentoo]("http://www.gentoo.org/") is a good distribution for tweakers, and the community is geared to facilitate them.

---

### Post by Genun on 2009-07-09
Thanks for the reply and I would definitely not mess with my own computers that I need to work. However I am doing this to learn. I may not be a kernel developer but I want to know more about it. I want to learn.

---

### Post by Yellow Pasque on 2009-07-09
What you need and don't need is highly dependent on your hardware and any hardware you intend to use with that kernel in the future, so make sure you know your hardware real well (use lspci) and read the help items carefully.

I prefer this guide: [https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

It's been a while since I've rolled my own kernel. It gives a little speed boost, but configuring it for compilation gets very tedious after you do it once or twice. Good luck and have fun.

---

