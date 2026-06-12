---
title: "virtual machine won't detect xbox 360"
date: 2009-08-22
forum: General Help
---

### Post by serpantman on 2009-08-22
When running xbox version of visual studios in a virtual machine, i enter the key from my xbox when at the connectivity screen. But the xbox is not detected. I know their are problems using XNA with ubuntu, IE you can't, but i figured i might be able to compile and then run it on the 360. But i couldn't even get the 360 to be detected. Are their any people here that have a way to develope games for the 360 using ubuntu?

---

### Post by zarthon on 2009-08-22
> **serpantman said:**
> When running xbox version of visual studios in a virtual machine, i enter the key from my xbox when at the connectivity screen. But the xbox is not detected. 

Are you running ubuntu on xbox?

When in a virtual machine the environment will only detect hardware that is "simulated" by the visualization platform.  These are very striped down and don't commonly include native sound or graphics necessary for developing a game. 

You will need a way to move the code from your machine to the regular game partition of your xbox then run it natively. 

You can also write AWESOME games for ubuntu using [pyglet]("http://www.pyglet.org/") or pygame ! 

Good luck.

---

### Post by serpantman on 2009-08-22
I always like other options! Maybe after i finish this one.

I thought that the virtual machine would be able to detect the xbox since its done over the network, and virtual machines use the internet fine. I'm pretty sure im installing windows on a second hd whenever my friend drops it off, but i thought i'd see if anyone here knew a solution.

---

