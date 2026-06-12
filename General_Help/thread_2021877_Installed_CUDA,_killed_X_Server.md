---
title: "Installed CUDA, killed X Server"
date: 2012-07-09
forum: General Help
---

### Post by kahgfakhjsf on 2012-07-09
[I tried installing 64 bit CUDA 4.2]("http://developer.nvidia.com/cuda-downloads") on [my laptop]("http://support.apple.com/kb/SP546") running Ubuntu 12.04. 

At step 2 I killed my X server by issuing:
> sudo service lightdm stop

Then I ran:
>  sudo ./devdriver_4.2_linux_64_295.41.run
to install the driver. 

When I tried to restart X
> sudo service lightdm start

I was given a blank command prompt. When I restarted: I was given a command prompt that I could log into, but no graphical interface. 

Assuming I don't care about installing CUDA, how could I get X running again?

---

### Post by kahgfakhjsf on 2012-07-10
I tried uninstalling the driver 
> sudo ./devdriver_4.2_linux_64_295.41.run --uninstall

Although it uninstalled, I still only have a command prompt at startup. 

Here are the last few lines of /var/log/Xorg.0.log:

> [    22.506] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.506] vesa: Ignoring device with a bound kernel driver
[    22.506] (WW) Falling back to old probe method for vesa
[    22.506] (II) UnloadModule: "vesa"
[    22.506] (II) Unloading vesa
[    22.506] (EE) Screen(s) found, but none have a usable configuration.
[    22.506] 
Fatal server error:
[    22.506] no screens found
[    22.506] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    22.506] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    22.506] 
[    22.513]  ddxSigGiveUp: Closing log
[    22.513] Server terminated with error (1). Closing log file.

---

### Post by kahgfakhjsf on 2012-07-11
Someone suggested to me that my drivers were conflicting. So I did an lsmod to see what kernel modules I had on, one called _nvidia_ was one of them, I removed it, then tried to start x. 

> modprobe -r nvidia
sudo service lightdm start

My computer switched into tty7 and started the GUI. Although it didn't let me into my account, I was able to apply my graphics drivers with the additional drivers interface in system settings. 

When I rebooted, I was able to boot strait into a GUI (with some flashes on the screen). Unfortunately when I try to login as me, the screen flashes a lot and puts me back to the login screen, I can login as a guest though.

---

