---
title: "Uninstalling nVidia Drivers Fully"
date: 2011-03-22
forum: General Help
---

### Post by 3246251196 on 2011-03-22
I need to install nVidia drivers from the official site. The driver I installed via the Additional Drivers does not seem to be enabling Anarchy Online to run as smoothly as it should; I need more FPS and should be getting more FPS anyway.

Basically, is it enough to Remove the drivers from the Additional Drivers window or is there a more essential way it must be done?

---

### Post by Dlambert on 2011-03-22
In my experience, if you shut down gdm and try to install the latest Nvidia drivers manually, it automatically deletes the old one, then you have to repeat the process to reinstall it.

First download latest driver from Nvidia for your card, the place it on the desktop, and make it executable. (Right Click, Properties, allow booting as a program)

Then, ```
/etc/init.d/gdm stop

```Then u will need to login again

Then ```
Sudo ./N
``` Then hit TAB and the full title will appear, and hit enter and follow the directions

---

### Post by 3246251196 on 2011-03-22
Thanks.
Now, after installing the drivers I get to the UBUNTU screen (with the 5 dots underneath the logo) and it simply hangs.

Does not do anything. I can boot into Recovery.

I have no idea why it is now hanging...

Normally it would show this screen for a second and then I would proceed to log in.

---

### Post by 3246251196 on 2011-03-22
Okay, that problem was sorted out. During installation of the nVidia drivers through RECOVERY, I was asked if I wanted to have a file installed that would disable Nouveau kernel. I installed this file. But then deleted it after the nVidia drivers were installed. When I was restarting I think it was loading up Nouveau because I removed this file. So, I installed the file again and this time I restart and I am here now, writing this - fine.

1) How to prove that I have indeed successfully installed the most recent nVidia drivers?
2) How to prove that I am using the nVidia kernel instead of Nouveau?

Edit: I did realise that in Sys>Pref> I have a new option nVidia X Server Settings (but i cannot remember if that was there before!!)

---

### Post by lithopsian on 2011-03-22
Look in your /var/log/Xorg.0.log file and it will tell you the driver versions that are loaded.  Make sure they are nVidia and not nouveau.  Also look in glxinfo and make sure it shows your nVidia and not Mesa/Nouveau.

---

### Post by 3246251196 on 2011-03-22
**GLXINFO**
===
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
===
[B]Xorg.0.log
[/B]===
[    20.252] (II) LoadModule: "nvidia"
[    20.252] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    20.276] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.280]     compiled for 4.0.2, module version = 1.0.0
[    20.280]     Module class: X.Org Video Driver
[    20.296] (II) NVIDIA dlloader X Driver  260.19.44  Sun Feb 27 21:31:52 PST 2011
[    20.296] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.296] (++) using VT number 7
===

Would those be what I should be looking for?

---

### Post by 3246251196 on 2011-03-23
Anyone?

I have had a day to test and I am honestly not convinced that I getting a  better performance from either Anarchy Online or Guild Wars when  compared to Windows 7.

People may reply saying - how do you expect a game to run better when it  has to go through emulation, but I have noticed many people say that  performance on WINE is as good, if not better.

There is nothing I hate more than having a bottlenecked system which is not providing its potential!

---

### Post by pqwoerituytrueiwoq on 2011-03-23
```
cat /etc/modprobe.d/blacklist.conf | grep nouveau
```if you get output from that command you need to edit /etc/modprobe.d/blacklist.conf to re-enable nouveau
you will need to re-blacklist it when installing nvidia's run file driver

---

