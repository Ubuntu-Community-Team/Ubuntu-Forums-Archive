---
title: "Lucid Lynx Runs Really Slowly"
date: 2010-07-14
forum: General Help
---

### Post by somidscr21 on 2010-07-14
I have just installed Lucid on my tower (Dual 2.6GHz cpu, 4GB ram), and it is running very slowly. I feel like I am running it off of the live cd. I notice the slow down all the time, it's like there is a delay after clicking the mouse. I realize my computer is not screaming top of the line, but it should not be like this. Especially since Linux Mint 9 (based off of Lucid) runs so much more smoothly. I know this is vague, but I don't even know where to start.

---

### Post by mörgæs on 2010-07-14
A machine like this should run Ubuntu like a greased lightning.

First, you can run the command **top** to see if there is any application which is overloading the CPU. Press q for quitting top.


More likely, though, is a problem with the graphical drivers. Please post the output of 

```
hwinfo --gfx
```

---

### Post by somidscr21 on 2010-07-20
Sorry it took me so long to respond, I have been out of commission for a while. Before I could do much, the computer was formatted and is now running linux mint 9 (which is based directly off of Lucid). I am experiencing the same problems that I was on Lucid. After running top, I could see it was usually nautilus or gnome-settings running at 75 or higher cpu causing problems. Also, the graphics card I have is an nVidia GeForce 9500 GT. I still have no ideas how this is happening. If you do want to continue helping, just to let you know you can take the gloves off, I've been running variants of Ubuntu for four years now, so feel free to really let er rip.  Thanks!

---

