---
title: "Black Screen After Clean Install"
date: 2012-01-12
forum: General Help
---

### Post by borth92 on 2012-01-12
So I installed Ubuntu 11.10 on my HP Pavilion dv6 with an A8 processor and HD Raedon graphics. I can install the fglrx graphics if only I can get to a command line. But root shell prompt in recovery mode is not letting me use apt-get or edit Sources.list. So I need someone to get me to a low graphics mode that I can see or to a command line that can install programs. I'm very frustrated, someone please help!

---

### Post by topsites on 2012-01-12
To my understanding you can Ctrl-Alt-F1 to a command line after it is done booting, even from a black screen.
Also in Ubuntu we precede all our commands with sudo...
sudo apt-get etc
sudo edit etc

---

### Post by xyzzyman on 2012-01-12
At grub, press 'e' and change

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT=”nomodeset single”
```

You will then need to install the driver from ATI's site. I used wget and typed the URL manually after getting it from my phone, but you could always install links or lynx from apt-get (Which I never think to do in those situations.) Had a time getting it installed on a Toshiba notebook with that A8 cpu/gpu in it.

---

### Post by borth92 on 2012-01-13
ive tried almost every variant of nomodeset, but generally with single before it so ill have to give that a try. and ctrl alt f1 doesnt show

---

### Post by borth92 on 2012-01-13
> **topsites said:**
> To my understanding you can Ctrl-Alt-F1 to a command line after it is done booting, even from a black screen.
Also in Ubuntu we precede all our commands with sudo...
sudo apt-get etc
sudo edit etc

sudo is not required in the root shell...your root...but anyways I tried it with and without and theres a permissions issue

---

### Post by xyzzyman on 2012-01-13
I just remembered. To install the ati driver I wound up having to chroot into the installation and install it that way. Duh. My bad. Now the question is, do you know how to chroot into an installation?

---

### Post by borth92 on 2012-01-15
i do not, but thats okay. I added nomodeset single to the boot and got to a different black screen with a blinking underscore in the upper left corner. Then ctrl+alt+f1 got me to the command prompt. Thanks for the ideas guys, I'm back on Ubuntu!

---

