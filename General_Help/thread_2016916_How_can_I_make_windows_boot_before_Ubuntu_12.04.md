---
title: "How can I make windows boot before Ubuntu 12.04?"
date: 2012-07-04
forum: General Help
---

### Post by JackOConnor on 2012-07-04
so recently I had the following problem: [http://ubuntuforums.org/showthread.php?t=2005923 ]("http://ubuntuforums.org/showthread.php?t=2005923")
Which I solved with alot of help. I had a problem booting either OS and had to use boot repair to fix it.

But now I have two new more minor problems:

[LIST=1]
[*]Ubuntu boots first and I have to access windows from it. I want it to be the other way around. I want to use ***Easy BCD***  as the first boot menu.
[*]When Ubuntu boots, there are two options to boot windows from.
[/LIST]
I don't mind the second one as much as the first. The first problem is my main issue. If anyone would like to help, you should probably read the thread in the link above as most of the info is in there. 

Please help, it's not urgent, just annoying!!!

---

### Post by oldfred on 2012-07-04
Some here use easyBCD, but most of us use grub.

You may do better here:
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want grub to show Windows first, you can use grub customizer which makes it easy:

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Zvlwab on 2012-07-05
run the following to put Windows on top in the grub menu:```

sudo mv 30_os-prober 09_os-prober
sudo update-grub
```

---

### Post by JackOConnor on 2012-07-05
The only reason that I actually wanted to change it was because if I turn on the computer and leave it, it will automatically go into Ubuntu after a while.

Is there a way to make it wait for user selection?

---

### Post by YannBuntu on 2012-07-05
Yes: [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

---

### Post by JackOConnor on 2012-07-05
Oh! Thanks very much:)

I changed the GRUB_TIMEOUT value to -1. That was easy. No need for easy BCD so!

Thanks again!:):):)

---

