---
title: "Suggestions of lightweight *buntu distros (Lubuntu?)"
date: 2010-05-23
forum: General Help
---

### Post by racie on 2010-05-23
Hey everyone.  I have a really old computer running Windows 98SE right now and it works OKAY, but it does not support the wireless card.  Now, I've tried the official derivative, Xubuntu, on this machine, only to find that it is more resource heavy than it appears to be, running like a turtle on the computer.  However, I found the wireless card to be working right out of the box with nothing I had to do to set it up.

I've been looking into Lubuntu, which is said to be even lighter than Xubuntu.  They recently released a "stable beta" of Lubuntu 10.04.

Has anyone tried this or anything else that is even lighter than Xubuntu?

The computer has 254MB of RAM and has an Intel Celeron 565MHz processor.

Any suggestions are appreciated!  Thank you.

---

### Post by tolanri on 2010-05-23
I installed Lubuntu yesterday on my netbook and it's great. It's been long time since I tried Xubuntu, but in my opinion it runs better than Xubuntu and is less resource hungy.

After reading your question I think I'll try to install Lubuntu on Virtual Machine with 256MB RAM and see how it runs out of the curiosity :) Will report back later.

---

### Post by wilee-nilee on 2010-05-23
I like Puppy Linux here is a pretty cool puplet.
[http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/](http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/)
And here is the latest Puppy
[http://puppylinux.org/wikka/LucidPuppy](http://puppylinux.org/wikka/LucidPuppy)
Here is another, although I couldn't get the mouse to work upon install, bu I didn't try that hard.
[http://brainwavedesigncentral.net/mike/Bruno-pup.html](http://brainwavedesigncentral.net/mike/Bruno-pup.html)

---

### Post by wojox on 2010-05-23
> **wilee-nilee said:**
> 
And here is the latest Puppy
[http://puppylinux.org/wikka/LucidPuppy](http://puppylinux.org/wikka/LucidPuppy)


+1 for LucidPuppy. Comes packed full of applications and is fast and lightweight.

---

### Post by tolanri on 2010-05-23
Lubuntu 10.04 "beta stable" takes to boot to desktop (stopwatch start at grub selection menu, stopped at fully loaded desktop environment) ~35secons on my Acer AspireOne 531h netbook.

Also I'm done installing Lubuntu on Vmware with only 1 core enabled CPU at 3000MHz (Q6600) and with 256MB of RAM.

Installation took precisely 10:02 (CPU was fully loaded almost at all times during installation process, RAM usage was at around 160MB during installation). I installed the system from mounted image file so that explains high CPU usage.

Boot took 18 second (from GRUB selection to fully loaded desktop). Memory consumption after boot reported by Xfce4 Taskmanager is about 180MB.

System seems very responsive, loading applications (tried Chrome, Abiword) takes only two or three seconds.

Started Pidgin, Google Chrome, Abiword, Xchat, File manager, and Xfce4 Taskmanager at the same time, it took about 20seconds to open them all. Xfce4 Taskmanager reports Memory consumption with all of these applications running at 201MB.

Here is free -m result after boot:

```
tolanri@tolanri-vmware:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           244        240          3          0          7         48
-/+ buffers/cache:        185         59
Swap:          713          0        713
```And here is free -m with all above applications running.

```
tolanri@tolanri-vmware:~$ free -m
             total       used       free     shared    buffers      cached
Mem:           244        241          3          0          4          32
-/+ buffers/cache:        204         39
Swap:          713         30        683
```Responsiveness slowdown caused by swapping is noticeable, but still it's very  responsive.

---

### Post by itachisxeyes on 2010-05-23
well, i'm not sure of any other Ubuntu based distros, but Damn Small Linux, is quite lightweight and is Debian based just like Ubuntu. also Knoppix is another Debian based lightweight distro. though Knoppix is more of a repair disk.

---

