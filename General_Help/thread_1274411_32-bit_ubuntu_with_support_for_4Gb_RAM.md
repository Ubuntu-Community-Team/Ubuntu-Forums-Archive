---
title: "32-bit ubuntu with support for 4Gb RAM"
date: 2009-09-24
forum: General Help
---

### Post by crazyfuturamanoob on 2009-09-24
I'm currently using 64-bit Ubuntu. I want to switch back to 32-bit because some important applications don't work. (E) Is recompiling kernel with PAE-support worth the extra RAM due to performance overhead?

---

### Post by XCan on 2009-09-24
Do you have exactly 4GB RAM installed? If that's the case, I doubt it will be worth it with PAE. But of course if you want to push everything, you should do it. But I wouldn't have done it. Tbh, the gain is even minimal for going 64 bit if one has 4 GB worth of RAM.

Out of curiousity, which app is it that doesn't work on your 64 bit system?

---

### Post by bodhi.zazen on 2009-09-24
9.10 has a pae kernel.

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae)

---

### Post by crazyfuturamanoob on 2009-09-25
Here are some problems, which don't exists in 32-bit:

[list]
[*]Blender crashes with yafray plugin
[*]NetBeans J2ME emulator does not work
[*]Can't install GtkRadiant deb
[*]Flash+FF got really bad performance
[/list]
I got 4Gb of RAM. Even in 64-bit, free -m shows total of 3959 megabytes of memory. (ugly acer logos in BIOS, grr...:evil:)

---

### Post by Vaphell on 2009-09-25
you know you can use 32bit apps on 64bit system? i don't know if there are no issues with these particular apps but it's definitely doable.

---

