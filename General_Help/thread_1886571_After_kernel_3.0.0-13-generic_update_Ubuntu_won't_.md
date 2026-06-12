---
title: "After kernel 3.0.0-13-generic update Ubuntu won't boot"
date: 2011-11-25
forum: General Help
---

### Post by thom# on 2011-11-25
I recently installed the updates on Ubuntu and upon restarting my computer, it won't boot up. When the purple screen is reached the following text is displayed:

> 
[B]loading Linux 3.0.0-13-generic
loading initial ramdisk[/B]


A few more processes seem to run and I'm left in the terminal (I can copy the output if required.)

I'm quite new to ubuntu, so please excuse my lack of knowledge. I'm just  taking a wild guess - but is this something to do with the Linux  headers that were installed?
  
Below is the output of the kernel update, from *'cat /var/log/dpkg.log | egrep 'install |upgrade '*

>  	 	 		 			 				[B]2011-11-23 19:57:07 install linux-headers-3.0.0-13 <none> 3.0.0-13.22
2011-11-23 20:08:13 install linux-headers-3.0.0-13-generic <none> 3.0.0-13.22
[/B]

Any help would be appreciated. :confused:

At the moment I'm starting Ubuntu, by holding shift to access the GRUB menu, then selecting the older kernel 3.0.0-12-generic.

Is it possible to roll-back the kernel upgrade? Is this advisable? :confused:

---

### Post by bluexrider on 2011-11-25
Unless you removed the original kernel you should be able to boot into the old one.

Then in terminal 
[FONT=arial][B]sudo dpkg --get-selections | grep linux-image

to see what IS installed
[/B][/FONT]

---

### Post by thom# on 2011-11-25
Yes, I am able to boot the original kernel from the GRUB menu.

The output of *'[FONT=arial]sudo dpkg --get-selections | grep linux-image'[/FONT]* is below:

> linux-image-2.6.38-10-generic            install
linux-image-2.6.38-11-generic            install
linux-image-2.6.38-8-generic            install
linux-image-3.0.0-12-generic            install
linux-image-3.0.0-13-generic            install
linux-image-generic                install


However, I'm not sure what to do as the default selection is this new kernel.. 3.0.0-13-generic.

---

### Post by bluexrider on 2011-11-25
To remove the kernel
[FONT=arial][B]sudo apt-get purge linux-image-3.0.0-13-generic

reboot
[/B][/FONT]

---

### Post by matt_symes on 2011-11-25
. Wrong thread

---

### Post by KoljaX on 2011-11-29
I am having the similar problem, although i cannot get to see the "purple screen". The start up is getting locked while I still see a strange image, probably before the video driver is started. I successfully booted up in recovery mode, so I suppose the issue is some previous software i already had (possibly the nvidia proprietary driver). The old kernel is working fine.

Thanks in advance for the help.

---

### Post by bach on 2011-12-02
I am having serious problems with suspend-and-resume after I upgraded to kernel 3.0.0-13. I am running Ubuntu 11.10 64 bit. Hardware is DELL Latitude E6510 (Intel GPU).

---

### Post by BC59 on 2011-12-02
> **bach said:**
> I am having serious problems with suspend-and-resume after I upgraded to kernel 3.0.0-13. I am running Ubuntu 11.10 64 bit. Hardware is DELL Latitude E6510 (Intel GPU).

Well there is a simple solution.

Boot and from the boot screen (if you cannot see it hold SHIFT down) choose to boot with the old kernel 3.0.0-12.

When everything is OK, install from the Ubuntu Software Center the application StartUp Manager. Then open it and choose to boot by default with the old kernel. Close it and that's it.

---

