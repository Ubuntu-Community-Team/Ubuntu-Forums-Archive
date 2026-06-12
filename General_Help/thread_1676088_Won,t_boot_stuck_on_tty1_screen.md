---
title: "Won,t boot stuck on tty1 screen"
date: 2011-01-26
forum: General Help
---

### Post by carpetmanleo on 2011-01-26
I was upgrading video driver from nvidia (260.19.36), and restarted as prompted. now it wont load desktop just goes to tty1. tried startx says no such directory ubuntu newbie please help. thanks in advance:popcorn:

---

### Post by corncob on 2011-01-26
Try pressing ctrl-alt-F7.
Oh well, I gave the thread a bump anyway.

---

### Post by Krytarik on 2011-01-27
> **corncob said:**
> Try pressing ctrl-alt-F7.
Oh well, I gave the thread a bump anyway.
Won't work, unfortunately.;-)

How did you install the driver, manually with the installer from Nvidia's website or via "System -> Administration -> Hardware Drivers (10.04) / Additional Drivers (10.10)"?

Try booting via "recovery mode -> Try to fix X server", this should get you to the desktop, without running the Nvidia driver. If that doesn't work, login at the console and remove/rename the file "/etc/X11/xorg.conf".

---

### Post by carpetmanleo on 2011-01-27
I did it manually everything was fine for a few days , then my daughter wanted to play the sims 3 so i got it going , then ubuntu did some automatic updates and the game quit working. said it needed 3-d acceleration and i switched to the one in ubuntu to see if that helped and rebooted and that is when it started. whew.:confused:

---

### Post by Krytarik on 2011-01-27
> **carpetmanleo said:**
> i switched to the one in ubuntu
How did you do that?

If not via Hardware Drivers/Additional Drivers, but instead via apt-get/Synanptic then remove it from there.

In either case un-install the manually installed driver following the install instructions.

After that install the driver via Hardware Drivers/Additional Drivers.

---

### Post by carpetmanleo on 2011-01-28
I did it in the additional drivers.It wont let me uninstall or install says no such file or directory.

---

### Post by Krytarik on 2011-01-28
I need more info.

Please provide some output of what it says exactly, of both the un-install of the manually installed driver and of the install via "Additional Drivers".

Did you upgrade your Ubuntu version, e.g. from 10.04 to 10.10?

Please upgrade your packages again:
```
sudo apt-get update
sudo apt-get upgrade
```After doing that, what is the output of the following commands?:
```
dpkg -l |grep linux
``````
uname -r
``````
dpkg -l |grep nvidia
```
Please post all outputs enclosed in code-tags (#).

---

### Post by carpetmanleo on 2011-02-05
I just put another hd in it I will mess with it when i dont fell like holding a hammer. :evil:

---

### Post by carpetmanleo on 2011-03-04
Krytarik 
 this is my output
(dpkg -l |grep linux
ii nvidia-173                                                          173.14.280ubuntu1
          nvidia binary xorg driver, kernel module and vdpau library
ii nvidia-173 modaliases                                        173.14.280ubuntu1
           modaliases for the nvidia binary x.org driver
ii nvidia-96-modaliases                                          96.43.190ubuntu1
           modaliases for the nvidia binary x.org driver
ii nvidia-current-modaliases                                   260.19.06-0ubuntu1
             modaliases for the nvidia binary x.org driver )

(uname -r    2.6.35-27-generic )

(dpkg -l |grep nvdia 
ii nvidia-173                                                          173.14.280ubuntu1
          nvidia binary xorg driver, kernel module and vdpau library
ii nvidia-173 modaliases                                        173.14.280ubuntu1
           modaliases for the nvidia binary x.org driver
ii nvidia-96-modaliases                                          96.43.190ubuntu1
           modaliases for the nvidia binary x.org driver
ii nvidia-current-modaliases                                   260.19.06-0ubuntu1
             modaliases for the nvidia binary x.org driver )
sorry took so long been busy thanks for your help though

---

### Post by Krytarik on 2011-03-04
Hi back, carpetmanleo.

You posted the nvidia packages twice, please add those of the linux packages. ;-)

---

### Post by carpetmanleo on 2011-03-04
> **Krytarik said:**
> Hi back, carpetmanleo.

