---
title: "Boot Windows with wubi"
date: 2012-07-08
forum: General Help
---

### Post by SilverDragon24 on 2012-07-08
I've been using Ubuntu with wubi for a while now and I notice the The root filesystem is a file name root.disk,
any way I can create a similar disk file which'll let me boot windows from the disk file itself?

---

### Post by Frogs Hair on 2012-07-08
The Ubuntu root disk is a folder inside the Windows partition. It is possible to run Windows and other operating systems from Ubuntu with software. [https://www.virtualbox.org/](https://www.virtualbox.org/)

I haven't read about anyone using a virtual installation from a Wubi installation though. Wubi also uses the Windows boot loader and when you select Ubuntu or Windows you are using the Windows boot loader.

---

### Post by SilverDragon24 on 2012-07-10
How can I make a root.disk file from my windows Installation maybe you didn't read the question right. Its just an experiment that I thought which'll let keep 2 versions of windows on one partition.

---

