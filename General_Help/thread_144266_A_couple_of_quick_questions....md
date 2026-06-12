---
title: "A couple of quick questions..."
date: 2006-03-13
forum: General Help
---

### Post by xc_xtc on 2006-03-13
I loaded my laptop with a dual boot system. Xp/Ubuntu

   After playing around a bit i found nUbuntu to be better for what i needed to do. Now, I still have Ubuntu and got a Linux for dummies book and would like to learn...

  My first question is how do you know what and where to get packages? When i type a command and Unbuntu doesnt recognise it; how i do I figure out where to get the package? (or what the name might be...?)

  Second: Im using a live version of nUbuntu but it doesnt support my card directly. I need to mount the card and install the drivers... or something... lol... ::Can I write a batch file to burn to the nUbuntu CD and not have to repeat the process over and over?::

  Third: Can writing to a partition used for storage (for all systems) can I do irreversable damage from a confused drive? 

   Thanks alot. Hope to break away from winduhs.

---

### Post by jpkotta on 2006-03-14
One:
Synaptic is my favorite package manager.  You can search, read descriptions, etc. with it.  Launch it with ```
sudo synaptic
``` or Menu -> System -> Administration -> Synaptic.

Two:
I doubt you can add a script or any type of file to any Live CD.  If you install to your hard drive, then you can easily write a script to load a driver and set up a card, provided that you know what commands are needed.

Three:
Your question is rather vague.  If the drive is "confused" now, then I wouldn't  trust it for anything.  An unreliable drive is useless.  If you are wondering about making a partition, and whether this can damage the drive, then, yes there is a *very* small chance of wiping the drive, much smaller than the chance of user error, but I'd say nothing to worry about.

---

### Post by xc_xtc on 2006-03-14
by confused... well no its not but im was wondering how it will react to bewritten by linux and xp (for storage) fat32

  so far, everything has installed alright... except the command package to build in linux. (make and etc..)

  ....and i dont see why i couldnt add a script to a cd...

  if not the cd, maybe the HD..? It is loaded with XP AND ubuntu...

---

### Post by stuporglue on 2006-03-14
Hey there, xc_xtc....I'm a bit confused by some of your post, but I'll see what I can understand.

Some definitions:
package -- a package is sort of like an installer. You install a package and it puts the program, the graphics, the documentation and whatever else the program needs where it needs to go.
program -- When you type a  command, you are running a program. The program may have been installed from a package, but you don't run a package. 

Searching for packages is done in (menu) System-->Administration-->Synaptic Package Manager

> but it doesnt support my card directly
What card are you talking about? Video, audio, network...

> Can writing to a partition used for storage (for all systems) can I do irreversable damage from a confused drive? 
 
Yes. Maybe? What do you mean by confused? Write support isn't solid for NTFS yet, so you could have some issues there. I guess if your computer is really confused it could do anything though.

---

### Post by xc_xtc on 2006-03-14
umm yeah i understand most prompt stuff..... maybe not the linux syntax yet but... i go back to basica

   Now.. 

  The cards being anything, pcmci, flash, v.9, combo, etc.... that i plug into my laptop.

   Now the point of my dabbling in unbuntu is to learn linux whle not totally helpless. nUbuntu is much less GUI and I cant navigate yet... although I just found out last night that drive/devices are files/folders,etc... last night.

  as i said... the storage area is fat32.. not ntfs.

---

