---
title: "Kubuntu faster than Ubuntu - Why?"
date: 2010-03-02
forum: General Help
---

### Post by cottfcfan on 2010-03-02
I`ve always preferred a Gnome to a KDE desktop, but for the last few months KDE has won me over. Reason - its faster.
 No matter what task I do Kubuntu is always a lot snappier than its Gnome equivalent. Particularly when using open Office is this the case.
 But why? They`re both on the same computer,(I dual boot) and I use the same settings.
 What could cause the difference in speed, when they`re based on the same architecture?

---

### Post by dabl on 2010-03-02
Assuming the same kernel and settings for things like swappiness and filesystem/mount options, I would suspect that the "snappiness" is 100% in the video display domain, meaning it is related to the K Display Manager (KDM) versus the Gnome Display Manager (GDM) and other aspects of the desktop environments.

If you could devise a CLI script or command that would take a few seconds to execute, it would be interesting to compare the speed of execution of the same script on both systems when operated in the terminal.  If my theory that it's "all video" is correct, then the execution time would be the same on both systems.

---

### Post by cottfcfan on 2010-03-02
dabl,

Do you mean it could be graphics card related?
I have to use the proprietary FGLRX driver for my HD2400 card, and have wondered if KDE just handles it better than Gnome.

---

### Post by dabl on 2010-03-03
No, there should be no difference between the speed of your GPU itself when the same driver is being used in Ubuntu and Kubuntu.

But, the efficiency of KDM/KDE, when using your graphics system, is apparently better than GDM/Gnome. I do not know why that would be -- probably that's why I'm not a display manager developer.  :D

Down in [[COLOR="SeaGreen"]**this**[/COLOR]](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that) article is a script.  If you really, really want to prove whether the underlying Linux systems run the same speed, you could exit X with Ctrl-Alt-F1, then shut down the X server with "sudo service kdm (or gdm) stop", and then run that script, while timing it, first in Kubuntu and then in Ubuntu.  My two cents bets they are about the same, which would prove that it is only the display manager that is handling it differently.

---

### Post by cottfcfan on 2010-03-03
Shame because i do like Gnome.
But the lag gets irritating eventually, guess i`ll stick with KDE until 10.04 is released.
 My graphics card has kernel support in the next release, so that will hopefully solve my problem.

---

