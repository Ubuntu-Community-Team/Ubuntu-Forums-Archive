---
title: "Ubuntu 11.04 getting stuck during loading"
date: 2011-05-21
forum: General Help
---

### Post by jacklsw2008 on 2011-05-21
Hi all,

I'm using Vaio VGN-CS16G laptop running on Windows Vista. I have been trying out Ubuntu for a few releases already and recently I tried out 11.04 natty.

Since GRUB2 is introduced, there has been trouble for me to dual boot as GRUB 2 will get hanged at random after startup. When it gets stuck, neither OS will load; it could even get stuck if I don't press anything then I tried to scroll around the boot menu but it didn't respond.

I suspected that could be the issue with my nvidia graphics card and I searched and tried multiple solutions (including adding the "nomodeset" parameter at the GRUB conf file /etc/default/grub.

The last release I tested (should be 10.10 I guess), I found a workaround by disabling the graphical terminal by uncommenting this part:
**GRUB_TERMINAL**=console

Back then, things didn't get stuck anymore whenever I boot Ubuntu or Vista. However now in 11.04, I did the same thing. No startup issue for Vista, but for Ubuntu, it occasionally gets stuck too. I'd love to hear from all of you if you have encountered this and provide inputs for me to settle this once and for all. Thank you very much.

---

### Post by linuxinstalledfromhdd on 2011-05-21
I can't stand those sony viaos..  biggest headaches on earth..  Good for windows though

---

### Post by jacklsw2008 on 2011-05-21
haha. i wouldn't want a vaio laptop anymore, nor any overpriced sony products too. :P

---

### Post by jacklsw2008 on 2011-05-30
nobody knows what's the actual usage of "console" in GRUB_TERMINAL?

---

