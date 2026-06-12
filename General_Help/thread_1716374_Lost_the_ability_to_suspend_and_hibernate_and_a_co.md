---
title: "Lost the ability to suspend and hibernate and a couple of questions"
date: 2011-03-28
forum: General Help
---

### Post by thegeomaster on 2011-03-28
Hello everyone,
I have recently downloaded Ubuntu 10.10 and installed it onto my laptop, alongside with pre-installed Windows XP. I'm _very_ happy with Ubuntu and find it a lot better than many other operating systems. However, I have stumbled across a problem recently: I don't seem to be able to suspend ("sleep") the laptop and neither can I hibernate it. These options worked so far and if I remember correctly, this started when I updated my kernel to 2.6.38. Since then, I've lost the options to sleep and hibernate, and when I close my laptop lid, I get a message "Unable to suspend". Does anyone else have this problem and is there a solution to it?

Also, a side question - why does video run so slowly on Ubuntu using VLC? This happens to me when watching .mkv videos. Many frames get skipped and there are visible artifacts, in fact, so much that the video can barely be watched. Actual FPS drops below 1, so one frame stays on screen several seconds. I tried tweaking the options, choosing different demuxers, codecs and graphics output. This happens only while running on batteries and works fine under Windows, I have no idea why. Under Windows the video is played using Media Player Classic and ffdshow, if it makes any difference.

Thanks in advance for your help, 
Geomaster

---

### Post by 3Miro on 2011-03-28
If the VLC problem occurs only when the cable is unplugged: When on battery power, Ubuntu will slow down the CPU in order to save energy. XP should be doing the same, but there are different ways/levels of powering down the CPU, so XP may be working fine. Check the Gnome-Power-Manager settings (System -> Admin).

I am not sure about the suspend/hibernate.

---

### Post by safarin on 2011-03-28
I already face this problem before. Hehehe..

This happen to me when I install Ubuntu using wubi.
After I installed using "live-cd" method. Problem solved. :D

---

### Post by thegeomaster on 2011-03-29
> **safarin said:**
> I already face this problem before. Hehehe..

This happen to me when I install Ubuntu using wubi.
After I installed using "live-cd" method. Problem solved. :D
I see. But suspend/hibernate have worked for me so far, so I guess it doesn't have anything to do with the installation. Also, I don't have a CD/DVD reader on my laptop, so installing from a Live CD would be impossible.

Also, I remember installing and running Intel's PowerTOP recently, does it probably have something to do with the sleep/hibernate disappearing?

3Miro, Safarin, thanks for the help so far :)

---

### Post by philinux on 2011-03-29
> **thegeomaster said:**
> Hello everyone,
I have recently downloaded Ubuntu 10.10 and installed it onto my laptop, alongside with pre-installed Windows XP. I'm _very_ happy with Ubuntu and find it a lot better than many other operating systems. However, I have stumbled across a problem recently: I don't seem to be able to suspend ("sleep") the laptop and neither can I hibernate it. These options worked so far and if I remember correctly, this started when I updated my kernel to 2.6.38. Since then, I've lost the options to sleep and hibernate, and when I close my laptop lid, I get a message "Unable to suspend". Does anyone else have this problem and is there a solution to it?

Also, a side question - why does video run so slowly on Ubuntu using VLC? This happens to me when watching .mkv videos. Many frames get skipped and there are visible artifacts, in fact, so much that the video can barely be watched. Actual FPS drops below 1, so one frame stays on screen several seconds. I tried tweaking the options, choosing different demuxers, codecs and graphics output. This happens only while running on batteries and works fine under Windows, I have no idea why. Under Windows the video is played using Media Player Classic and ffdshow, if it makes any difference.

Thanks in advance for your help, 
Geomaster

Is this a wubi install?

You can use a live usb to install.

---

### Post by safarin on 2011-03-29
My friends who install using Wubi method, all of them facing this problem. I'm not sure the hibernate/suspend problem is came from installation or not.

maybe you could check this link

[https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html]("https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html")
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

I think, maybe Wubi installation doesn't reserve the swap area (sorry cannot verify because I not install Ubuntu using Wubi).

Hahaha, my CD/DVD drive also broken. I installed Ubuntu using USB pendrive/flashdrive. Maybe you could use this method if you interested.

:P

---

### Post by philinux on 2011-03-29
From wubi FAQ.

> Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


---

