---
title: "How do I upgrade to 10.04 from terminal_"
date: 2010-03-17
forum: General Help
---

### Post by colobix on 2010-03-17
Hey I was wondering if it is possible to upgrade from terminal.
I got pc issues after i upgraded to 9.04 so I can\t access gnome.
So maybe I could fix it by upgrading to the newest version.

---

### Post by Ozymandias_117 on 2010-03-18
I believe to do this, you would have to enable karmic-proposed updates in sources.list

---

### Post by 3rdalbum on 2010-03-18
Upgrading from one release to the next-but-one is a bit risky at the best of times, much less when the target distribution is still in development and you're having problems.

Download the current live daily build of Lucid (or wait about a day for Beta 1 to come out and be available on the torrents) and do a fresh install from there.

---

### Post by colobix on 2010-03-18
I cant burn it on cd. I only have one cd rom which is in use by the live cd
SO, ok can I repair the version I Have installed now then_
Or maybe reinstall all the files or something?

---

### Post by dcstar on 2010-03-18
> **colobix said:**
> Hey I was wondering if it is possible to upgrade from terminal.
I got pc issues after i upgraded to 9.04 so I can\t access gnome.
So maybe I could fix it by upgrading to the newest version.

There is no "upgrade" until a version is released, which will be the end of April for 10.04.

---

### Post by colobix on 2010-03-18
I dont really know what the bug is, but I cant boot into grub.
I have 2 kernels. The main kernel doesnt boot at all, it just freezes while the Boot hd0,0 message comes up.
Kernel 2 stops working after the white ubuntu logo comes up and then it says Boot Filesystem Failed or something like that.
So is there a command I can use to either downgrade or reinstall 9.10.

---

### Post by wjm on 2010-03-18
upgrading from a stable release to a beta/pre-beta release is never wise on a day-to-day workstation unless you're a hundred percent sure you understand the risk associated with that choice.  

That being said ... you can do it by modifying your karmic sources to lucid and then passing along the command "sudo apt-get dist-upgrade".  It should in theory perform an upgrade.

---

