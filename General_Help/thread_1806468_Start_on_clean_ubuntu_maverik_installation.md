---
title: "Start on clean ubuntu maverik installation"
date: 2011-07-17
forum: General Help
---

### Post by JaizEdelmann on 2011-07-17
Hey everyone, i'm running lucid lynx minimal installation, and would like to upgrade to maverik, mean while id like to start fresh on my system got a few bugs i know i can fix by starting clean, however im running a linux software raid, can this be a problem for me? or will i just beable to mount my raid in fstab as usual, also will installation of maverik minimal installation guide me through installation on same drive as my lucid / remove current system?

---

### Post by JaizEdelmann on 2011-07-18
/bump

---

### Post by dino99 on 2011-07-18
there are still some raid issues, albeit now it should be driven smootly by the latest grub/kernel

the easiest way is to change the sources.list: replace lucid by maverick

sudo gedit /etc/apt/sources.list

---

### Post by JaizEdelmann on 2011-07-20
> **dino99 said:**
> there are still some raid issues, albeit now it should be driven smootly by the latest grub/kernel

the easiest way is to change the sources.list: replace lucid by maverick

sudo gedit /etc/apt/sources.list

What do you mean with raid issues? will i lose my raid data/setup if i format maindrive and install maverik? or is it just that maverik doesent support raid yet? i dont mind just reinstalling lucid lynx, if that would mean that i dont lose my raid data. I just want a clean install

---

### Post by JaizEdelmann on 2011-07-21
/bump

---

