---
title: "No init found Try passing init=bootarg could not boot from live CD"
date: 2011-03-17
forum: General Help
---

### Post by jekintrivedi on 2011-03-17
I have a Nvidia FX 5500 graphics card AGP port which is the source of problem.

Whenver i try to boot after connecting the GFX card the Ubuntu fails to load . Gives the corrupt kernel signal (all three ligts numlock cps lock scroll lock start blinking)

When i try to boot using the recovery mode ,I get this error message

Target filesystem doesn't have /sbin/init.
No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
--------------------------------------------------------------

I booted with 10.10 LiveCD even tried 9.04 CD but even it freezes like the normal ubuntu system. Even tried the graphics fail safe mode in live CD

I also tried fedora 15 , Kubuntu 10.10 all giving same problem 

Any idea as though what is the problem .. ? ?

Or ateast an alternative way to get my graphics card installed & run ? 

I cant do the X config changes to start my GFX card cause the text mode is not running . 

I cannot do the fsck , update grup other commands as the text mode is not running .

Is there any method to use BusyBox shell to solve my problem cause thats the only thing i can use .. other than GRUB shell

---

