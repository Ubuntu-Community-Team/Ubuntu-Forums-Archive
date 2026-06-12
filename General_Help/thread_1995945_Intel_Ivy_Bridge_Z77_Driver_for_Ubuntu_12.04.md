---
title: "Intel Ivy Bridge Z77 Driver for Ubuntu 12.04"
date: 2012-06-03
forum: General Help
---

### Post by Mesopotamia on 2012-06-03
Hi everyone,

I was wondering where I can get the repository for the latest Intel Z77 chipset from?

I've got the new Intel Ivy Bridge 3570K along with with the built in HD4000 video card.

Thanks

Edited: I found [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) but they don't seen to mention anything about the Z77 chipset.

---

### Post by traditionalist on 2012-06-03
Not directly but you might find what you want if you follow this up;

[http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1)

---

### Post by 3Miro on 2012-06-03
Is there something not working right?

Under Linux, all the open drivers are integrated into the kernel, if you want to update the drivers, you simply update the kernel. You can look for a beta or unofficial version of the kernel, but unless you have something broken right now, the new kernel will probably be less stable and cause more problems (since it is still under development).

---

### Post by Mesopotamia on 2012-06-03
> **3Miro said:**
> Is there something not working right?

Under Linux, all the open drivers are integrated into the kernel, if you want to update the drivers, you simply update the kernel. You can look for a beta or unofficial version of the kernel, but unless you have something broken right now, the new kernel will probably be less stable and cause more problems (since it is still under development).

12.04 keeps freezing randomly. Whether I'm browsing, encoding a video, or watching YouTube.

The other thing I noticed in System Setting is that the Graphic Card isn't identified as Intel HD4000, whereas it was in 11.10.

I'm going to use this PC mainly for HTPC, so I need to make sure that all the hardware acceleration is maintained if I have a driver installed.

Thanks for your help.

---

### Post by Mesopotamia on 2012-06-03
> **traditionalist said:**
> Not directly but you might find what you want if you follow this up;

[http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1)

Thanks for that, but the article doesn't really show where to get the driver from.

---

### Post by traditionalist on 2012-06-03
> **Mesopotamia said:**
> Thanks for that, but the article doesn't really show where to get the driver from.


I think the drivers are integrated. I have not seen a separate download anywhere.

---

### Post by SuperFreak on 2012-06-03
I have a i7 3770k Intel chip and Asrock z77 board. I had problems with frequent freezing of screen, keyboard and mouse with the only solution a hard reset.
I found this site and no longer have any problems but use at your own risk[http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html]("http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html")

---

### Post by idoitprone on 2012-06-03
wiki to the latest linux build

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Kernel.2BAC8-FAQ.2BAC8-DebuggingMainlineBuildsSupport.Does_the_kernel_team_support_the_mainline_kernel_builds.3F](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Kernel.2BAC8-FAQ.2BAC8-DebuggingMainlineBuildsSupport.Does_the_kernel_team_support_the_mainline_kernel_builds.3F)

---

### Post by Mesopotamia on 2012-06-04
Thanks everyone for your helpful replies.

Yes, I have the Z77 Astrock motherboard along with the i3570 and the built-in video card.

I just followed SuperFreak and idiotprone's links and the video card is now identified in the System Setting.

I upgraded into the latest 3.3.7 kernel version.

I haven't experienced any freeze up yet as I just performed that upgrade few minutes ago.

I will mark my thread as solved once everything is confirmed.

Thanks gents :)

---

### Post by Mesopotamia on 2012-06-04
I could confirm that Ubuntu hasn't frozen up since I last upgraded the kernel.

Thanks again everybody for your great support :)

---

### Post by uelkfr on 2012-07-12
Hi, I have updated kernel to 3.4.0. This is the latest possible from mainline for Ubuntu 12.04 Precise Pangolin.  But videocard isn't detected in system settings. When I run ogre3d samples I don't see all textures. Can I install v3.5rc6 on Ubuntu 12.04?[ ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.5-rc6-quantal/")

---

### Post by 3Miro on 2012-07-12
Are you using some sort of Hybrid Graphics? Do you have more than one video card or is the Ivy Bridge Video the only video card?

---

### Post by uelkfr on 2012-07-13
No, I use only integrated Intel Graphics.
ASUS P8Z77-V and Intel Ivy Bridge

---

### Post by djlooka on 2012-07-13
I have an i5 3570k on a Z77 Gigabyte mobo.
Ubuntu 12.04, kernel 3.4.4-030404-generic, Mate DM.

**The new kernel helped me solving the freezes**, but I still can't get proper GPU acceleration.

I don't have artifacts, but **the top part of the screen kinda stutters**; sometimes it also happens while scrolling web pages in firefox.

I have to use SW video acceleration, both in xbmc (the main purpose for this machine!) and in vlc or mplayer.

I've been trying almost every tutorial for vaapi but none has worked so far.
I'll try to keep you updated... :(

---

### Post by idoitprone on 2012-07-13
> **djlooka said:**
> I have an i5 3570k on a Z77 Gigabyte mobo.
Ubuntu 12.04, kernel 3.4.4-030404-generic, Mate DM.

**The new kernel helped me solving the freezes**, but I still can't get proper GPU acceleration.

I don't have artifacts, but **the top part of the screen kinda stutters**; sometimes it also happens while scrolling web pages in firefox.

I have to use SW video acceleration, both in xbmc (the main purpose for this machine!) and in vlc or mplayer.

I've been trying almost every tutorial for vaapi but none has worked so far.
I'll try to keep you updated... :(

```
sudo apt-get install libva-intel-vaapi-driver
```

tools->preference->input & codecs->use gpu acceleration

---

### Post by djlooka on 2012-07-14
> **idoitprone said:**
> ```
sudo apt-get install libva-intel-vaapi-driver
```

tools->preference->input & codecs->use gpu acceleration

Thank you for your response.
However, I already have the vaapi driver installed, but unfortunately it doesn't work with vlc (lots of artifacts, whereas pure sw acceleration gives smooth rendering).

```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

After a lot of tinkering, I got it to work with xbmc, so I am probably going to recompile vlc-vaapi and mplayer-vaapi and see if it works.

Stay tuned...

---

