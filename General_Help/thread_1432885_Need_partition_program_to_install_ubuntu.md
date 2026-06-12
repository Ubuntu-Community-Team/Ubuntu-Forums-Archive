---
title: "Need partition program to install ubuntu"
date: 2010-03-18
forum: General Help
---

### Post by mosquetero on 2010-03-18
Hi all!

Nowadays Ubuntu is the "king" of my hard drive but I also need Windows for several reasons so I need to install it. Do you know how could I partition my hard drive to make space for windows using an Ubuntu application?

Thanks in advance

---

### Post by Drenriza on 2010-03-18
ubuntu live cd.

Or download hirens bootcd 10.2.

both cd,es have programs to help you out with your problem.

---

### Post by whiskeylover on 2010-03-18
Boot from Ubuntu live CD, and do "sudo gparted"

---

### Post by slakkie on 2010-03-18
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by oldfred on 2010-03-18
Make sure you create a primary partition as windows really only boots from a primary. (A few of the real experts do have some work arounds, but for us regular users it is much easier just to create a primary)

---

### Post by ushills on 2010-03-18
Why not install it in a virtual machine using vmware or virtualbox, then no need to re-boot.

---

### Post by Mark Phelps on 2010-03-18
You didn't say which version of Windows.  

If it's Vista or Win7, do NOT use Gparted or the Ubuntu installer to resize the OS partition.  Doing so runs the risk of corrupting the OS and rendering it unbootable.

If it's XP, then GParted should do OK.

BTW, you can also download a free MS Windows app, EASUS Partition Master to do the Windows partitioning.

---

### Post by sandyd on 2010-03-18
> **ushills said:**
> Why not install it in a virtual machine using vmware or virtualbox, then no need to re-boot.
+1
virtualbox works awesomely

---

