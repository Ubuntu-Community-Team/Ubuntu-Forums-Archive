---
title: "monitor goes out of sync when login screen appears"
date: 2006-04-14
forum: General Help
---

### Post by ayyjayy on 2006-04-14
I am having a problem with my new install of Ubuntu 5.10.  The inital spalsh screen shows everything fine, but when the login screen appears the monitor shows an out of sync message (I know the login screen is there because I can here the noise it makes, and I can type in my username and password and hear it play the login music).  I have a P4 2.8 Northwood, 1GB RAM, ASUS P4P8XSE mobo, GeForce FX5600XT with 256MB RAM (VGA, S-Video, and DVI outputs), and a Viewsonic VX2000 20.3 inch LCD monitor.  It is a dualboot system with XP Home SP2.  I am not a total noob when it comes to this stuff (I have another Ubuntu 5.10 machine running a webserver with php myadmin and mySql) but I don't know what to do if I can't get into the main screen to see what I am doing.  I would appreciate any help you guys can give me...or at least point me in the right direction.

Thanks ](*,)

--edit-- I have since gone in to my xorg.conf and added the HorizSync and VertRefresh lines to the monitor section and have tried different ranges for them both, but to no avail.  I have even gone to the ViewSonic webiste and found the ranges from them and it still doesn't work.  Any suggestions will be greatly appreciated.

---

### Post by fcastillo on 2006-04-15
I'm having the same problem and don't know what to do. I enter ubuntu in the same mode to look for a video configuration file to change the video resolution. I know that if I can change this resolution the system will work, but I don't know where the file is... Please somebody help us....

---

### Post by ayyjayy on 2006-04-15
I have finally figured it out.  After hours of fooling around with it, I decided to check the refresh rate on my Windows partition.  It was 60 Hz.  So I went back into my xorg.conf file and set the range for my VertRefresh to 60.0-60.0, and it worked.  I now have a full 1600x1200 screen and everything is working fine.  If anyone else wants to know the steps I followed, here they are:

Ctrl+Alt+F1 - that will take you into a command line once you see the monitor out of range message

-type in your username and password

sudo bash

-then you have to type in your password again

cd /etc/X11
vi xorg.conf  (I know what you are thinking here.....why use vi?  It was the first text editor that i learned to use, so I guess it is nostalgia.)

-add the HorizSync and VertRefresh lines to the Monitor section
-I set the HorizSync to 30.0-82.0 and the VertRefresh to 60.0-60.0

cd /etc/init.d
./gdm restart

-and it worked after that....not sure if it will fix anyone elses problem but it might point you in the right direction.

:D

---

### Post by fcastillo on 2006-04-16
Thanks for that... I worked for me too

---

