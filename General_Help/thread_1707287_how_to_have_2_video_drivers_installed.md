---
title: "how to have 2 video drivers installed?"
date: 2011-03-15
forum: General Help
---

### Post by X1R1 on 2011-03-15
Hi guys, simple question, answer might be hard to do.

I have a laptop with 2 graphic cards on it, currently I have the nvidia drivers installed, and I want to install the Intel ones, but when I try to install I am prompted to remove the nvidia ones.

I have a module to turn off the nvidia card, but I still need to get the drivers for the intel card install, how to do it? Thanks for the help!

---

### Post by Grenage on 2011-03-15
Hi there,

As far as I am aware, intel drivers come with Ubuntu; you shouldn't need to install them.  What are you trying to achieve?

---

### Post by zaphod777 on 2011-03-15
last I checked the dual video card layouts like nvidia's optimus setup don't work in Linux yet. nVidia said they have no plans to release an optimus friendly Linux driver for the time being.

You are better off tring to disable one of them in the BIOS to save power. I ended up just getting an Asus with a built in Intell HD card since I don't play games and it plays video like a dream and doesn't get hot or drain the battery. 

If you are trying to do dual video cards so you can have dual monitors that might be a different story but I don't know how to do this.

---

### Post by ruien on 2011-03-15
> **Grenage said:**
> Hi there,

As far as I am aware, intel drivers come with Ubuntu; you shouldn't need to install them.  What are you trying to achieve?

There are several laptops with 2 graphics card. I have a new Asus laptop with a nvidia 1gb card and a Intel card. The intel runs the desktop and when i play games the nvidia card autoloads so i can play opengl games. Works fine in win 7  but not in linux. Thats why i dont install linux on that laptop. Its called Optimus technology and there are no plans to make drivers for theese laptops having this graphic solution.    [http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

Some claim that som opensource drivers work. Some dont.

---

### Post by Grenage on 2011-03-15
Ah, Optimus.  That does make things interesting, but at least the OP has the option of turning one of them off in the BIOS; not everyone does.

---

### Post by X1R1 on 2011-03-15
Just to clarify. I don't have nvidia optimus card, just switchable graphics, what I want to achieve is to be able to switch to the intel card when I like without the need to install / uninstall.

Even if ubuntu comes with the Intel drivers I am pretty sure they got replaced when I installed the nvidia ones.

And another clarification, my "module to turn off the nvidia card" I mean its a kernel module. But I do have an option to turn off the Intel card In the BIOS

---

