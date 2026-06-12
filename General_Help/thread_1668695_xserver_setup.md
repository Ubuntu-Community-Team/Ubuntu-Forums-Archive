---
title: "xserver setup"
date: 2011-01-16
forum: General Help
---

### Post by necco on 2011-01-16
greetings.

i am evaluating the use of ubuntu 10.10 on a dell "hybrid studio". the video card has a 256Mb VRAM and (i think) is an integrated i810.

gnome panel proposes a max 4/3 resolution of 1024*768@60Hz, my good old trinitron screen goes up to 2048 and is otimized for a 1600*1200@85Hz resolution.

i have tried to run as root dpkg-reconfigure xserver-xorg on tty1 but nothing happens and i have my "#" back. ctrl-alt backspace does not work to kill gnome and when stopping Xorg through /etc/init.s/stop gdm the procedure freezes trying to check the battery level.

does anybody has a clue on how i can get a decent workspace?

thanks in advance.

necco

---

### Post by necco on 2011-01-19
thanks a lot for your interest, it has been solved by forcing monitor detection

---

