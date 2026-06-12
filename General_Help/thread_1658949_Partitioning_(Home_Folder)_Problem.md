---
title: "Partitioning (Home Folder) Problem"
date: 2011-01-03
forum: General Help
---

### Post by embra55 on 2011-01-03
Hi All.
Having been converted to using "Linux" about 8 months ago, and gaining confidence to try different distros, and figuring out how to 'keep' my Home folder, I've had great fun trying them out and learning as I go.
The latest distro I'm trying is Kubuntu, which I really like and will keep for a while. However, when I was partitioning in the set-up, I omitted to create my home folder. Instead I now have is a partition the size of my "old" home folder, and to which I have to sign into to gain access. The files are all there so that is no problem.

1. What i would like to know is if this set-up is OK, or should I change it so that it is actually in the home folder (if so how?( a re-install?))

2. If I should decide to try out another distro in the future will this be safe to change to "home"?.

Hope I've explained clearly enough, and thanks in advance for any help regarding this.

embra55

---

### Post by Bucky Ball on 2011-01-03
You might find this of interest for future reference:

[https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html](https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html)

You don't really need to install the whole thing just to try out the desktop environment. For instance, if you were running Ubuntu and wanted to try KDE (Kubuntu desktop environment), you just install kde-full (or another flavour) from Synaptics. Want to try Xubuntu? Install xubuntu-desktop. Edubuntu? edubuntu-desktop.

At login screen, hit 'Sessions' and choose the environment you want and you're away. The packages from all will be available regardless of what desktop environment (DE) you log into and if you don't like easy as going to Synaptics and uninstalling.

You can come up with some real hybrids this way. Why not Ubuntu Satanic artwork in KDE over an Xubuntu base installation? :)

My desktop is Xubuntu with ubuntustudio-audio and ubuntustudio-video packages, edubuntu-artwork, but I have a million other options installed which I can change to with a few clicks! (Laptop Ubuntu with Ubuntu Satanic artwork.)

Bit off topic but maybe for next time.

---

### Post by embra55 on 2011-01-05
Hi Bucky Ball,
Thanks for the reply, I'll give that a try soon, and yeah it is a bit of topic. However I managed to figure my problem out. I simply hadn't changed the drop down from "don't use this" to "ext4" % mount at "/home". Learning all the time (lol). Problem solved.
Thanks, Embra55

---

### Post by Bucky Ball on 2011-01-05
After posting my last thread, off topic again(!), I installed Xfce DE on my own new laptop. It's great and it flies! Just choose 'Xfce session' at the login screen.

---