### Post by Krytarik on 2011-03-23
As for your Nvidia driver, you may try those provided by Xorg-Edgers' PPA, it's more recent than those provided by the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```As for Wine's performance, do you expect Linux apps to run in Windows as fast as they do in Linux?! ;-)

Greetings.

**EDIT:** And yes, I also hear those claims of Wine running apps/games more stable/faster or at least as fast as they run in Windows. But in fact, I don't even get some pretty simple puzzle games to run at my mom's system.

---

### Post by Dlambert on 2011-03-24
Looks like your running NVidia, but run in terminal ```
nvidia-settings
```


Wine is great, if you have the right hardware.

---

### Post by 3246251196 on 2011-03-25
> **Dlambert said:**
> Looks like your running NVidia, but run in terminal ```
nvidia-settings
```
Wine is great, if you have the right hardware.

That command brings up NVIDIA X Server Settings. So, it looks like I am running nVidia.

Just out of curiosity, in Ubuntu SWare Center when I search for NOUVEAU, both:

- Userspace interface to nouveau-specific kernel DRM services -- runtime

and

- X.Org X server -- Nouveau display driver (experimental)

both have a green check mark next to them.

Why?

---

### Post by realzippy on 2011-03-25
Means they are installed,btw many graphics drivers are preinstalled,
but they are not in use.

---

### Post by 3246251196 on 2011-03-25
Thanks, I have them, but they are not in use.

---

### Post by Dlambert on 2011-03-25
Yep, looks like your drivers are working. Look up configs etc in [AppDB]("http://appdb.winehq.org/") on wine's website to try and get your performance better.

---

### Post by 3246251196 on 2011-03-26
Thankyou for that link, Dlam. It brought about a point that I had overlooked. Trial and error with the version of Windows emulation has done the trick.

For instance, I have found that through Anarchy Online, Windows 95 emulation is the key. When I tried Win95, my FPS was somewhere near 66%-100% better. Additionally, I have found that less clutter within my GUI for AO helps a lot. Some of the windows I had running (to access my perks etc) were taking up ~~5 FPS. Therefore, a combination of less clutter and Win95 emulation has brought my FPS to somewhere near double what it was before.

Similarly, Guild Wars works a lot better through Win98 emulation. I was getting 10-30 FPS. Well, now, I am getting 30-60 FPS.

Thankyou all.

---

### Post by 3246251196 on 2011-03-26
> **Krytarik said:**
> As for your Nvidia driver, you may try those provided by Xorg-Edgers' PPA, it's more recent than those provided by the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```As for Wine's performance, do you expect Linux apps to run in Windows as fast as they do in Linux?! ;-)

Greetings.

**EDIT:** And yes, I also hear those claims of Wine running apps/games more stable/faster or at least as fast as they run in Windows. But in fact, I don't even get some pretty simple puzzle games to run at my mom's system.

Though, I have not tried this yet. I still have the drivers from the official nVidia website: [[http://www.nvidia.co.uk/object/linux-display-ia32-260.19.44-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.44-driver-uk.html)]

Something to consider I suppose! If anyone knows that the drivers I have linked are menacing then please let me know.

---

### Post by Krytarik on 2011-03-27
> **3246251196 said:**
> Though, I have not tried this yet. I still have the drivers from the official nVidia website: [[http://www.nvidia.co.uk/object/linux-display-ia32-260.19.44-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.44-driver-uk.html)]

Something to consider I suppose! If anyone knows that the drivers I have linked are menacing then please let me know.
Oh, I just saw this by luck. I unsubscribed myself before, because of the apparent nonsense ping-pong play here.

If you want to try those manual install, consider that
- it is not a safe install, you can't remove the driver easily and safely
- you have to re-install the driver each time when the kernel gets upgraded
- the driver will not get updated automatically

---

### Post by Dlambert on 2011-03-27
> **Krytarik said:**
> Oh, I just saw this by luck. I unsubscribed myself before, because of the apparent nonsense ping-pong play here.

If you want to try those manual install, consider that
- it is not a safe install, you can't remove the driver easyly and safely
- you have to re-install the driver each time when the kernel gets upgraded


I bed to differ, there is a script to automatically do it(reinstall), and the process in easy for me.

No problem, just passing on advice.

You may want to mark the thread as solved.

---

### Post by Krytarik on 2011-03-27
> **Dlambert said:**
> I bed to differ, there is a script to automatically do it(reinstall), and the process in easy for me.

I know, I also used the manual install back in Gutsy 7.10.
But I always ended up at the console login after a kernel upgrade, and then I needed to run the installer from there. And yeah, like you said, no problem for the experienced and non-panicking user, but not every user is that advanced.

And yeah, it may even be that X manages to start a xserver in low graphics mode upon normal boot. But at least when choose the "recovery mode" boot option, you should be able to get to the desktop.

---

