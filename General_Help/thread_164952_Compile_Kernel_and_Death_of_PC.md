---
title: "Compile Kernel and Death of PC"
date: 2006-04-23
forum: General Help
---

### Post by smadahar on 2006-04-23
As a  fairly new Ubuntu user I have a problem which I cannot yet find the cause of. If I compile a new kernel (2.6.12 for example) I can get all the way through until I have to make a .deb file at the end. When this happens, a few minutes in and my computer switches off. The only other times this happens in when the CPU overheats and the motherboard's safety swith off kicks in. 

Today I decided to do an upgrade to Dapper flight 6 via the sudo apt-get method. Guess what? During the installation the computer switched off. Now, I have a broken linux installation with more problems than I can solve. Of course I can get the thing re-installed, but does anyone know of this problem or even better how to try to solve it? 

I have home made PC with an AMD 2GHz Processor, 384MB RAM, 200GB hard drive and fairly standard everything else.

---

### Post by oofnik on 2006-04-23
I had a similar problem involving faulty memory. Everything I would try to compile with gcc would lock up my system and force me to restart it. I memtested each DIMM individually (4x 256MB each) and found the faulty one, replaced it, and I've been fine ever since. You should try to do the same, maybe you'll discover some faulty memory too.

---

### Post by paritybit on 2006-04-23
You may need to upgrade your cooling if putting load on it stops your computer....
apt-get should fix all things alright but I really think this is a hardware problem with relation to a lack of proper cooling from what you have described.

---

### Post by smadahar on 2006-04-24
Thanks for the tips, I'll definately do the memtest, although in normal operations the computer can handle quite intensive jobs (3D rendering and games). I'll test the memory and see what happens.

---

