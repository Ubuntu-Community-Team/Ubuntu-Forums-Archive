---
title: "No sound, permissions, or shutdown options."
date: 2010-09-22
forum: General Help
---

### Post by Slinky Owl on 2010-09-22
My Ubuntu 10.04 system does not always boot up properly. Ever since Ubuntu 10.04 it has been booting up with these few issues more often than not. 
Firstly, my sound does not work and my system does not detect a sound card according to the "aplay -l" command. It should be detecting my soundblaster, though I cannot tell you its model for, currently, I cannot detect it :(. 
Secondly, I do not have permission to access any storage media that is not my filesystem, ie MP3 players, external HDD, or even my secondary HDD that is connected via SATA inside my machine. Whenever I try to open one of these storage devices, I get an error "Unable to mount 250 GB filesystem   Not Authorized" or a similar message. 
Thirdly, I cannot shutdown my system without using the terminal. Any icon or option to shutdown/reboot are either grayed out, or are removed completely.
On the off chance that my system boots up correctly, which it does sporadically, everything works just fine. Soundcard is detected, I can access storage media, and even the shutdown options that were gone are back to where they should be.
Normally, I would think about treating this as three different problems, however, they consistently occur together. I NEVER only see one or two. 
Any ideas? Questions? Was I clear enough on my problem??

Ubuntu release 10.04(Lucid) Kernel 2.6.32-24-generic GNOME 2.30.3
2.9 GB RAM, AMD Phenom quad core, EVGA nForce 730a motherboard.

---

### Post by lkjoel on 2010-09-24
> **Slinky Owl said:**
> My Ubuntu 10.04 system does not always boot up properly. Ever since Ubuntu 10.04 it has been booting up with these few issues more often than not. 
Firstly, my sound does not work and my system does not detect a sound card according to the "aplay -l" command. It should be detecting my soundblaster, though I cannot tell you its model for, currently, I cannot detect it :(. 
Secondly, I do not have permission to access any storage media that is not my filesystem, ie MP3 players, external HDD, or even my secondary HDD that is connected via SATA inside my machine. Whenever I try to open one of these storage devices, I get an error "Unable to mount 250 GB filesystem   Not Authorized" or a similar message. 
Thirdly, I cannot shutdown my system without using the terminal. Any icon or option to shutdown/reboot are either grayed out, or are removed completely.
On the off chance that my system boots up correctly, which it does sporadically, everything works just fine. Soundcard is detected, I can access storage media, and even the shutdown options that were gone are back to where they should be.
Normally, I would think about treating this as three different problems, however, they consistently occur together. I NEVER only see one or two. 
Any ideas? Questions? Was I clear enough on my problem??

Ubuntu release 10.04(Lucid) Kernel 2.6.32-24-generic GNOME 2.30.3
2.9 GB RAM, AMD Phenom quad core, EVGA nForce 730a motherboard.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by Slinky Owl on 2010-10-03
I think I may have found an answer to my problems. I created a new installation of Ubuntu and followed as many steps as I could remember when creating it the first time. Everything worked perfectly until I installed the proprietary drivers for my nVidia card. On the required reboot after installing that driver, my system started up with no sound, no permissions, and lost the means to shutdown. I've since removed those drivers from my first Ubuntu installation and immediately things are working perfectly, though I will give this some time seeing how sporadic this problem was.

---

