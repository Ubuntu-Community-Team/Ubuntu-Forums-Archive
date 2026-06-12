---
title: "Wireless &amp; Brightness problems with Ubuntu 12.04 on Pavillion G6"
date: 2012-04-27
forum: General Help
---

### Post by Mitko1239 on 2012-04-27
Hi, everyone!
So today I installed Ubuntu 12.04 on my laptop, which is HP Pavillion G6-1211eu, but I've encountered these problems:

1) My Wi-Fi is stuck on connecting, although the Ethernet connection works.
2) Ubuntu starts on minimum brightness so I have to change it on every start.

Hope you can help me out with these problems. :)

---

### Post by Mitko1239 on 2012-04-28
> **Mitko1239 said:**
> Hi, everyone!
So today I installed Ubuntu 12.04 on my laptop, which is HP Pavillion G6-1211eu, but I've encountered these problems:

1) My Wi-Fi is stuck on connecting, although the Ethernet connection works.
2) Ubuntu starts on minimum brightness so I have to change it on every start.

Hope you can help me out with these problems. :)

Anyone?

---

### Post by michyzazu on 2012-04-30
I have the same problem for brightness in Ubuntu 11.04.
The g& series of HP have 2 different video card, the HD intel graphics and the radeon one.
Brightness is controlled by the HD intel graphics so you have to put in terminal this line to change brightness: "echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness" were the number stands for the intesity that you want.
If it doesn't work try by controlling the path, because you have a different version of ubuntu.
For the part concerning the wifi card i need to know the model.
You can know it by writing in terminal lspci and looking under "Network controller".
I didn't find yet a method for using shortcuts to change brightness so you have to put every time that line in terminal. 
I hope this helps you!

PS sorry if I made mistakes writing in English..

---

### Post by michyzazu on 2012-04-30
I had a look on HP site and it seems that you have my same network adapter.
I have a "Ralink rt5390". If you have this adapter open terminal and type:

sudo add-apt-repository ppa:marko-techytalk.info/ralink-wireless

sudo apt-get update  

sudo apt-get install rt5390-dkms

If you have a different card try putting your model number instead of mine in the last command.

Another advice...You have an overheat message when you turn on your computer after using Ubuntu, haven't you?
This thing will not solve it but the temperature of your pc while using Ubuntu will appreciably decrease(You should have my same video card, Radeon HD 6470m, to verify it type lspci and have a look).  
Do not install the video card driver by using the driver manager of Ubuntu and go here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

download the driver and then open terminal, by using the "cd" command navigate to your download folder(if you downloaded it with firefox you should only type "cd Download") and then use "sh amd-driver-installer-12-4-x86.x86_64.run"(It's better if you control if the name is the same, it shouldn't be different if AMD don't update the driver within few days).
Follow the instruction and install them.
Hope it helps!:KS

---

