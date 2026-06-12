---
title: "Fglrx Drivers"
date: 2005-03-16
forum: General Help
---

### Post by motuvaa on 2005-03-16
I finally get them work but when I run glxgears I get only 1800FPS Per 5Seconds.. 
It's really weird because SuSe gives me fps from 2500 to 5000  :oops:

---

### Post by HeavyAl on 2005-03-16
Ok, what video  card, and how did you get them working?

---

### Post by motuvaa on 2005-03-16
I have Ati Radeon 9600xt and I install xorg-fglrx-driver with apt.. just like in howto.
Then I run fglrxconfig and append "UseInternalAGPGART" "no" to the xorg.conf file.
When I type fglrxinfo it says:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

---

### Post by jmajor on 2005-03-16
Me too I finaly get it to works. Except in a very strange way. I have tried for weeks without any success to make fglrx work, and today my computer simply crash. I hit the reset button and bingo everything works.... :???: I was never able to get Opengl to work and now I got this:

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

glxgears:
23485 frames in 5.0 seconds = 4697.000 FPS
23396 frames in 5.0 seconds = 4679.200 FPS
23493 frames in 5.0 seconds = 4698.600 FPS
21370 frames in 5.0 seconds = 4274.000 FPS
23505 frames in 5.0 seconds = 4701.000 FPS

I am running Hoary on a Athlon 3200 with a Radeon 9600 Pro.
Does anybody have a hint on what make it finally works?

---

### Post by emperor on 2005-03-16
[QUOTE=jmajor]
glxgears:
23485 frames in 5.0 seconds = 4697.000 FPS
[/QUOTE]

Not sure how accurate glxgears is with the fglrx driver.
I also have a 9600PRO with a 2800 AthlonXP processor.

What do you get with fgl_glxgears, the fglrx 3D test program.
I get the following +/- 10 FPS:
2279 frames in 5.0 seconds = 455.800 FPS

---

### Post by motuvaa on 2005-03-17
I get only 200fps in fgl_glxgears :o

---

### Post by jmajor on 2005-03-17
This is what fgl_glxgears give me : 

2396 frames in 5.0 seconds = 479.200 FPS
2390 frames in 5.0 seconds = 478.000 FPS
2369 frames in 5.0 seconds = 473.800 FPS
2346 frames in 5.0 seconds = 469.200 FPS
2345 frames in 5.0 seconds = 469.000 FPS

This is not to bad :-) since those are the FPS I use to get with glxgears.

---

### Post by motuvaa on 2005-03-17
How did you install?
I installed this way:
sudo apt-get install xorg-fglrx-driver
sudo fglrxconfig
sudo pico /etc/xorg.conf -> append line "UseInternalAGPGART" "no" to device section
then reboot.. and fglrxinfo gives me:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

---

### Post by motuvaa on 2005-03-17
fgl_glxgears give me:

1617 frames in 5.0 seconds = 323.400 FPS
1788 frames in 5.0 seconds = 357.600 FPS
1789 frames in 5.0 seconds = 357.800 FPS
1786 frames in 5.0 seconds = 357.200 FPS
1789 frames in 5.0 seconds = 357.800 FPS
1789 frames in 5.0 seconds = 357.800 FPS
1788 frames in 5.0 seconds = 357.600 FPS
 and then: Segmentation fault  :D:D

---

### Post by jmajor on 2005-03-19
I did exactly the same install procedure and everytime it give always the same result (crappy 3d) until that crash that by miracle gave me finally full speed 3d. Every time I install a drivers I will do a printout of either xorg.conf to compare. They where all the same even the last one. So I simply do not understand why it works now and not before :-k . 

I find out a problem : It is when I want to change resolution the system give me that message : (Le serveur X ne supporte pas l'extension XRandR. Le changement de résolution à la volée n'est pas disponible. *Translated to: The X server does not support extension XRandR. Resolution change on the fly is not supported*)

Do you have any idea about this message???

---

### Post by daniels on 2005-03-19
It means exactly what it says: that you can't change resolutions on-the-fly with fglrx.  The driver doesn't support it.

---

### Post by emperor on 2005-03-19
I had this problem prior to running flgrxconfig. You should be able to change resolution on the fly IF flgrx is configured correctly.

---

### Post by daniels on 2005-03-20
I think it might work if you disable the DGA extension.  Which is no great loss.

---

### Post by motuvaa on 2005-03-20
I installed warty instead of hoary (Hoary crashed all the time)
I installed ati drivers.. I have OpenGL/3D Accerlation but fps suck (~1800FPS) and glxgears, fgl_glxgears and 3D screensavers pokes..

If I run fglrxconfig it overwrites my XF86Config-4 and then X won't work.. or if I change Indentifier to : "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)" instead of default : "Silicon Integrated Systems (SiS) SG86C202" and reboot, X stops working.
I've installed ati drivers with warty apt (fglrx-driver, fglrx-driver-dev & fglrx-control)
What could be wrong? :?:  ](*,)

---

### Post by emperor on 2005-03-20
It sounds like there is another variable, perhaps a hardware or memory problem.
Hoary should not crash all the time as you report and you should not get seg faults running fgl_glxgears.

---

