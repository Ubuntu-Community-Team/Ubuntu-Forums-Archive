---
title: "Kernel source path?"
date: 2004-10-24
forum: General Help
---

### Post by Dracontopes on 2004-10-24
What is the kernel source path in Ubuntu 4.10?

I have installed the kernelsources using: sudo apt-get install linux-source

Now I can't find it in /usr/src (there is only a .tar.bz2 package)

---

### Post by btb on 2004-10-24
cd /usr/src
sudo tar -xjvf kernel.tar.bz2

Optional is making a simlink.

sudo ln -sf /usr/src/linux-source-xxxx /usr/src/linux

Atleast, I think this is the appropiate way. Just installed ubuntu yesterday.

---

### Post by Dracontopes on 2004-10-24
[QUOTE=btb]cd /usr/src
sudo tar -xjvf kernel.tar.bz2

Optional is making a simlink.

sudo ln -sf /usr/src/linux-source-xxxx /usr/src/linux

Atleast, I think this is the appropiate way. Just installed ubuntu yesterday.[/QUOTE]
 Thank you :)

---

