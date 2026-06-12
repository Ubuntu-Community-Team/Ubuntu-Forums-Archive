---
title: "need help with 8.4 desktop Installation"
date: 2010-06-07
forum: General Help
---

### Post by snake_eyes on 2010-06-07
Hello,

I'm trying to install Ubuntu 8.4 in the following server specification:

these are the server :

Motherboard intel origional DG41RQ
CPU Intel core2due 2.93Ghz 64bit
Ram 4GB
2 harddisks each 1 terra

but I got Operating system not supported, can some body help me with this matter?

Please note that I tried 9.4 also the same unlike 10.4 it works properly...

Waiting your reply plz...

Cheers,

---

### Post by xoomer.ap on 2010-06-07
Maybe, you have in mind 8.04 ;) ?
> but I got Operating system not supported, can some body help me with  this matter?
Where concretely you got this?

---

### Post by snake_eyes on 2010-06-07
> **xoomer.ap said:**
> Maybe, you have in mind 8.04 ;) ?

Where concretely you got this?

I'm getting this at the first CD Booting :(, but I need to install the 8.4 because I gonna install Zimbra and still they didn't support 10.4 

Any advice?

---

### Post by xoomer.ap on 2010-06-07
Wow...

Looks like this is not Ubuntu installer words...
Are you trying to boot installer of Ubuntu from CD at real (non-virtual) machine?

---

### Post by snake_eyes on 2010-06-07
> **xoomer.ap said:**
> Wow...

Looks like this is not Ubuntu installer words...
Are you trying to boot installer of Ubuntu from CD at real (non-virtual) machine?

yes I'm trying to install Ubuntu for the installer (non-virtual) I thing there is something wrong with hardware because I tried deferent CD's but the same,,

What I supposed to do dears?

Cheers,

---

### Post by xoomer.ap on 2010-06-07
Please tell little more about where showing up this message?

Sorry, sounds naively, but I think there is no problem with installer of Ubuntu. Looks like some software for booting can not load some disk, because that disk not have any bootable OS.

Sorry, sound naively again, maybe you should look at "boot priorities" in your BIOS settings or on other similar bases?..

Respectfully, xoomer.ap.

---

### Post by snake_eyes on 2010-06-08
Again Thank you for your cooperation with this matter,

Dear, If there is a problem with the Booting or something else why the 10.4 is booting smoothly? I don't know if there is special I must done before installing 8.4 such as compatibility between H.D. IDE, SATA or some else...

Cheers,

---

### Post by xoomer.ap on 2010-06-08
> I don't know if there is special I must done before installing 8.4 such as compatibility between H.D. IDE, SATA or some else...
Maybe, maybe. Try it. Maybe you should take a look at emulation IDE-mode in SATA-controller's options in your MoBo's BIOS?..

---

### Post by basel2010 on 2010-06-10
hi
i have the same problem

this is the messgae it give to me

udeved-event[1496]:run_program:'/sbin/modprobe' abnormal exit
BusyBox v1.1.3(Debian1:1.1.3-5ubuntu12) built-in shell (ash)
Enter 'help' for list of built -in commands

(initramfs)

---

### Post by snake_eyes on 2010-06-10
> **basel2010 said:**
> hi
i have the same problem

this is the messgae it give to me

udeved-event[1496]:run_program:'/sbin/modprobe' abnormal exit
BusyBox v1.1.3(Debian1:1.1.3-5ubuntu12) built-in shell (ash)
Enter 'help' for list of built -in commands

(initramfs)

I tried again, also I got the same message :(

---

