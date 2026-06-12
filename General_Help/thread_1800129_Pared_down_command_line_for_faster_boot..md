---
title: "Pared down command line for faster boot."
date: 2011-07-08
forum: General Help
---

### Post by Bre Ntt on 2011-07-08
Would be possible to have a dual boot with Ubuntu only loading the things necessary for command line use of emacs? 

I thought it might be good to be able to take notes for class on a quickly booting command line. (It has the added benefit of being less distracting)

Does it work like that? Could a pared down command-line only install be sufficiently faster on boot-up? Might another flavour of Linux be more suited to the task?

---

### Post by gizmo720 on 2011-07-08
I would recommend installing Ubuntu-server, which is pretty minimal. You might also want to install xinit to allow you to easily open a graphical program from the terminal (You don't even need a window manager)

If you really want stripped down, look into [arch linux.]("http://www.archlinux.org/")

---

### Post by lykwydchykyn on 2011-07-08
Loading only a command line can certainly be faster.  What are you dual-booting with?  If you already have Ubuntu installed, you can probably just set this up with runlevels and add it as a boot option without creating a separate install.

---

### Post by 1clue on 2011-07-08
Why not just go to a no-x runlevel?

Ubuntu does it differently than the way I learned it, it used to be init 3 gave you no X but full featured otherwise, and init 5 was X.  Have to look at the documentation to figure it out.

You should also be able to specify the runlevel during boot by passing a kernel parameter in.

---

### Post by Bre Ntt on 2011-07-09
I'll be dual booting with Ubuntu. 

I've changed the runlevel to boot into the command prompt before. But it still seems to take longer than it should. It seems like it must be doing a lot more than would be necessary to load basic command line functionality. 

My thinking is that I remember DOS taking a couple of minutes to fire up on a 286 machine, so it seems like a command prompt with enough resources to run emacs and wouldn't be asking to much more than DOS would have on a 286. So one might think that loading linux with just enough basic functionality to edit text files on a modern computer should be able to fire up pretty fast? But strangely, changing the run level, there is still quite a wait between pressing power, getting through the BIOS stuff (which there's no way to get around presumably), and through the Ubuntu splash screen (the part that might be improved?), and finally to the command prompt.  

I've been doing some snooping, and there is a couple of distributions that are made to be small and fast booting (Damn Small lLinux and Puppy Linux) . Yea, I came across ArchLinux too. Thinking about trying that out. 

Thank you for the responses.

---

