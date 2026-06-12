---
title: "nVidia and Plymouth aren't working together."
date: 2010-06-03
forum: General Help
---

### Post by uRock on 2010-06-03
I just had to restart my system 4 times in a row to get it to boot in the proper graphics mode. Other than not shutting down, what should I do to prevent this? 

This has been a recurring problem for a few days now.

Do I need to uninstall the nVidia driver and install Nouveau? If so, is Nouveau automatically enabled after disabling the nVidia driver?

Thanks,
uRock

---

### Post by philinux on 2010-06-03
See the General Help forum sticky.

Also for info that you are not alone.
[http://ubuntuforums.org/showthread.php?t=1495401](http://ubuntuforums.org/showthread.php?t=1495401)

---

### Post by uRock on 2010-06-03
I made the change to the grub file, so hopefully the problem is fixed. I'll give it a few days to see if I have problems with it.

Thanx,
uRock

---

### Post by Linuxforall on 2010-06-03
I usually install my own nvidia driver via run file and that has worked out quite well for me even on Lucid, however since xswat ppa is being updated right away with latest beta, I now install via hardware drivers and stay current. When my system boots, I just see a brief blinking cursor and I am right into the desktop after that so for me Plymouth is a non issue here, even while shutting down, I briefly see the Ubuntu screen before my system shuts down.

---

### Post by uRock on 2010-06-04
Ok, the fix listed in the Sticky thread did nothing for fixing the boot-up issue.

How do I remove the nVIdia driver and run the default Nouveau driver?

---

### Post by philinux on 2010-06-04
> **uRock said:**
> Ok, the fix listed in the Sticky thread did nothing for fixing the boot-up issue.

How do I remove the nVIdia driver and run the default Nouveau driver?

System>admin>hardware driver Deactivate. Reboot

I would reverse any changes you made via the sticky first.

---

### Post by dino99 on 2010-06-04
i've removed "splash" to be able to boot with 34, 35 refuse

---

### Post by dewey_daniels on 2010-06-04
Well I was Having similar problems.
First just get "Startup Manager"
Second System-Administration-Startup-Manager.
Third Change the Display setting to the max that your computer can handle.
Fourth Change the Color Depth to 24.
Fifth Reboot


It should work if you have the same problem as me. It work for me hopefully it is the same for you

---

### Post by uRock on 2010-06-05
I tried deactivating the driver, then restarting. It restarted and had a very messed up resolution and I couldn't find an applet to change the settings.

Dino99- My problem isn't with the bootup resolution. The problem is with the bootup being interrupted, then going into low/safe graphics mode.

For now I am just going to keep booting Windows. Hopefully the devs will get this ironed out in the next kernel update.

Thanks,
uRock

---

