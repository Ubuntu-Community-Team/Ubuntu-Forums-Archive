---
title: "Some problems"
date: 2010-07-27
forum: General Help
---

### Post by Quackers on 2010-07-27
Hello all,
I hope somebody can help with a few problems I'm having.
I have a Sony Vaio AR51SU.
The first partition is a backup 
The second partition is Windows Vista
The third partition is Mac OS X - Snow Leopard
Today I installed Ubuntu 10.04 on a fourth partition.
The installation was smooth and all hardware worked right away (after downloading a driver for my 8600M GT graphics card).
I used Ubuntu for about 3 hours then rebooted in an attempt to boot Vista.
On restarting the grub menu came up and gave me the choices of Ubuntu/Ubuntu recovery/Ubuntu/Ubuntu recovery/MemTest/MemTest/ Windows/Windows recovery/Mac OS X 32 bit/Mac OS X 64 bit.
It's a big menu :D
However the only OS that would boot was Ubuntu.
After using the Vista dvd I set Vista partition as active and used bootrec /rebuildbcd. After this Vista was bootable.
I then used EasyBCD (already used for booting Mac OS X previously) and added an entry for Linux as well.
However neither Mac OS X or Ubuntu will boot from the Windows bootloader - even though the entries appear. When I use the entries for Mac or Ubuntu the boot fails very quickly.
Even so, the first menu on pressing the start button is still the grub menu (not Windows bootoader).
Have I missed a step or two? 

Also, in case this is relevant, when in Ubuntu the sound now doesn't work (no output device) whereas I was listening to the radio earlier! and Ubuntu will not restart or shutdown - it just logs me out. Both worked ok earlier.

Any advice would be very appreciated. 
Thanks

---

### Post by Quackers on 2010-07-27
Now the sound is working but no speaker icon in top panel.

---

### Post by Quackers on 2010-07-27
A further update.
I now have Ubuntu booting from the Vista bootloader and I have Vista booting from the grub menu.
This is good improvement.
However I can't boot Mac OS X from anywhere! More reading then!

---

### Post by Quackers on 2010-07-27
Now I can boot Vista and Mac OS X from the Vista bootloader but not Ubuntu even though Easybcd says it's there.
I can only boot Ubuntu and Vista from the grub boot loader - not Mac OS X.
Ah well at least I can boot them all now - even though I have to use different bootloaders.

42 views and no replies! Don't you like me? Or the subject? :-)

---

### Post by Vaphell on 2010-07-27
no offense, it's nothing personal
it's easy - 'some problems' is a meaningless title, so people click it out of curiosity, but apparently there was no one who would know about fixing boot problems in multiboot configurations yet

---

### Post by Quackers on 2010-07-27
Lol, I've been hanging around forums for too long to take it personally :-)
I appreciate your comment about the title, but if I'd put what I needed to the title would have been as long as the post.

I don't know how to spell it, but I think you may know what I mean when I say jinkuye  :-)

---

### Post by Vaphell on 2010-07-27
rofl, it's 'dzi&#281;kuj&#281;' :D
you could at least give a hint it's about problems with multiboot, some people here ate their teeth on such experiments and would know that they can help at a glance.

---

### Post by Quackers on 2010-07-28
Very dodgy spelling there Mr Vaphell :-)
Yes multi-boot in the title would have been a better idea. I can't edit that now can I?

---

