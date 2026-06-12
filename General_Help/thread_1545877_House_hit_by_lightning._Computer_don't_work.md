---
title: "House hit by lightning. Computer don't work"
date: 2010-08-04
forum: General Help
---

### Post by dw5437 on 2010-08-04
Everything almost works but not quite. The question is instead of shotgunning the problem should I start with replacing the hard drive or the motherboard or the processor. Is there a way to tell what is blown? The house took a direct hit and most electronics were fried. The main problem is that I set the computer to never go to sleep and it does every few minutes and I have to log back on quite often. Several games no longer play or just quit in the middle of the game and sends me back to the desktop. I haven't tried to do everything yet so I don't know of other problems. I don't have a lot of extra money so I only want to replace what I have to. The computer is a Dell Inspiron with 2.5 Gb processor and an Nvidia card ordered from Dell with Ubuntu 10.4 installed.

---

### Post by DeMus on 2010-08-04
> **dw5437 said:**
> Everything almost works but not quite. The question is instead of shotgunning the problem should I start with replacing the hard drive or the motherboard or the processor. Is there a way to tell what is blown? The house took a direct hit and most electronics were fried. The main problem is that I set the computer to never go to sleep and it does every few minutes and I have to log back on quite often. Several games no longer play or just quit in the middle of the game and sends me back to the desktop. I haven't tried to do everything yet so I don't know of other problems. I don't have a lot of extra money so I only want to replace what I have to. The computer is a Dell Inspiron with 2.5 Gb processor and an Nvidia card ordered from Dell with Ubuntu 10.4 installed.

When I started to read your message it sounded as if it didn't work at all. Later I read it is working but not as it was.
Maybe during a write operation on disk something went wrong and the only thing wrong now is the data on disk. It sounds strange maybe but try to re-install the complete OS. Do you have means of backing up your data? If so then do that first.
This way you don't have to invest money at all, just some time. Success.

---

### Post by hawthornso23 on 2010-08-04
Almost working but not quite sounds like a memory problem. Memory can be damaged by static quite easily and damaged memory would cause precisely this kind of erratic failure. If you had CPU damage I wouldn't expect it to run at all. Similarly for many other components.

Try running memtest and see what it turns up.

---

### Post by dw5437 on 2010-08-04
I already reinstalled. That was the 1st thing I tried. Sorry I should have put that in the original post. How do you do a memtest?

---

### Post by Keith_K on 2010-08-04
my experience with over loaded computers is that they never 'quite' work right, after piece by piece repairs. it seems that several items get damaged but your mileage may vary. good luck

---

### Post by celldweller1591 on 2010-08-04
may be ur GPU or ram is hit thats why your games crash and you come out of games at once. I advice you to get your computer checked by a hardware specialist or just give it a memtest. if your cpu or mobo would have been hit, you wouldnt be able to use your computer at all ! 
And yea, no offense but > 2.5 Gb processor i think its 2.5 GHz, Cpu clocks are in Ghz (Giga Hertz or Giga cycles per second) and its Ubuntu 10.04 not 10.4 !

---

### Post by DeMus on 2010-08-04
> **dw5437 said:**
> I already reinstalled. That was the 1st thing I tried. Sorry I should have put that in the original post. How do you do a memtest?

Boot with your CD and choose memtest. Just let it run a for a long period of time.

---

### Post by oldfred on 2010-08-04
Do you have homeowners insurance? It often covers this type of damage, but you have to document it well. Talk to your insurance agent.

---

### Post by dw5437 on 2010-08-04
No no insurance. I tried the memtest but when I put Ubuntu disk in it has no options, it just boots straight into the live cd. It only stops to ask for my language. I don't remember how long I have had this computer but I think I will call Dell and see if I am still under warranty. Should have done that 1st I guess. The memory problem sounds like my best bet. I didn't even think of that. Many thanks for the info and the criticism.

---

### Post by hawthornso23 on 2010-08-06
Reboot the computer. Before the splash screen shows up hit escape. You only get 2 seconds to do it so be alert with your finger ready on ther ecape key when you reboot. This will put you into the grub menu and offer you a bunch of boot options you won't have seen before, For example you can boot into an old kernel or boot up in safe mode. One of the options is to run memtest. Recommend you leave it running overnight.

---

