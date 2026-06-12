---
title: "live cd - input signal outt of range"
date: 2009-10-21
forum: General Help
---

### Post by OA-5599 on 2009-10-21
Hello,

I'm trying to boot the 9.10 beta live CD but after the splash screen it says "input signal out of range".
The CD boots fine on a different Computer.
I've seen a lot of threads about this subject but still haven't found a solution.I've tried setting different boot parameters, safe graphics mode, reconfigure xserver. Older live CDs are booting fine on the same PC.

---

### Post by skatinjj on 2009-10-21
did you burn it at a slow speed (if you did burn it)?

---

### Post by OA-5599 on 2009-10-21
yes, I burned it at a slow speed.
Also just tried a usb startup disk.
But I get the same message.

---

### Post by OA-5599 on 2009-10-21
btw, My graphics card is a Nvidia 7600GS (I think).
It works on a PC with a Nvidia 8something.

---

### Post by skatinjj on 2009-10-21
Have you tried setting the driver and resolution manually in xorg.conf?

Short on time, if you are not sure how ask and I will respond as soon as I can).

Curiosity, can you go into the monitor settings and choose an auto setting for adjusting the display?

---

### Post by OA-5599 on 2009-10-22
I can't get into the monitor settings.
I wanted to try setting the xorg.conf manually but I can't even get into the terminal (ctrl+alt+F1) anymore.
It just shows some text and on the bottom is a blinking cursor.

---

### Post by OA-5599 on 2009-10-22
I can access the terminal again but when I open the xorg.conf the file is empty (sudo nano etc/X11/xorg.conf).
Maybe I'm doing something wrong.
Also when I type "sudo dpkg-reconfigure xserver-xorg" nothing happens.

---