You posted the nvidia packages twice, please add those of the linux packages. ;-)
Sorry bout that :confused:
(dpkg -l |grep linux                                      
generic linux kernal headers
ii linux-image-2.6.35-22-generic                                   2.6.35-22.35
linux kernal image for version2.6.3.5 on x86x86-64
ii linux-image 2.6.35-25-generic                                   2.6.35-27.44
linux kernal image for version2.6.3.5 on x86x86-64
ii linux- image 2.6.35-27-generic                                   2.6.35-27.48
linux kernal image for version2.6.3.5 on x86x86-64
ii linux-image generic                                                     2.6.35.27.35
generic linux kernal image
ii linux-libc-dev                                                               2.6.35-1027.48
linux kernal headers for deployment
ii linux-sound-base                                                         1.0.23 +dfsg 1ubuntu4
base package for alsa and oss sound systems
ii playonlinux                                                                    3.8.11
play on linux is a front end for wine
ii pptp-linux                                                                       1.7.2-5
point to point tunneling protocal9pptp0 client
ii sys linux                                                                     2 ;4.01+dfsg-3ubuntu1
collection of bootloaders
ii sys linux-common                                                     2:4.01+dfsg-3ubuntu1
collection of bootloader ( common files)
ii util-linux                                                                      2.17.2-0ubuntu.10.10.2
*miscellaneous* system utilities )

---

### Post by mmsmc on 2011-03-04
are you able to get into failsafe graphics mode through recovery?

---

### Post by carpetmanleo on 2011-03-04
what exactly is recovery?:confused:

---

### Post by Krytarik on 2011-03-04
So, unfortunately you missed to post the first, more important, part of the "linux" package listing, but kudos for writing these down by hand! ;-)

Please check again and make sure that the following packages are installed:
- linux-headers-generic (seems to be)
- linux-headers-2.6.35-27
- linux-headers-2.6.35-27-generic

Also I noticed that you have version 173 of the proprietary driver installed, replace it with the "current" version, do it manually:
```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-current
```After doing so, make sure to have a proper xorg.conf by running those command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Then reboot.

---

### Post by mmsmc on 2011-03-04
when you boot to grub, you have 2 choices for ubuntu, normal and recovery, click on recovery and choose failsafe, if you get in you can uninstall nvidia from there, if not listen to krytarik

---

### Post by carpetmanleo on 2011-03-05
> **mmsmc said:**
> when you boot to grub, you have 2 choices for ubuntu, normal and recovery, click on recovery and choose failsafe, if you get in you can uninstall nvidia from there, if not listen to krytarik

it doesn't give me that choice. It did before the update, oh well I will try Krytarik's . thanks. sorry bout the first line i had it wrote down just forgot it.

---

### Post by carpetmanleo on 2011-03-05
> **Krytarik said:**
> So, unfortunately you missed to post the first, more important, part of the "linux" package listing, but kudos for writing these down by hand! ;-)

Please check again and make sure that the following packages are installed:
- linux-headers-generic (seems to be)
- linux-headers-2.6.35-27
- linux-headers-2.6.35-27-generic

Also I noticed that you have version 173 of the proprietary driver installed, replace it with the "current" version, do it manually:
```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-current
```After doing so, make sure to have a proper xorg.conf by running those command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Then reboot.

 wow! I owe ya one.well maybe two.Thanks a bunch.I could have wiped it out and redone it but where would the fun be in that huh.:D  How do you no all these commands? Is there a manual or something? Anyways thanks for all your help Krytarik. You to MMSMC.

---

### Post by Krytarik on 2011-03-05
> **carpetmanleo said:**
> How do you no all these commands? Is there a manual or something?
How long would that manual be, eh?! :P No, I use Linux since some 8 years or so now, and you learn a lot in that time, see a lot of guides, install instructions, UF threads and so on...

You will find a lot of good guides here, I use them regularily as reference and to learn more:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)

Btw., great that it worked! Please mark this thread as "solved", via "Thread Tools".

Greetings.

---

### Post by carpetmanleo on 2011-03-05
> **Krytarik said:**
> How long would that manual be, eh?! :P No, I use Linux since some 8 years or so now, and you learn a lot in that time, see a lot of guides, install instructions, UF threads and so on...

You will find a lot of good guides here, I use them regularily as reference and to learn more:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)

Btw., great that it worked! Please mark this thread as "solved", via "Thread Tools".

Greetings.
  well thanks for your help ; I really appreciate it.:guitar:

---

