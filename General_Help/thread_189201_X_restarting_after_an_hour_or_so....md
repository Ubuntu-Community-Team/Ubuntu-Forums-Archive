---
title: "X restarting after an hour or so..."
date: 2006-06-04
forum: General Help
---

### Post by Gomek on 2006-06-04
So I've done a server install and then installed fluxbox, Xgl, gdm, and xscreensaver.  At least, those are the ones I think are important for you to know.

I don't have any gl screensavers activated or even installed, so I can't figure this out.  I let my screensaver activate, and after an hour or so of sitting there, my X session reboots and sits there on the gdm login screen.

X doesn't seem to crash like this when I'm using it...only after it sits at the screensaver.  It kind of makes me think there's a power management setting somewhere that I can't find.  gnome-power-manager is installed, and the sleep options I have changed to "never", so I don't think it's that...  In xscreensaver-demo, I've changed it to never lock the screen, and the sleep/suspend/off options on there don't even seem to work, so I don't think it's that, either.

Needless to say, I'm at a loss, here.  I really don't want to be dumped back into the login screen after a certain amount of time.

Is there some type of setting I'm missing, or is Xgl just crashing from a screensaver?

---

### Post by mattkenn4545 on 2006-06-05
Are you using the dock or miniwin plugins with compiz?

If so disable and I bet the issue will be resolved.

From what I have read this is due to those plugins losing track of windows (screensaver counts as one) which eventually causes a crash of the xserver.

Also post your logs and any messages you recieved.

---

### Post by Gomek on 2006-06-05
Not using compiz.  Compiz is a window manager and would take the place of fluxbox.  I'm using fluxbox and xcompmgr with transset.

---

### Post by Ramses de Norre on 2006-06-05
Did you check ~/.xsession-errors /var/log/Xorg.0.log and /var/log/Xorg.0.log.old for error messages after a crash?

---

### Post by Gomek on 2006-06-05
Yeah, this particular problem isn't reporting anything in those files.  Also, the time it takes isn't very consistent.  It just did it twice, and it only took like 5-10 minutes.

---

### Post by mattkenn4545 on 2006-06-05
if you are not using compiz why are you using xgl. 

Maybe I'm just confused.

---

### Post by cleentrax on 2006-06-05
This can be a hardware issue: A bad/poorly-seated stick of RAM, or insufficient cooling are two causes of reboots that I have dealt with. Both of these can occur after a period of time, as you mentioned.

---

### Post by Gomek on 2006-06-05
> if you are not using compiz why are you using xgl.
From [http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/) --
> Xgl is the X server architecture layered on top of OpenGL and takes advantage of available accelerated 3D rendering hardware. It is designed to integrate well with the composite extension and performs best when a compositing manager is running.
Basically I'm just experimenting.  xcompmgr is a compositing manager.  Who says I can't try to take my favorite window manager and use Xgl to try to make it look prettier?  =P



> This can be a hardware issue: A bad/poorly-seated stick of RAM, or insufficient cooling are two causes of reboots that I have dealt with. Both of these can occur after a period of time, as you mentioned.
Runs fine when I'm using it and when it's in Winblows.  I think it's just unstable.  Perhaps XGL just doesn't work right with some of the stuff I'm running.

---

### Post by minisori on 2006-06-06
I have the same issue since I activated the gnome-screensaver or the power save for the monitor. When i left the comp aloone a couple of hours (maybe less) I always find it in gdm, and its prety anoying when you are working and you have hundreds of windows open, cause u have to start over again....

---

### Post by dbw on 2006-06-09
I have the same problem -> random restarts to gdm.  I am running the Badger with fluxbox, and have found that the problem occurs every time that xscreensaver tries to run the open-gl screensavers.  However, running xscreensaver demo also crashes to gdm.  I have tried commenting out the open-gl screensavers in my profile, but this doesn't seem to be complete for some reason.  Additionally, I did used to be able to run all screensavers ( for like 8 months) and then it randomly crapped out on me.  I have tried reinstalling xscreensaver, including erasing my profile file.  I think that my next step will be reinstallation of the open-gl crap.  gotta check on how that fits in w/ my nvdiea-drivers first.  

if anyone has any ideas, i do have a custom kernel, w/ nvidea compiled in, which has been running for 5 months.
 -peace

---

