---
title: "Scanner Optrox on KUbuntu"
date: 2006-04-11
forum: General Help
---

### Post by albé on 2006-04-11
Hello,

I am trying to use my 7/8 j old Scanner "Optrox Photomaker 3E" to work via
KUbuntu 5.10.
Apparently there are no drivers for this one? This Company does not exists
anymore, since a few years.

It works fine under Win98/Win2000pro.

Does someone know a way? I use XSane :-) and a very new "newbie" in Linux.
Connected direct to LPT1 and printer out to my HP916C

Thanks in advance,

---

### Post by Neeko on 2006-04-17
There are two things you need to make this work.

1. The scanner must be supported by SANE, unfortunately for you, this scanner is not, according to the SANE project site [http://www.sane-project.org/sane-mfgs.html#Z-OPTROX]("http://www.sane-project.org/sane-mfgs.html#Z-OPTROX")

2. Assuming the scanner would work with another SANE driver (unlikely but possible) you may need to re-compile the linux kernel to include scanner support for your paralell port scanner (I can't recall the exact name of the kernel option you must enable) as I don't think its enabled by default.

---

### Post by albé on 2006-04-18
[QUOTE=Neeko]There are two things you need to make this work.

1. The scanner must be supported by SANE, unfortunately for you, this scanner is not, according to the SANE project site [http://www.sane-project.org/sane-mfgs.html#Z-OPTROX]("http://www.sane-project.org/sane-mfgs.html#Z-OPTROX")

  2. Assuming the scanner would work with another SANE driver (unlikely but possible) you may need to re-compile the linux kernel to include scanner support for your paralell port scanner (I can't recall the exact name of the kernel option you must enable) as I don't think its enabled by default.[/QUOTE]

  Indeed, it is not supported.

  I kept a small partition with Win 2000 to use my scanner when I need it.     (not often :-)  ) I will probably buy a new one.

  Thanks anyway for your reply!

---

