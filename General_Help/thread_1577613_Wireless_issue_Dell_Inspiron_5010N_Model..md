---
title: "Wireless issue Dell Inspiron 5010N Model."
date: 2010-09-19
forum: General Help
---

### Post by vishnu.vyasan on 2010-09-19
Hi Friends,

I have used kubuntu for same time in my pc and since i really become a fan of Ubuntu.

Yesterday i have tried to install the Ubuntu on my Laptop which is Dell Inspiron N5010.

I am facing a couple of problems. I installed ubuntu 10.4 desktop edition 64 bit LTS. The look and feel rocks, Thank you guys. 

1) My wireless is is not active, My laptop is having broadcom wireless card. Earlier in my pc when i installed my kubuntu, it automatically detected the networks and only thing i had to do was to enter the password for the network. Here i could not see the network's and i tried to enter things manually, but failed. 

2) I could not activate my desktop effects. I have Ati Radeon Graphics card with 1 GB memory.  What should i do for this? Should i download the graphics card driver for ATI? 

I am moving from xp to ubuntu 10.4 and its really fantastic. I travel a lot with my laptop. So this wireless issue is a showstopper for me. 

Please help me.

---

### Post by halj32 on 2010-09-19
all the drivers you need are on the CD under pool restricted
installing dkms, fakeroot, patch, and then the bcmwl-kernel-source package from the live-cd

if you are using a new 2.6.35.* kernel
see my second post here
[http://ubuntuforums.org/showthread.php?t=1571483](http://ubuntuforums.org/showthread.php?t=1571483)

good luck

---

### Post by xircon on 2010-09-19
Connect to your router with an ethernet cable and update.  Then run hardware drivers program from the menu whilst still connected, this will download the new drivers.

This assumes your machine has the DW1501 card. To check run lspci from a terminal and look for a line like:

```
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

```

[IMG]http://i367.photobucket.com/albums/oo118/xircon/HardwareDrivers_001.png[/IMG]

---

### Post by vishnu.vyasan on 2010-09-19
Thanks... Guys for the Quick reply.  I will try both your intruction's and get back here.

---

### Post by vishnu.vyasan on 2010-09-20
Guys both the methodes failed. 

I tried to install the driver from Pool-->Restricted-->b-->package name. It showed a message that DPKMS missing. i downloaded and installed the package. The next time instalation happened but getting a failed message. 

I could not connet using  ethernet cable. I have to buy some. Meanwhile could we download all the packages needed for upgrade and propratry drivers from some where?

---

### Post by vishnu.vyasan on 2010-09-20
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

this is my card. But i doubt its  rev 02.

---

### Post by xircon on 2010-09-20
You need an ethernet cable.  I think you can download onto your Windows partition but do not know where from.

---

### Post by halj32 on 2010-10-13
did you try this
right Ive just been to broadcom site and you need to download & install 2 patches
sta_5.60.48.36_2.6.33_kernel_patch.zip
&
sta_5.60.48.36_2.6.34_multicast_kernel_patch.zip
extract to /usr/src/bcmwl-5.60.48.36+bdcom (as admin)
then in an terminal run

sudo patch -p0 < patch
then
sudo patch -p0 < patch_hybrid_multicast

youll probably need to install dkms ect

then run
sudo dpkg --configure -a

reboot & done everything should be working

---

### Post by vishnu.vyasan on 2010-10-13
hi,
i got this thing fixed. Actually the flgrx commands from the ati wiki did the trick.

thanks for replying.

---

