---
title: "Xubuntu 12.04 battery issues"
date: 2012-05-07
forum: General Help
---

### Post by crashfatal on 2012-05-07
I am using Sony Vaio VPCCW23EN with 3 gigs of Ram, and running Nvidia 310m without optimus. I had just installed Xubuntu 12.04 LTS considering the fact that it does not take too much of processor and battery backup is good. But after using it the battery backup is not great in fact its less than usual.. I have installed jupiter and also enabled ASPM, but still no use. can anyone plz help me.?? Is der anyway to increase the battery backup.??

---

### Post by timzak on 2012-05-07
Try recalibrating your laptop battery:
[http://www.laptopbattery4.co.uk/blog/calibrate-laptop-battery/](http://www.laptopbattery4.co.uk/blog/calibrate-laptop-battery/)
This article gives Windows-specific instructions, but the basic principle applies...
-disable all power management (ie, suspend, hibernate, etc)
-fully charge battery
-unplug a/c and let battery drain til computer shuts down (don't run apps or you may have data loss when laptop shuts down)
-plug a/c back in and let computer fully charge
-battery should now be calibrated.

I don't have nvidia on my laptop, but it could be that the nvidia drivers aren't as fully optimized as their Windows counterparts to conserve battery.  Try going into nvidia-settings and seeing if there are settings you can adjust to optimize battery life.
`
I can tell you that on my laptop with Intel video, the computer runs cooler (fan hardly ever kicks up to high speed) than it did under Gnome (Ubuntu 10.04) or in Windows 7.  I've not measured battery life, but my guess is it is improved as well.  Part of the difficulty is the Xubuntu battery indicator is not as featured as Windows 7 or Gnome, so there's no built-in way to measure and compare battery life.

edit: also, per the previous person's reply, try installing powertop from the repositories:
sudo apt-get install powertop 
and run it from the command line:
sudo powertop
Gives some useful info when you let it run awhile with the laptop running on battery.

---

### Post by crashfatal on 2012-05-08
I tried removing the proprietary drivers of Nvidia and using the integrated Intel drivers but it seems that laptop gets much hotter than earlier.. I have installed Psensor and it shows the GPU getting heated than usual, so I installed the proprietary driver again. My battery backup on windows is around 2.30-3.00 hrs on a full charge.. but I don't even get 2.30 hrs of backup on Xubuntu. So  is there any other alternative for it.???

---

### Post by Toz on 2012-05-08
You need to look at a solution for your optimus graphics setup using bumblebee. Here is a link that might help you get started: [http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04]("http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04").

---

### Post by crashfatal on 2012-05-08
@Toz but my nvidia 310m doesn't supports OPTIMUS....

---

### Post by Toz on 2012-05-08
Do you have an option in your BIOS to use only the nvidia chip or to disable it completely?

---

### Post by crashfatal on 2012-05-08
I don't have any option in that... And right now am installing bumblebee that u provided the link... should I install it or no.??

---

### Post by crashfatal on 2012-05-08
so what should I do nw.???

---

### Post by Toz on 2012-05-08
If you don't have optimus then bumblebee won't work for you. I'm sorry, but I don't have any more suggestions. Maybe someone else can offer a suggestion.

---

### Post by timzak on 2012-05-08
I recall Phoronix testing battery life and finding that it is a bit shorter in Linux than Win7.  Search [www.phoronix.com](www.phoronix.com) for more info.  Have you tried the nouveau driver?

---

### Post by crashfatal on 2012-05-09
No I didnt try the nouveau driver... But are there any chances that using open source driver rather than proprietary can help saving battery.??

---

### Post by timzak on 2012-05-09
> **crashfatal said:**
> No I didnt try the nouveau driver... But are there any chances that using open source driver rather than proprietary can help saving battery.??

From Phoronix on April 21, 2012:


> Throughout all of the tests, on average the Intel Core i7 + NVIDIA Quadro FX 880M notebook was consuming 13% more power when on the NVIDIA 295.40 binary driver over the Nouveau Git code, but this driver's OpenGL performance was also multiple times faster

[http://www.phoronix.com/scan.php?page=article&item=nouveau_libdrm_rewrite&num=6](http://www.phoronix.com/scan.php?page=article&item=nouveau_libdrm_rewrite&num=6)

---

### Post by scottbomb on 2012-05-09
It seems that the power regression issue with 11.10, which was supposed to be fixed in 12.04, has actually gotten worse in my situation. Using Thinkpad T60, powertop reports a discharge rate of about 12 watts while idling. It did this last night for about 2.5 hrs before until the battery was almost dead. In 11.10, powertop would report battery drain at around 8 watts while idling, sometimes even lower. But last night, while doing my test, it never dipped below 10 watts, even with the wi-fi shut off and screen backlight on a low (but readable) setting. I was also running it in TTY1. I had firefox going in TTY7 with facebook up so it would query the server now and then. I shut that down about half-way through but it had no effect on battery drain. Turning off wi-fi (while leaving the wired NIC plugged in) saved 1 watt.

---

### Post by crashfatal on 2012-05-09
So how to use nouveau driver for nvidia 310m cuda.. I tried installing it following the steps from nouveau site, but the xorg.conf file in /etc/X11/xorg.conf is removed when I deactivate the proprietary even though I had installed xorg.xserver PPA... any help.??

---

### Post by crashfatal on 2012-05-12
Will anyone reply me how to install nouveau driver for nvidia 310m cuda.????

---

