---
title: "Ubuntu in VirtualBox"
date: 2009-08-22
forum: General Help
---

### Post by BrandonArchangel on 2009-08-22
How much RAM should I give VirtualBox to run Ubuntu on a old Dell machine running XP with only 512mb of RAM. It seems like 512mb of RAM is recommended but I do not know if it is safe to use all of my RAM, won't it be extremely slow if I do that? Lol will it also be slow if I only use 256mb anyway? Any good recommendation.

---

### Post by BrandonArchangel on 2009-08-22
Bump

---

### Post by nhanquy on 2009-08-22
RAMs are cheap. Buy more RAM.

---

### Post by howefield on 2009-08-22
> **BrandonArchangel said:**
> How much RAM should I give VirtualBox to run Ubuntu on a old Dell machine running XP with only 512mb of RAM. It seems like 512mb of RAM is recommended but I do not know if it is safe to use all of my RAM, won't it be extremely slow if I do that? Lol will it also be slow if I only use 256mb anyway? Any good recommendation.

You can't use all your memory for your guest. How will the host system run if there is no memory left for it. Both the host and guest share what you have in the machine.

XP will run with 256, but possibly not well enough never mind the fact that the host will only have 256.

Try it and see, it may do what you want, but don't be surprised if not.

---

### Post by anomis66 on 2009-08-22
I have VB installed on my works laptop.  When running Ubuntu in VB, I alloacted 394MB RAM to the client, but the host has 2GB installed.  

I agree with nhanquy, check the Dell specification for your model and fit as much RAM as is supported or you can afford.

---

### Post by BrandonArchangel on 2009-08-22
I don't feel like upgrading a old Computer when I have nice new ones. And to the second comment thanks. The third thank you also would either of you reccomend Wubi on Vista or XP instead? As I have a laptop with 4gb of RAM but I am just scared I will screw it up when installing Wubi and am also unsure of whether or not it is truly safe to use with vista.

---

### Post by majed on 2009-08-22
If u have nice new ones, replace xp with ubuntu on the old one.. why use virtualbox on a limited machine..

---

### Post by howefield on 2009-08-23
> **BrandonArchangel said:**
> I don't feel like upgrading a old Computer when I have nice new ones. And to the second comment thanks. The third thank you also would either of you reccomend Wubi on Vista or XP instead? As I have a laptop with 4gb of RAM but I am just scared I will screw it up when installing Wubi and am also unsure of whether or not it is truly safe to use with vista.

Seeing as it is your old computer, it sounds ideal for experimenting with. You could take an image of the disk as it currently stands, then you can do what you like with it knowing you can reimage back to the point of when you took the image.

Just another option.

---

