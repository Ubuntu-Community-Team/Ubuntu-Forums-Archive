---
title: "Wubi"
date: 2011-02-12
forum: General Help
---

### Post by Ubntu on 2011-02-12
I have 4 partitions and can not install Ubuntu. So my questions is, will wubi work? It installs in windows so I am thinking it will, but I am a noob when it comes to GNU/Linux.

Also sorry for so many questions. :???::???:

---

### Post by jmszr on 2011-02-12
Ubntu,

As long as you have the free space Wubi will work. You will need at least 10GB (actually, you can install it in less, but you would soon run out of room) for Wubi. Defrag Windows a couple of times before you install Wubi to help ensure contiguous free space.

Here is a link to the WubiGuide, it should be of help: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) .

Feel free to ask any questions you may have.

---

### Post by Ubntu on 2011-02-12
> **jmszr said:**
> Ubntu,

As long as you have the free space Wubi will work. You will need at least 10GB (actually, you can install it in less, but you would soon run out of room) for Wubi. Defrag Windows a couple of times before you install Wubi to help ensure contiguous free space.

Here is a link to the WubiGuide, it should be of help: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) .

Feel free to ask any questions you may have.

I have 175GB free space so it's fine. I'll sleep on it and try to set it up later. :D

---

### Post by Rubi1200 on 2011-02-13
In addition to what jmszr posted, if you do a fresh install of Wubi you need to lock the grub packages to prevent GRUB updates breaking the install.

See here for more:
[https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

---

### Post by Ubntu on 2011-02-13
Thanks for the help everybody. Installed Ubuntu with wubi and it's working fine. :o

---

### Post by Rubi1200 on 2011-02-13
Excellent! Make sure you lock the grub packages and everything should be okay.

Enjoy :)

---

