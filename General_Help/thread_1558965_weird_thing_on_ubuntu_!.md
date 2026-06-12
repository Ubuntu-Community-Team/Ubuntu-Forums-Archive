---
title: "weird thing on ubuntu !"
date: 2010-08-22
forum: General Help
---

### Post by linuxuser2424 on 2010-08-22
hello everybody,i just install ubuntu 10.4 linux 32.bit on my Pc and it's was running fine beside the video card (intel x4500 ) :( not supported in ubuntu anyway after i update about 251 package in ubuntu ,i restarted the pc after in the grub ...they show me 4 Ubuntu !!!!!!! 2 for boot ubuntu and 2 for ubuntu recovery and 1 for windows 7 loader !! why this happen after i did update to ubuntu ? help me please and sorry for my bad english and i may comment late so dont worry

thank you ):P

---

### Post by uaebuntu on 2010-08-23
It is all OK and supposed to do that. When you update linux kernal the old one remains available so if you cannot boot from the new version you still have the old one available, plus a number of recovery and memory test options. When you are satisfied that the new version works OK you can go into System - Administration - Synaptic Package Manager, search for Linux Headers and mark the **lowest numbered one** for removal. Once these are all removed and you are left with just one Grub options do not display on boot.

Windows 7 loader is there in case you wish to create a dual boot machine.

---

### Post by sxmaxchine on 2010-08-23
Thats right

and just in case you need help removing a kernel i used [these instructions]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by rtimai on 2010-08-23
Actually, I had the reverse problem! I thought the boot menu which included previous kernels as well as recovery modes were potentially useful, but it disappeared after upgrading to Lucid. I recently found that for single o/s systems the boot menu is hidden by default, and you have to hold the Shift key down as soon as you see, "Grub loading..." 

You can view the entire Grub2 (actually v1.98!) manual in Terminal by entering 

> info grub

Arrow key to scroll, PageUp/Dn to move to different sections of the manual, Q to quit back to Terminal.

---

