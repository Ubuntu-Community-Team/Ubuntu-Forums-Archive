---
title: "NVIDIA Graphics Ubuntu 10.04 Help"
date: 2010-10-08
forum: General Help
---

### Post by rosshuts on 2010-10-08
Hi There,

I am an Ubuntu newbie and loving the OS so far. Also apologies if this thread is not in the correct place either!

I have installed it onto my custom made media centre connecting to my Sony 1080p HDTV via HDMI.

Its been up and running for a couple of weeks or close to a month and its been totally perfect. 

All of a sudden I have an error message appearing on startup. The following error message is as follows:-

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Oct 08 18:04:30 NVIDIA(0): Failed to initialize the NVIDIA Kernel. Please see the 
systems kernel log for additional error messages and consult the nvidia readme for details.

Screens found but non have a usuable configuration.

I am not sure why its started all of a sudden. I am using the hardware recommended drivers by Ubuntu for my NVIDIA onboard 9300 card (its built in to my zotac mobo) and the configuration hasn't changed at all since setting them up.

Not quite sure what other details to give at this stage, but if you need any more info like logs etc then I can upload them if you can tell me where to get the from.

As stated, I am a total newbie, but loving it so far and so pleased to get away from Windows as I feel Ubuntu makes for the perfect XBMC home media centre.

Thanks,
Ross.

---

### Post by 3Miro on 2010-10-08
My bet is the nvidia driver. The driver is closed source and proprietary and is not part of the Linux kernel. Which means that every time you update the kernel, you have to update the driver so that it recognizes and works with the kernel.

The easiest way to fix that is to reisntall the driver. Go to System -> Admin -> Hardware Drivers, uninstall the driver, reboot and then install it again. this should fix the problem.

---

### Post by Cavsfan on 2010-10-08
I can provide you with a link to obtain the latest driver from nVidia, a link detailing how to install it and another 
with a howto add a script that automattically updates the kernel with the driver whenever it is updated or a new 
kernel is added. If you are interested.
I have a nVidea Geforce 9800 GT 512Mb and the latest drivers rock!

---

### Post by 3Miro on 2010-10-08
> **Cavsfan said:**
> I can provide you with a link to obtain the latest driver from nVidia, a link detailing how to install it and another 
with a howto add a script that automattically updates the kernel with the driver whenever it is updated or a new 
kernel is added. If you are interested.
I have a nVidea Geforce 9800 GT 512Mb and the latest drivers rock!

This is exactly what the Hardware Manager in Ubuntu does, it just fails to do it sometimes. Installing the "latest" driver is a hassle, it is not considered stable with respect to Ubuntu and it will be hard to get support if something goes wrong.

---

### Post by Cavsfan on 2010-10-08
This is the driver download page, just pick your card and download:
[[COLOR=blue]_pick the one that matches your card._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

This is how to install the driver:
[[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

Step 4 I had to write down as you have to reboot and do some special stuff.** You will need this after rebooting**

How to create the script:
[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

Edit: Just change the driver file name to the file name that you download from nVidea.

I was able to do this no problem. And I have gone through several kernel updates and installs.

---

### Post by Cavsfan on 2010-10-08
> **3Miro said:**
> This is exactly what the Hardware Manager in Ubuntu does, it just fails to do it sometimes. Installing the "latest" driver is a hassle, it is not considered stable with respect to Ubuntu and it will be hard to get support if something goes wrong.

They are stable now. Many people are using the latest such as I. I have version [COLOR=Red]256.53[/COLOR] and it works a lot 
better than the ones that were on Hardware Manager. Perhaps you should give it a try if you have an nVidia card. :P

---

### Post by rosshuts on 2010-10-09
Hi Guys,

Thanks for the all the replies and sorry for the delay.

I will those links you suggested and download the latest drivers etc.

Sadly the wife is hogging my TV with that show called X-Factor.

I just assumed I should choose the drivers that are listed in the hardware drivers as it was recommended by Ubuntu rather than downloading and installing them manually.

Anyway, I will give them ago and let you know how it goes.

Cheers,
Ross.

---

### Post by SeijiSensei on 2010-10-09
> **rosshuts said:**
> I just assumed I should choose the drivers that are listed in the hardware drivers as it was recommended by Ubuntu rather than downloading and installing them manually.

I've always used the Hardware Drivers application to install the NVIDIA drivers, and it's worked flawlessly so far.  I really can't see any reason to get the driver from NVIDIA's site unless there's some bleeding-edge item that you absolutely must have.  I've been watching HD videos with a 9500GT and the drivers installed by using the Hardware Drivers application for a couple of years now.

Works great with up-to-date [versions]("https://launchpad.net/~rvm/+archive/ppa") of smplayer and mplayer with VDPAU support.

---

### Post by Cavsfan on 2010-10-09
> **SeijiSensei said:**
> I've always used the Hardware Drivers application to install the NVIDIA drivers, and it's worked flawlessly so far.  I really can't see any reason to get the driver from NVIDIA's site unless there's some bleeding-edge item that you absolutely must have.  I've been watching HD videos with a 9500GT and the drivers installed by using the Hardware Drivers application for a couple of years now.

Works great with up-to-date [versions]("https://launchpad.net/%7Ervm/+archive/ppa") of smplayer and mplayer with VDPAU support.

I have also just used the one from Hardware Drivers - version 185 for opengl, until I found out that I didn't have to.
Then I was told that I would have to re-install the driver every time a new kernel was updated or added and 
was shown the script to do that automatically. So the question is do you want to stick with version 185 or the 
latest version 256.53? It was a no brainer for me. The video, as one would hope, is greatly enhanced vs the 185 driver.
Ubuntu has come a long way in being able to handle the latest nVidea drivers. I have a Geforce 9800 GT 512MB and it is 
smokingly better than the 185 driver was. You just have to take the extra steps I mentioned above. I figure anyone 
can do it. If you running an old pentium 4 with a very old nVidea card, maybe you might stick with the default driver, but if 
you have a decent system with a fairly new nVidea card, go for it I say!

BTW, I am on Maverick and the drivers are now in **System** > **Administration** > **Additional Drivers** now.

---

### Post by 3togo on 2010-10-11
If u want VDPAU support, u shouldn't use NVIDIA 256. It is not working rite now.

---

