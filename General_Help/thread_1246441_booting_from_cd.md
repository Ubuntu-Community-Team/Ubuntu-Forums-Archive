---
title: "booting from cd"
date: 2009-08-21
forum: General Help
---

### Post by Kanga on 2009-08-21
Hi,I'm running a dual boot system with 2 hard drives, Hardy Heron and windows xp.
I wish to try running fedora from a live cd, but if I restart computer and press esc to get into bios, choose option to boot from cd, system starts to load from cd, and then screen shows grub menu. If I ignore grub and dont choose options, then system boots into Heron.
How do I run from live cd please ?

Thanks

---

### Post by jtravnick on 2009-08-21
Are you sure that the cd you are trying to boot is a live cd? Also when you go to leave the bios are you saving changes?

If your bios is set to boot to the cd first than the problem is in in the cd.

The computer will look at the cd if its bootable than it will boot it. If not than it goes to the next drive that is set in the bios if it has a bootable operating system it will boot it if not than it goes to the next drive and so on and so on.

---

### Post by Jerry.S on 2009-08-21
When you boot up do you see a prompt for boot menu. On my system if I press F8 at the same time I see the bios prompt I will get a menu that list all of my drives and then I can select from were I want to boot from

---

### Post by VipX1 on 2009-08-21
You don't say what Motherboard you have, weather it's a laptop or a desktop so it's hard to help. Usaully it's the DEL key to get into the BIOS or F2.In the BIOS go to BOOT DEVICE PRIORITY and set your CD drive to the first entry in the list (your primary hard drive must be listed too, don't remove it completely) and press F10 and YES to exit. Then you'll see the Fedora Live CD when you reboot. 
If your getting the boot menu by pressing ESC, as some ASUS motherboards do that and then selecting your CD drive but it still goes to your default boot OS, in this case 8.04 Hardy then I suspect the CD is not working correctly. 
I hope this helps.

---

### Post by lisati on 2009-08-21
I don't know about the Fedora CDs but some bootable CDs I've used pop up a message along the lines of "Press a key to boot from CD" - if you ignore it, or are distracted and miss it, then the "normal" boot sequence resumes, bypassing the CD

---

### Post by Kanga on 2009-08-24
Sorry for delay guys,
computer is Dell dimension desktop 4100
pentium 3 930mhz
384mb ram
windows xp pro on 40gb hdd
ubuntu on 30gb hdd
motherboard is intel 815
other numbers are:-
FW82815
LO400385
SL4DF
Intel 99
DELL REV. A01
E 139761
V N 232
AA A10383-403
DS/N MY 02336V-OBS 05BA  CSO MY


I know that Fedora has started to load from cd because I saw it on screen, then I did nothing and Ubuntu started.
I just cant load from cd because the Grub menu only gives a choice of only various kernels of Ubuntu, and xp.
I think that Grub wont let the cd take priority, and Ubuntu is on the master drive and xp on the slave, hence Ubuntu loads as priority.

---

