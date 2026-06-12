---
title: "Intel's graphics drivers for Ubuntu"
date: 2009-12-03
forum: General Help
---

### Post by Clive McCarthy on 2009-12-03
Intel's graphics drivers for Ubuntu (from Tungsten Graphics, who sold out to VMware) are markedly inferior :( to the Intel written drivers for Windows :o. It's so bad that Ubuntu is not usable for some graphics intensive work. Intel produces more graphics chips than Nvidia & AMD/ATI combined so this is not simply a matter of getting better hardware.

The hardware is fine, it's the drivers.

The X4500 may not be the best GPU but the Tungsten drivers make it useless with Ubuntu. The Nvidia Ion is not only superior on Windows it utterly creams the Intel hardware on Ubuntu.

My question: does anyone know how where there is an open source driver project to correct this?

:popcorn:

---

### Post by lidex on 2009-12-04
The only thing I've seen recently:
[http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html")

---

### Post by Clive McCarthy on 2009-12-04
Thanks. As it happens I've already tried and am using 9.10 -- I think earlier versions of the OS had worse problems.

Maybe Intel will take a hint and write drivers now that Tungsten has been acquired and is probably moving on. Intel makes a point of declaring their driver approach to be Open Source -- but this is a case where closed-source drivers (written by Nvidia for their hardware) result in a better product.

---

### Post by Clive McCarthy on 2010-12-06
Good-bye to Intel GPUs and good-bye to Win XP.

I have found that the _latest_ Nvidia drivers for Ubuntu are great. They may even be better than the Win XP ones. It's worth the hassle to install the latest ones and NOT the ones from the repository --unless you want to sacrifice 75% of the hardware's performance.

[CENTER][IMG]http://www.phoronix.com/data/img/results/nouveau_gallium3d_first/3.png[/IMG][/CENTER]

I get excellent performance out of the ION/9400 GPU with Ubuntu and the Nvidia proprietary driver so I no longer need XP. The Intel X4500 drivers from the Tungsten "open source", running the same OpenGL application, die with segmentation violations. Side by side Ubuntu and Win XP with Nvidia drivers and the GeForce 9400 are entirely comparable in performance.

:popcorn:

---

