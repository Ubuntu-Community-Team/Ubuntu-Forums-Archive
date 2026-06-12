---
title: "Graphics Problems in 9.10"
date: 2009-11-05
forum: General Help
---

### Post by aren55555 on 2009-11-05
Okay here I go; so I decided that I was going to install Ubuntu 9.10 on my Toshiba A300 laptop. Installation - no problem.

My machine boots up with 9.10 and I install the updates it prompts me with. Then the machine asks me whether or not I want to install/enable the restricted drivers for the ATI Mobility Radeon HD 3450 that my laptop shipped with. The installation goes well - no errors.

After restarting my machine I only see a black screen and the CAPS LOCK light is flashing On and Off. So I boot into recovery mode and do:
```
sudo nano /etc/X11/xorg.conf
```
I change the line driver from "fglrx" to "vesa" save the file and reboot. Okay, 9.10 boots up fine and I can actually see the GUI, no more black screen. So I download the ATI Catalyst drive for my card and install it. After restarting my computer, I get the exact same issue - black screen with CAPS LOCK flashing.

So I boot into recovery mode and change the simlar line to "vesa" in the xorg.conf file.

Once again I boot up 9.10 and I have my GUI back. Now my problem is: how exactly do I obtain drivers for my hardware so that I can use 3D applications like compiz? Was I doing something wrong in my previous driver installs?

Please note that I am not a linux/ubuntu/command line pro although I know a lot more than the basics - so please direct the advice at an intermediate level. Furthermore if I was not clear enough please do post and I will get back quickly.

Thanks in advance for your help, I truly appreciate it!

---

### Post by fragos on 2009-11-05
You might try "radeon" for your driver. It's in the default Ubuntu install.

---

