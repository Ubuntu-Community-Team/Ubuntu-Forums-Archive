---
title: "Display bug after display properties change"
date: 2009-08-07
forum: General Help
---

### Post by yodaa on 2009-08-07
Hello,

**I ] My PC configuration is :**

_Hardware :_
ASUS A8N SLI Deluxe motherboard
AMD 64 3500+ processor
NVidia Geforce 9800 GT
illyama 17" CRT screen (27 – 96 kHz Horizontal sync | 50 – 160 Hz Vertical sync)

_OS :_
Ubuntu Studio 9.04 alternate AMD64

**II ] At the first run, I decided to change the display resolution :**

I tried to change it to 1024 X 768, but after that the screen appeared totally messy : horizontal colored lines and messy pixels... 

After rebooting the system (splash screen / login screen are are ok), the desktop is still covered with the display bug mentioned earlier.

**III ] I tried to fix that with :**

**3. 1 )** I rebooted the system (force to, because I can't see the desktop, icons...) and choose the "recovery mode" of Ubuntu Studio :

*Recovery menu -> xfix : try to auto repair graphic problem*

**3. 2 )** I rebooted the system and the problem still occurs.
**3. 3 )** I rebooted the sytem and choose the "recovery mode" of Ubuntu Studio this time :

*Recovery menu -> root : drop to root shell prompt*

I tried to delete the "xorg.conf" file :

#cd /etc/X11/
#ls
#rm xorg.con*

**3.4 )** I rebooted the system and the problem still occurs.
**3.5 )** I was advised to install the nividia drivers manually in console mode (seem's like I can't access graphical mode...).

But the point is that I'm an Ubuntu beginner and after reading a bit of documentation I don't have a clear view about the process.

Does this display problem caused only by the lack of Nvidia drivers ? At first run of Ubuntu Studio the graphical desktop interface was ok (except the screen resolution)

If NVidia non OSS drivers installation is the key : of should I install them properly ?

_Latest non OSS NVidia driver (beta) :_ 
[http://www.nvidia.com/object/linux_display_amd64_190.18.html](http://www.nvidia.com/object/linux_display_amd64_190.18.html)

_Latest non OSS NVidia driver (stable) :_ 
[http://www.nvidia.com/object/linux_display_amd64_185.18.31.html](http://www.nvidia.com/object/linux_display_amd64_185.18.31.html)

Those driver are ".run" files, after reading documentation i seems that they have to be download, build, installed, configured. I tried to figure out the whole process (but I'm a bit lost at this point) :

#wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.31/NVIDIA-Linux-x86_64-185.18.31-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.31/NVIDIA-Linux-x86_64-185.18.31-pkg2.run)

*note : what's the default directory destination for this download*

# cd /myDownloadDirectory
# chmod -x NVIDIA-Linux-x86_64-185.18.31-pkg2.run
# NVIDIA-Linux-x86_64-185.18.31-pkg2.run

[I]At this point I need to process to the installation but how ?

Seems like kernel headers, and build-essential packages are needed... how can I check if there are also installed ?[/I] 

Help would be appreciated

---

### Post by yodaa on 2009-09-06
Issue solved : I' ve finally installed precompiled NVIDIA drivers using :
```
# sudo apt-get install nvidia-glx-180
```
nvidia-settings utility came with that package. After reboot Display was ok and 
I was able to configure my display settings.

---

### Post by CatKiller on 2009-09-06
> **yodaa said:**
> 
After rebooting the system (splash screen / login screen are are ok), the desktop is still covered with the display bug mentioned earlier.

I'm glad you got it fixed in the end, but per-user resolution settings are stored in ~/.config/monitors.xml. Deleting or renaming this file would have set your resolution back to the default that's used for the GDM login screen.

---

### Post by yodaa on 2009-09-10
Hi,

Thanks for your feedback. good tip ! I'll have a closer look to the config file (~/.config/monitors.xml.) you mentionned.

---

