---
title: "All attempts to install NVIDIA proprietary fail"
date: 2010-05-28
forum: General Help
---

### Post by mfseeker on 2010-05-28
The problem is that Ubuntu 10.04 as delivered is not compatible with the Nvidia driver installed with 10.04. This problem is widely reported, as is a fix for it. The usual form of the fix is as follows:

[FONT=monospace]To fix the above error message use the following procedure[/FONT]
 [FONT=monospace]1) Download Newest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")[/FONT]
 [FONT=monospace]2) Open module blacklist as admin[/FONT][INDENT]   [FONT=monospace]gksudo gedit /etc/modprobe.d/blacklist.conf[/FONT]
 [/INDENT][FONT=monospace]Add these lines and save:[/FONT][INDENT]   [FONT=monospace]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/FONT]
 [/INDENT][FONT=monospace]3) Uninstall any previously installed Nvidia drivers:[/FONT][INDENT]   [FONT=monospace]sudo apt-get --purge remove nvidia-*[/FONT]
 [/INDENT][FONT=monospace]4) Reboot your computer[/FONT]
 [FONT=monospace]5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)[/FONT]
 [FONT=monospace]6) Login and cd to the directory where you saved your file[/FONT]
 [FONT=monospace]7)Install drivers[/FONT][INDENT]   [FONT=monospace]sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run[/FONT]
 [/INDENT][FONT=monospace]8] Start GDM[/FONT][INDENT]   [FONT=monospace]sudo service gdm start[/FONT]   

 [/INDENT]This does not work for me because when I restart at (5) I do not get any message, only a blank screen. In order to get a usable system, I need to remove noveau from the blacklist.

 I believe that blacklist.conf contains a list of various video drivers that are to be excluded from consideration when the system attempts to find a driver at startup.

 When I exclude all of the drivers in the fix list, I get a blank screen at startup.

 If I do not exclude nouveau, I get a usable system with full resolution, but the system has some problems drawing screens when I switch programs. I read somewhere that nouveau is good, but not yet up to the full performance of the nvidia proprietary driver.

 When I startup without nouveau, I do not get the message that Ubuntu cannot load Nvidia drivers. I assume that that means that in some config file consulted at startup there is supposed to be a reference to Nvidia drivers that is missing from my system, that my system doesn't know enough to look for Nvidia drivers.

 If I follow the recipe above with the nouveau driver not blacklisted and then try to go through steps (6), (7) & [8], I don't get the error message at (5). I have opened a terminal, issued sudo service gdm stop, and then done (6) and (7). When I get to the sh install of Nvidia, it begins to install but then fails because it says it can't run when another driver, presumably nouveau, is present.

 So, I edit the blacklist.conf file to remove the nouveau driver. Then I try to do the Nvidia driver install. It fails in the same way. So I conclude that in order for the install to recognize that nouveau is gone, I must restart. But with nouveau gone, my restart fails with a blank screen, so I have no means of doing the driver install.

 In fact, for a long time I was really screwed because in that state I didn't have a way of getting control of my system. Fortunately, there is a Ubuntu 10.04 alternate install CD that lets me boot to a primitive console from which I can edit blacklist.conf to recognize the nouveau driver and regain control. But that puts me back where I started without the capability of installing the Nvidia driver. How do I break out of the catch 22?

---

### Post by dabl on 2010-05-28
Without knowing your GPU or system, I would guess that you only need to use a "framebuffer" or boot option, when you reboot with the nouveau driver blacklisted. If you can hit "e" on the Grub menu, and then add "vga=xxx", where "xxx" is the appropriate framebuffer value, then it should let you have a vesa display until you install the Nvidia driver.  Commonly used values for "xxx" are 785, 788, and 791.  In some cases, "xforcevesa" works, rather than "vga=xxx".

---

