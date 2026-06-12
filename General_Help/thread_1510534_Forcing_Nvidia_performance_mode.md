---
title: "Forcing Nvidia performance mode"
date: 2010-06-15
forum: General Help
---

### Post by utheer on 2010-06-15
I currently am switching from windows to ubuntu. In windows I was using rivatuner to force a constant 3d performance mode setting on my graphics card. I was wondering if there is any way to do this on a linux based system?

---

### Post by dabl on 2010-06-15
When you install the proprietary driver, and use the nvidia-xconfig utility to write a suitable /etc/X11/xorg.conf file, it will take advantage of the capabilities of your card to enable the 3D performance, when called upon by an application or the OS.

Also, in the nvidia-settings utility, if your GPU has "power management" capabilities, you can choose a profile that suits your needs -- including overclocking the GPU and graphics memory when in 3D mode.

---

### Post by utheer on 2010-06-15
The problem is my graphics card has a glitch where if it goes into 2d mode for whatever reason my screen goes black. Rivatuner has an option which basically forces it to never allow applications to use 2d mode.

---

### Post by dabl on 2010-06-15
That glitch may or may not happen in Linux -- you'll have to try it to find out (a booted Live CD should be sufficient - no need to install anything).

In general, Linux tends to use more "smarts" in controlling the use of your computer resources, including GPU, to optimize the performance of the system as a whole.  The downside of that is that you (the user) tend to have fewer levers to control it at such a fine level, as you might be accustomed to in Windows.

---

### Post by pirateofms on 2010-07-10
look in nvidia-settings --help (it's a lot of reading) and there may be a setting to do this.  There's a ton of settings in there you can use, including setting PowerMizer to Performance (or Adaptive).  Useful for boot scripts.

---

### Post by cokicd on 2010-07-11
> **utheer said:**
> I currently am switching from windows to ubuntu. In windows I was using rivatuner to force a constant 3d performance mode setting on my graphics card. I was wondering if there is any way to do this on a linux based system?

Try this if you want to force the max. performance mode:
[http://www.youtube.com/watch?v=_NSJx3G9-zc](http://www.youtube.com/watch?v=_NSJx3G9-zc)

---

