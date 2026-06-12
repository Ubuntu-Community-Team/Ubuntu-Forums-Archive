---
title: "freezes can't boot from pen drive"
date: 2012-07-17
forum: General Help
---

### Post by gahyoujerk on 2012-07-17
Hey guys, I can't seem to boot into xubuntu from a pen drive, even on my first time to explore the os.  It hangs everytime at the loading screen.

Info on my system:
Ubuntu 12.04 full install
AMD Mobile 64 processor
1 GB ram (i hope, possibly only 512MB)

It's a really old laptop I use to play around with linux.
Ubuntu works and is installed, but it's too much for my old computer I think. That's why I wanted to try Xubuntu, but it keeps freezing.
I also tried Lubuntu, but it didn't work either although puppy linux did, i just didn't like it.

---

### Post by Toz on 2012-07-17
What is the make/model of the laptop and what video card does it have? Maybe you need to boot with a specific kernel parameter (e.g. nomodeset).

---

### Post by gahyoujerk on 2012-07-18
hey thanks for the help, I managed to solve the problem.  Since I already had ubuntu installed I found out I could install the Xubuntu desktop environment from within ubuntu.

I opened terminal and typed
sudo apt-get update
sudo apt-get install xubuntu-desktop

now I can login to xubuntu or ubuntu at the ubuntu login screen or switch between them after logging out.  I'm happy I found this out, cause I can now use xubuntu and ubuntu.

---

