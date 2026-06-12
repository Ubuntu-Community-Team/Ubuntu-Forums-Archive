---
title: "after update :graphic is a mess, even terminals"
date: 2010-09-29
forum: General Help
---

### Post by KisGellert on 2010-09-29
yesterday i ran a security update , then
today when i start my computer ,graphic fail ,
some 'DRM' or flglx message dialog box appear. i cant remember.
after a reboot, screen is a mess, full with color points 
ALT-CTRL-F1 show blank screen.
i CANT DO ANYTHING. i CANT RESCUE ,or RECOVER or what.
now i write from a live cd.
please help.!!!

this is ubuntu 10.04 - 64bit

+i remember ,yesterday update contain kernel update.

---

### Post by KisGellert on 2010-09-29
Please help me!

---

### Post by 7h3d4rk0n3 on 2010-09-29
Do you know what graphics card you are using?

---

### Post by 23dornot23d on 2010-09-29
Do you get a boot menu .... can you choose the previous kernel ?

The older kernel should still be in your boot menu .... try that ...

If not ...... have you enough room on the drive ..... for a fresh install ... 

(Can you create a clean partition and re-install from your liveCD ..... this can help re-creating the boot menu and re-installing the graphics driver)

Takes 30 mins to do .........

---

### Post by KisGellert on 2010-09-30
good morning. yesterday night is suck for me with my ubuntu. MY EYES HURT!
& I DIDNT SLEEP ,ONLY LITTLE.

PROBLEM SOLVED PARTIAL
card is Radeon 3870.
the problem caused by 2.6.32-25 kernel update yesterday.
first i cant saw grub loader because 10.04 default graphical weirdness. 
 . but after digging in,
SHIFT , & E-key show me grub
then i gave boot param: "nomodeset"
this disabled some graphic acceleration(?) , 
then graphical env ,shows up & running , but terrible slow.
previous kernel rolled back.
i purged fglrx,
then 2D is fast again, thought i didnt try 3D. (this is quite good for me . Im a 2D user.)
official fglrx not working. & proprietary also.
...

---

