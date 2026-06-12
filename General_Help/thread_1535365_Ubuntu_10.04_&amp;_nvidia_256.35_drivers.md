---
title: "Ubuntu 10.04 &amp; nvidia 256.35 drivers"
date: 2010-07-20
forum: General Help
---

### Post by thenellt on 2010-07-20
I love trying linux every now and again to see what has changed. I do consider myself somewhat experienced with linux and other OS's having used anything from ubuntu 6.06 to mac OSX 10.6.2 on my machine. I've found ubuntu to be my favorite distro and the easiest to use and I've never run into a problem I couldn't easily solve with google until now.
I recently installed on a spare partition a clean install of 10.04 and the first thing I tried to do was install the nvidia drivers which I did through driver manager and then I restarted. I was greeted with the low graphics/ x server could not start screen. So far I have tried installing the drivers from source from the nvidia website, installing from their package and using driver manager and I did cleanly uninstall each one after I tried it. Each was version 265.35. My kernel is 2.6.32-22. So far no luck and I have searched and tried several things I found in google. Any help would be much appreciated and yes I am decently comfortable with a terminal.

---

### Post by overdrank on 2010-07-20
Hi and what is the model of the nvidia graphics card? Did you receive any errors when installing the drivers manually?

---

### Post by thenellt on 2010-07-20
Oh, sorry for not stating, I have a gtx 260 core 216, and no I didn't receive any errors during any of the installations. I also have installed the correct kernel headers by hand but that didn't help.

---

### Post by fillintheblanks on 2010-07-20
The 256.35 driver has given me problems with the screen blanking out on startup. I am currently testing 190.53, so far its ok

---

### Post by thenellt on 2010-07-20
Yeah the 190 series has worked for me in the past, but I was just hoping to use the 256 series as I have a newer card and so there are a fair amount of improvements that affect it. Then again I think I will temporarily go to the 190s so the install is usable until I can find a fix.

---

### Post by thenellt on 2010-07-22
So has anyone gotten any geforce 200 card working with the 256.35 drivers under 10.04?

---

### Post by krazarpwnu on 2010-08-26
Hi,  I have a 260m gtx and I'm using 256.35 drivers  on lucid x64. I've installed the driver with a .run from nvidia site without any problem.

However, i have sometimes  problems while i watch flash video  ( black screen...x server crash and restart).

I thougt it was the flash plugin but I'm not sure now. Maybe a problem with hardware acceleration.

Do you know this problem?

For your problem,I don't remember any trouble with previous driver 177 I think. I don't have try 190

---

### Post by ellgor on 2010-08-26
Hi,

Read somewhere that the Nvidia drivers don't get installed correctly, so I found this guide that simply works:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor

---

### Post by M4he on 2010-08-26
Also please make sure you have build-essential and the corresponding linux-headers installed before trying to install the nvidia driver. Simply type
```
apt-get install build-essential linux-headers-`uname -r`
```into the terminal to install them

---

