---
title: "Multiple versions listed in GRUB 2"
date: 2010-02-24
forum: General Help
---

### Post by cmcesq on 2010-02-24
I have a dual boot desktop with WinXP on C: and Ubuntu on D:.  GRUB 2 handles the start-up.  

Having installed multiple updates to Ubuntu, my GRUB menu now lists:
2.5.31-19-generic
2.5.31-17-generic
2.5.31-16-generic
2.5.31-15-generic
2.5.31-14-generic
 and (recovery mode) for each of the above, along with the mem test and WinXP.

Is there any reason I need to list all these variants of Ubuntu? If not, can I simply edit them from the GRUB config file or must I do something else to actually uninstall them?

Many thanks in advance.

---

### Post by drs305 on 2010-02-24
The easiest thing to do is remove older kernels with either Synaptic or Ubuntu-Tweak. Ubuntu-tweak is a great app that makes it easy to remove older kernels. When you uninstall a kernel it is removed from the Grub menu as well.

Generally users keep at least one older kernel which is known to work.

About 2/3 of the way through this post is a section explaining methods to eliminate older kernels from the menu.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by warp99 on 2010-02-24
Nope you don't need all of the kernel versions. Just go into Synaptic and locate the previous versions and remove them. If you're worried about not being able to boot your system you can keep the current kernel version (2.5.31-19-generic) and the previous one.

---

