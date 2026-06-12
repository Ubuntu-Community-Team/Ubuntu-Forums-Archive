---
title: "3d ati aceleration"
date: 2010-05-21
forum: General Help
---

### Post by josedb on 2010-05-21
Since i ve installed ati propetary driver i cannot get 3d aceleration back to work.

Xorg logs shows this:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by LowSky on 2010-05-21
We need More information please.

What model graphics card?
What version of Ubuntu?

---

### Post by josedb on 2010-05-21
Ubuntu 10.04
Ati hd4200 (notebook)


Ive installed ati driver from amd website
aceleration stop working, cannot remove ati website driver so installed fglrx from synaptic
Cannot restore aceleration yet.

---

### Post by apuglisi on 2010-06-01
try initializing your driver installation with the next command in your terminal:

> sudo aticonfig --initial -f

as specified by the ATI Catalyst installer, just after finishing the installation. Hope it helps.

---

