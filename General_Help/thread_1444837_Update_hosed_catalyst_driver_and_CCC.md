---
title: "Update hosed catalyst driver and CCC"
date: 2010-04-01
forum: General Help
---

### Post by esc1 on 2010-04-01
I run Karmic 64 bit on an AMD cpu. I don't know what update did this... All I know is after update and reboot I had this problem. 

A few months ago I installed the ATI driver from their site for my onboard Radeon HD 3200. On their site now they only have HD 33XX series or Radeon 3200 series on the integrated driver section. Which one would I go with? (Thanks ATI) Regardles of either one I install it doesn't work nor will it allow me to open Catalyst Control Center (CCC).

I use 
sudo sh ./ati-driver-installer-10-3-x86.x86_64.run
to install and choose install and not package specific, then automatic because that worked before.

And I use this
sudo sh /usr/share/ati/fglrx-uninstall.sh
to unistall...

Can anyone help me out here? With either installed everything still looks horrible and the screen flickers to black on processor use. With proprietary drivers from the ubuntu sources I can't enable desktop effects and it looks crummy in general.

---

### Post by NCLI on 2010-04-01
You probably had a kernel upgrade. You'll have to reinstall the driver. If you don't use the driver Ubuntu provides via Hardware Drivers, this will happen every time you upgrade the kernel. Thank ATi for not releasing the drivers as Open Source.

---

### Post by esc1 on 2010-04-01
I know a reinstall is necessary. Thanks.. did you read everything I wrote? My install isn't working and ATI doesn't even have my model listed.

There is no plain radeon 3200 so I must assume the one on Radeon site is for the HD 3200.

---

### Post by Mark Phelps on 2010-04-02
To find out what Ubuntu thinks is your video card model, since you can't run Ubuntu from your drive at this point, you should boot from the LiveCD and then open a terminal, and enter "sudo lspci". 

Look down near the bottom of that output and you will see a line describing the make/model of your video card.

---

