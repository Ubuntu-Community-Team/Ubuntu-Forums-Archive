---
title: "How to set the timer for Dual-boot?"
date: 2010-07-07
forum: General Help
---

### Post by Abu Azzubair on 2010-07-07
I've installed Linux Ubuntu 10.04 LTS on my computer, and the Dual-booting shows after starting the computer

But what I need to know is how do you set the timer so that if I don't press "Enter"...that it choses my preferred operating system in a certain period of time (seconds or minutes...etc) by itself?

Thanks in advance O:)

---

### Post by Meskarune on 2010-07-07
You have to edit the grub.cfg file. This file is located at /boot/grub

In the file there is something that looks like:  

GRUB_TIMEOUT="10"

This number sets the number of seconds we want GRUB to wait before automatically booting the default boot entry, unless any key is pressed to cancel the count-down timer.

    * We can change this number to a smaller number of seconds if we want our computer to boot a little faster.
    * We can set this number to a higher number of seconds if we want more time to hit a key or decide what operating system we might want to boot.
    * We can change this number to  -1  if we want to keep the countdown timer on hold and have GRUB wait forever or until we come back and tell GRUB what we want to do.

read more here: [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

