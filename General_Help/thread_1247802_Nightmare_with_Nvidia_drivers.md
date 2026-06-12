---
title: "Nightmare with Nvidia drivers"
date: 2009-08-23
forum: General Help
---

### Post by madu on 2009-08-23
Hello,

I have tried everything I could and am just too tired of restarting and restarting and restarting.

I have a 9.04 32-bit with a Nvidia GTX 260 card and all was working really well with Compiz and all.

I was studying for LPI Linux exam and was reading about kernel modules. I wanted to find out, for no particular reason, what modules depend on the nvidia module. So I ran something like depmod nvidia...
Because I never thought it would do anything. Anyway I had restart and it started in low-graphics mode.

I have tried many things up to now, and I have been able to get things working except for Compiz.

What I did:
1) sudo nvidia-xconfig - Error saying "You do not appear to be using Nvidia X driver. Do nvidia-xcongif"

2) sudo nvidia-xconfig - It writes in new xorg file and when I restart, it's in low-graphics mode.

3) Stopped GDM and installed a NVIDIA 180 driver. First gave me an error saying it cannot compile because the GCC version are different. But compiling with -k $(uname -r) seemed to fix that.

4) Still I was starting in low graphics mode. 

5) Enabled the restricted hardware drivers for Nvidia 3D acceleration. Sometime worked, sometimes did not.

6) FINALLY: I did "sudo dpkg-reconfigure xserver-xorg" and it seemed to fix things. I started with correct resolution. 
BUT, I couldn't start nvidia-settings. It still gave me the not using Nvidia X driver error.  I went and enabled the restricted hardware. It activated and asked me to restart. I thought my misery was over. Restarted back in the low-graphics mode. Nvidia-settings still gave me same problem.

I did step 6) again. Now the restricted hardware driver is activated, but Nvidia-settings still gives me the same error. And I cannot enable EXTRA mode in APPEARANCE. It says "Desktop effects cannot be enabled".


Anybody, please, give some way get out of this. I am addicted to Compiz it is very difficult to function without it.

Thank you.

---

### Post by Sam Lars on 2009-08-25
I recommend installing envy-ng and running
```
sudo envy-ng -t
```

---

### Post by madu on 2009-08-25
Thanks Sam.
But still doesn't help. It still starts in low-graphics with the error that cannot initialize the Nvidia kernel module.

Cheers.

---

### Post by Sam Lars on 2009-08-26
Try a
```
sudo aptitude reinstall
```
for whichever package provides your Nvidia driver.
If that doesn't work, try going to Nvidia and installing their latest driver from their site.

---

