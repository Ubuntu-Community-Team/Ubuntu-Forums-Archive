---
title: "Ubuntu 10.04 doesn't complete boot"
date: 2010-08-23
forum: General Help
---

### Post by palley92 on 2010-08-23
First, I apologize for my English; I've tried to make it as clear as possible.
 
Some days ago I had Windows XP and Ubuntu 10.04, obtained by upgrading from 9.10, installed on dual boot (same HD).
However, I had some issues with Ubuntu's boot: after its selection in GRUB, the login panel would not display and the screen would remain black.
I was told that upgrading might lead to problems, so I uninstalled Ubuntu 10.04 and installed it by CD.
Now I have Windows Vista and Ubuntu 10.04 (this time the CD-installed version) on dual boot, but Ubuntu after 4-5 uses doesn't boot anymore!I've also tried to boot in recovery mode, but that was no use(the recovery panel does not show up).
 
I'd greatly appreciate you help, and, if you need some hardware info just tell me (possibly how to get it too).
 
Thanks

---

### Post by davidmohammed on 2010-08-23
hi there and welcome.  What is your graphics card?

type in a terminal session

lspci | grep VGA

Please copy and post the results here.

---

### Post by palley92 on 2010-08-23
I can't access Ubuntu, it doesn't boot.
Anyway, my graphic card is a SAPPHIRE Radeon X1550.

---

### Post by davidmohammed on 2010-08-23
when you boot, press shift and it will display the list of kernels - this is your grub.

press e and then look for the line ending

... quiet splash --

change this to look something like

... nomodeset quiet splash --

CTRL + X to boot

---

### Post by palley92 on 2010-08-24
OK I've done it. Now it works, but, after I login, some strange colored lines appear before the loading of the desktop, and then it resizes to the default screen resolution, which I have to change manually.
Also, if I use graphical effects such as the cube, flashing lights appear. Is there some way to fix that too?

---

### Post by davidmohammed on 2010-08-24
I dont have an ATI card, so I've copied and pasted some stuff you can try from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver").  If it doesnt work, try the stuff in the second link to clean up the installation.

Use Administration - Hardware drivers and activate the ATI driver

if there is no driver to install

open a terminal session and type

sudo apt-get install fglrx-modaliases

reboot

Use Administration - Hardware drivers and activate the ATI driver.

---

