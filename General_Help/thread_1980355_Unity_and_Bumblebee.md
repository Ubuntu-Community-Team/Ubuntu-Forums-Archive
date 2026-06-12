---
title: "Unity and Bumblebee"
date: 2012-05-15
forum: General Help
---

### Post by Welly Wu on 2012-05-15
I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD running a clean installation of Ubuntu 12.04 64 bit Long Term Support. My laptop has the Intel Ironlake integrated graphics and a nVIDIA GeForce GT 325M GPU with nVIDIA Optimus technology. I installed Bumblebee Project 3.02 and it works right out of the box. In Unity 3D, I want to change some of the software packages to use the optirun command such as Mozilla Firefox, VLC, XBMC to take advantage of my nVIDIA GeForce GT 325M GPU. How do I do this? Please instruct with step-by-step directions. Thank you.

---

### Post by Henne91 on 2012-05-15
Here you'll find a few information on Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

> In Unity 3D, I want to change some of the software packages to use the  optirun command such as Mozilla Firefox, VLC, XBMC to take advantage of  my nVIDIA GeForce GT 325M GPU.No need to do this! Bumblebee is supposed to run things on your NVIDIA card that need heavy graphics stuff. Regular programs like Firefox don't need this.

However, you should use your NVIDIA card for 3D or graphic-extensive games or maybe HD videos. To do so you just have to open up a Terminal by entering "terminal" into the Dash. Now type "optirun <executable-name>" where >executable-name> is the name of the executable of the program you're trying to run.

For example: "optirun glxgears" or for Firefox it would be "optirun firefox"

---

