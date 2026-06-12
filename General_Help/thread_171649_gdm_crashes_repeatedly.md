---
title: "gdm crashes repeatedly"
date: 2006-05-07
forum: General Help
---

### Post by Face1 on 2006-05-07
Since sometime yesterday, gdm has been periodically (as in every 10 minutes or so) crashing, causing my session to be repeatedly restarted, as I have it automatically log me in.  I looked in /var/log/daemon.log (this might not be the most correct place to look, but it helped anyway), and I got this line tons of times:
> May  6 08:24:39 localhost gdm[15824]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May  6 08:30:51 localhost gdm[15967]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May  6 08:37:04 localhost gdm[16110]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May  6 08:43:17 localhost gdm[16253]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May  6 08:49:30 localhost gdm[16404]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May  6 08:55:43 localhost gdm[16547]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Something is clearly wrong with gdm or X11, so I looked in /var/log/Xorg.0.log and the only error I got is this:
> (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

So this seems to be the problem...every time I try to use any kind of opengl graphics, gdm crashes--it has been doing it periodically because of my screensaver!  

So the problem has been diagnosed, but what should I do?  Opengl features were working perfectly the other day, so I think that maybe all those X11 upgrades that were available that I installed (Which I figure were related to that security hole they found) screwed it up.  I figure my best bet is to reinstall the drivers (which I'll do tomorrow morning unless anyone has a better idea).  

Anyone else have this problem after the upgrade?

---

### Post by Face1 on 2006-05-07
Oh yeah, in the meantime, how can I disable my screensaver without opening up control center (I use KDE---maybe this should be in the kubuntu forum, but the rest of the thread is here, and the problem exists with both, so it's fine, I suppose)?  I can't open up control center because the little screensaver preview uses opengl and crashes gdm still.

---

### Post by Ramses de Norre on 2006-05-07
Many people had this issue, you'll need to reinstall the video drivers to get opengl working again.

---

### Post by JoeMetal on 2006-05-07
I've dist-upgraded to Dapper on three different machines and on all of them, before I do anything, I have to ```
sudo apt-get install nvidia-glx
```
It is rather annoying.

---

### Post by Face1 on 2006-05-07
Okay great, got it working, thanks a lot.

However, I had to use [this howto]("http://ubuntuforums.org/showthread.php?t=75074"), as I have had to do in the past as well to get things working.  Running that apt-get command doesn't help me--if anything it screws things up more.  Additionally, after installing the driver and editing the xorg.conf file, I couldn't run > /etc/init.d gdm start
I get a [FAIL] message when I do.  Anyway, startx doesn't help things from there (weird results), and I had to restart the computer to get things working, which I thought was very strange.  

But...it's working, so I'm happy.

---

