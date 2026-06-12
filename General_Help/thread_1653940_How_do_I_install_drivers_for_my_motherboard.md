---
title: "How do I install drivers for my motherboard?"
date: 2010-12-27
forum: General Help
---

### Post by varundeshpande.vd on 2010-12-27
Hi,

I am absolutely new to Ubuntu. I have so far managed to install Ubuntu 10.10 on my desktop. I have just started to check the options on it and was unable to change the Visual effects under Appearance preferences. It gives me error Driver not installed. I am using the ASUS A8V motherboard that has VIA K8M800 display chipset integrated. I also have the Motherboard driver CD with me but I don't know how to install the drivers? I am totally new to this place.. hope this makes sense... Please help...

---

### Post by wojox on 2010-12-27
Go to System > Admin > Hardware Drivers and see if there is anything to activate. ;)

---

### Post by dagoth_pie on 2010-12-27
First things first, Linux has most of the drivers built in, so odds are that you don't need to install any drivers. There are a few exceptions, the main one being graphics cards, normally a via chipset should run fine "out of the box" with no setup needed after the installation.

The bad news here is, although I'm not 100% sure, I'll give it a quick google, most integrated graphics cards aren't made to run 3d OpenGl applications, such as the desktop effects. I'll have a look and see what I find about your graphics chipset. In the meantime someone else might be able to help more.

---

### Post by dagoth_pie on 2010-12-27
Ok then, from my quick research, I've found your chipset should have basic OpenGL support. I'd recommend looking for a cheap 8x AGP card to put into your system, seeing as your motherboard would support it. But to get 3d rendering on your chipset you should be able to go to the terminal and type (or copy and paste)
```
sudo apt-get install xserver-xorg-video-via
```
That should install the drivers, then you just need to restart the xserver, the simplest way to do that is to just reboot your pc. I think, although I have been out of the loop for a while now, that your xserver should detect the new Openchrome drivers that command will install on your system. If it doesn't work then it might take some tampering with the xorg.conf file to get it to use the correct drivers.

---

### Post by varundeshpande.vd on 2010-12-30
Hi,

Thank you for the replies. I did try that command on terminal but unfortunately it did not work! I think I should go per your advise to get a simple AGP 8X card that is supported by me system and probably that should work..!!!

Thanks a lot again.

---

### Post by dagoth_pie on 2010-12-30
If I could reccomend one, it would be an Nvidia Geforce 6 series card, a 6800 would be good if you can find one cheap, they were some of the last ones to be made before everything shifted to Pci-e, but are still easy enough to get drivers running fine on Linux. Although if you aren't going to be doing anything more than run the compiz desktop effects then any geforce 5 or 6 will do. I'd reccomend not going any older than that though, I used to have a Geforce 5200 which ran flawlessly, even overclocked to run double the speed. But I've nevcer had a Geforce 4 play nicely with the Nvidia drivers packed with Ubuntu.

Unfortunately I can't make any suggestions on the Ati side of things, however I can say I have had a few Ati cards run fine on linux.

---

