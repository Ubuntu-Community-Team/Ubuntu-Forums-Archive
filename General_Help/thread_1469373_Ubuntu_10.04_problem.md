---
title: "Ubuntu 10.04 problem"
date: 2010-05-02
forum: General Help
---

### Post by SerraAngel on 2010-05-02
Good morning from troubled Greece

in the past i had succesfully installed ubuntu (8.04 and newer editions) several times without any serious problems,yesterday i decided to delete my hackintosh installation and try the brand new 10.04 i386

i tried cd and usb installations for both normal and alternative isos all verified,i also checked memory for problems,please note that the pc works flawselly with windows 7 32bit

the problem is that both lived cd boot or hhd installation boot (via alternative iso only) ends loading the wallpaper only and then restarts

i am pretty sure that this is a graphics card incompatibility

my system is Gigabyte ga-ma78gm-s2h version 1.0 with built-in gpu ati radeon hd 3200,4gb ddr2 ram and a dual core athlon 64x2  5000+


thanks in advance for any help

---

### Post by dino99 on 2010-05-02
Lucid dont need xorg.conf, so you can remove it

if grub-legacy (grub1) was previously installed, you have to remove/purge all the grub packages then only install grub-pc and grub-common, then:

sudo mkconfig && update-grub

into /etc/default/grub: add or change 

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

---

### Post by SerraAngel on 2010-05-02
i think grub is version 2

resolution during boot is fine (1650x1080)

the only problem is the restart before window manager kicks in

i have to add that i searched the net a lot before i post here and i didnt find anyone with a similar problem

can you be more detailed about the procedure to remove xorg.conf as i cannot log in to ubuntu?

ps i did a clean install via alternative iso

---

### Post by SerraAngel on 2010-05-02
still in pain

after 2 reboots in a row i managed to enter the ubuntu desktop i386 live usb and installed it to hdd in a separate partition

resolution during boot and in live cd session is fine (native 1650x1080)

but when installation finished and restarted the pc the problem still remains,after the purple screen with dots just before log in the screen goes black then signal loss to the monitor and pc restarts

i tried failsafe graphics mode,normal boots and every possible choice with no success

any ideas?

---

### Post by zearth on 2010-06-25
hi can someone help me, I have same problem as SerraAngel, after installation from an alternative cd, and when the startup of the page open in a matter of few seconds it just restart, can someone help me about this problem, I'm using Gigabyte ga-ma78gm-s2h and ubuntu 10.04

thanks

---

