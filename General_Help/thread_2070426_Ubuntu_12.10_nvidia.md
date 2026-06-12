---
title: "Ubuntu 12.10 nvidia"
date: 2012-10-12
forum: General Help
---

### Post by waspinator on 2012-10-12
Hi,

I installed the 64bit-PC daily image from 2012-10-11 (release candidate according to the release schedule) and I can't get my graphics to work properly.

Computer Specification:
Motherboard: Gigabyte X58A-UD3R rev1
Graphics:    nVIDIA GeForce GTX560 (GF114)
Screen:      Samsung BX2431 (1920x1080)

During installation, and when I first boot up, my screen is stuck at 1366x768 resolution. I thought I would try to install proprietary drivers to fix this. After installing them though, I am stuck at 1280x1024 and unity no longer starts. I can right click and make a new folder, or change my background, but none of the windows have any borders.

Under System Overview my graphics are listed as:
VESA: GF104B Board - 10410050

It was working fine on ubuntu 12.04.

Any ideas on what I can do? Is nVIDIA still supported in ubuntu?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
```
gtk-window-decorator
```that should get the borders back
```
sudo nvidia-xconfig;sudo reboot
```should get the driver working
i am using xubuntu 12.10 with nvidia and so is my mom

---

### Post by grahammechanical on 2012-10-12
It is not a case of Ubuntu supporting Nvidia but of Nvidia supporting Linux with drivers that are not buggy.

I stopped using Nvidia drivers a few weeks ago then things seemed to be fixed so I went back to it. Then this happened

[http://ubuntuforums.org/showthread.php?t=2067033]("http://ubuntuforums.org/showthread.php?t=2067033")

I am using the Nouveau driver. I do not know if this issue has been fixed.

If you go to System Settings>Software Sources you will see a tab for Additional Drivers. It will let you activate another version of the Nvidia driver or the Nouveau driver.

Regards.

---

### Post by waspinator on 2012-10-12
> **pqwoerituytrueiwoq said:**
> ```
gtk-window-decorator
```that should get the borders back
```
sudo nvidia-xconfig;sudo reboot
```should get the driver working
i am using xubuntu 12.10 with nvidia and so is my mom

Hmm. gtk-window-decorator says it's already running. Using the --replace option causes it to crash.

I tried the nvidia-xconfig, and reboot, but now it's stuck at 640x480 and gives me an error:

Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes.

I'm going to try ubuntu 12.10 beta 2 32bit and see if that helps.


**edit**: even worse

beta 2 32bit won't even boot into live mode. It just gives black/white horizontal stripes.

**edit2**: I can boot using the nomodset option. (should be labeled "Safe Graphics Mode" or something)

Trying to install again.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
sudo apt-get purge nvidia-current;sudo apt-get install nvidia-current-updates

---

### Post by waspinator on 2012-10-12
ok, solved. After installing ubuntu 12.10 beta 2 32bit and using the nomodeset option (hold shift to show grub, press e on ubuntu, and add nomodeset before quite boot) I got it to install. After booting the first time I went into software source, and installed the nvidia driver. After another reboot I got full resolution.

Thanks.

---

### Post by KAding on 2012-10-18
In my case installing the nvidia-current driver in the end failed because it couldn´t compile the module.

So the problem was solved by installing the kernel headers and then reinstalling the driver:
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove nvidia-current
sudo apt-get install nvidia-current

---

### Post by drdanielfc on 2012-10-18
> **KAding said:**
> In my case installing the nvidia-current driver in the end failed because it couldn´t compile the module.

So the problem was solved by installing the kernel headers and then reinstalling the driver:
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove nvidia-current
sudo apt-get install nvidia-current

Thank you so much! That did it for me. You sir are amazing.

For those of you who install the driver and then get stuck in that windowless desktop, you can press Ctrl+Alt+T to open up a terminal and then execute those commands. :)

---

### Post by alphalux on 2012-10-18
KAding's suggestion also fixed my problems. For some reason, I had buggy performance with the Nauveau display driver on a GeForce 210. Applying the nvidia-current driver via the Software Sources tab gave this result. It was only by adding the linux-headers that the nvidia-current driver worked. 

Thank you.

---

### Post by jajodo on 2012-10-20
Fabulous answer.  Installing the nvidia drivers on 12.10 amd64 via software sources left me with a purple windowless screen with black borders.  Not a whole lot of eye candy to say the least.  Following those command line instructions after ctrl-alt-t to bring up terminal brought back my desktop!

Ubuntu needs to do better than having buggy default Nouveau drivers and "proprietary tested" nvidia drivers that bring down the entire windowing system.  With the Nouveau drivers text appears as a sguiggly lines.

---

### Post by oizukitom on 2012-10-20
Greetings,

I feel terrible turning from a generally happy Ubuntu user to a complainer...

Are  you guys kidding me? This is a joke right? A DualCore with a nvidia  GF9500 is hardly new or exotic hardware yet still modern. Ok Ubuntu  12.04 and X and ?? something don't get along. No problem, I still have a  fall back install on another drive. 

12.10 is out. And guess  what, same issues !!!! Are you kidding me? Guys, you have heard of this  little company Nvidia right?  They have been making these things called  graphics cards and GPU's for nearly 20 years.  How does this happen? I  could see if I just came home with a GTX 660 Ti and it needed driver  help, but a GF9500?? To boot,  both a GF9500 and 550Ti worked GREAT on  the 11.xx version  ie my fall back.  

I see above that there is a  possible fix ... I will try it. I will hope it works so I can get back  to being a generally productive, hassle free, user.  My entire point is  this, I thought we were past stuff like this? When someone has to post  youtube vids to show users how to get their video cards to work, there  is a problem.  I don't mind a little shell work. But what about the  people who don't have another PC, never used a text based web browser,  or think 'shell' is what you get on the beach?   Or they don't know or  care to know what nomodeset is or does ? How exactly are they applying  the fix above? (Thank you for that BTW) Also for the record, until open  drivers or packaged drivers are capable of using other avenues to the  GPU like CUDA and OpenCL then I need the manufacturer's drivers.  You  know what scratch that, I just want the install/Live DVD to boot. Can we  start there?

I know people are giving Unity a hard time. It is  new and not bad at all. But one would think, 'man I have all these cool  effects for the desktop and 3D in Unity, let's see how they look on 32"  displays and a new Nivida 680.'  NO! you won't be able to, the LIVE DVD  only boots to VESA mode.

Using this nomodeset display to bitch and complain in a forum is nice.   

I  am sure there is a perfectly sound technical excuse why 12.xx doesn't  work and 11.xx does, but I don't care. I am still bitching and  complaining in nomodeset from the LIVE DVD.

No coffee for you,  just take a hand full of coffee beans in your mouth, chew them up, then  take a big slug of hot water, and swallow.  That's the user experience  we are going for now.

Man I feel better. Please feel free to delete this post. It is not constructive in any way. 

Sincerely.

EDIT:
After I cooled my jets. I went in again...  all for 64 bit.

If users are having trouble getting the 12.10 LIVE to boot with the intention of installing to hard drive and your hardware is nvidia, you may want to make sure you do a cold boot. Power your computer down completely ( not just a restart ).  Try to boot the 12.10 DVD now and see what you get. I am at an installed to hard drive,  full screen mode of some type now, my Details indicate Graphics Driver unknown Experience standard. We are getting somewhere.  

Now to try above and below posts with kernel headers. ( Thanks BTW )

---

### Post by Lisiano on 2012-10-20
The bug is caused by the drivers NOT pulling in the kernel headers
```
Package: nvidia-current
Priority: optional
Section: restricted/misc
Installed-Size: 198960
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: nvidia-graphics-drivers
Version: 304.51.really.304.43-0ubuntu1
Replaces: fglrx, fglrx-updates, nvidia-173, nvidia-173-updates, nvidia-180-modaliases, nvidia-185-modaliases, nvidia-96, nvidia-96-updates, nvidia-current-modaliases, nvidia-current-updates, nvidia-experimental-304
Provides: fglrx, fglrx-updates, nvidia-173, nvidia-173-updates, nvidia-96, nvidia-96-updates, nvidia-current-updates, nvidia-experimental-304, xorg-driver-video
**Depends**: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, **linux-headers-generic | linux-headers**, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13, xserver-xorg-core (>= 2:1.10.99.901)
Recommends: nvidia-settings
Conflicts: fglrx, fglrx-updates, nvidia-173, nvidia-173-updates, nvidia-180-modaliases, nvidia-185-modaliases, nvidia-96, nvidia-96-updates, nvidia-current-modaliases, nvidia-current-updates, nvidia-experimental-304
Filename: pool/restricted/n/nvidia-graphics-drivers/nvidia-current_304.51.really.304.43-0ubuntu1_amd64.deb

```But as you can see, highlighted are the kernel headers. Because they are missing, the driver can't compile and therefore, can't be loaded. Just install the headers manually and the system will happily compile the driver.

---

### Post by robrobinette on 2012-10-22
> **sakirasci said:**
> You saved me from a big trouble, thanks dude :) I'll add some extra information to what you've explained: there is an easy way to remove AMD (fglrx) drivers, just open a terminal and apply these commands:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```I applied these, and just like you said I saved my Ubuntu 12.10! Hope it helps to other people who got stuck with their 12.10 upgrades.

My "additional drivers" box was empty but his worked for me with my ATI drivers, thanks for the help!

---

### Post by sonicb00m on 2012-11-01
It's odd the driver issue is still a problem. Installing the kernel headers seems to be the key to get this going again.

---

### Post by tonyis3l33t on 2012-11-02
Worked perfectly, thanks KAding.

---

### Post by ias on 2012-11-06
> **KAding said:**
> In my case installing the nvidia-current driver in the end failed because it couldn´t compile the module.

So the problem was solved by installing the kernel headers and then reinstalling the driver:
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove nvidia-current
sudo apt-get install nvidia-current

This eventually worked, thanks! However, I noticed that when doing the last line of the commands, it asked for linux-headers-3.5.0-18, so I repeated the process replacing 17 by 18. There should be a command/script which checks which version you need to avoid future confusion. 

In any case, it now works!

---

### Post by Benchamoneh on 2012-11-07
Do you have to install the specific headers to make this work? Can't you use linux-headers-generic? Just curious as I'm concerned with what would happen when a new image comes out, would that just break again and require you to install the new headers and then reinstall the current driver?

---

### Post by Benchamoneh on 2012-11-07
> **Benchamoneh said:**
> Do you have to install the specific headers to make this work? Can't you use linux-headers-generic? Just curious as I'm concerned with what would happen when a new image comes out, would that just break again and require you to install the new headers and then reinstall the current driver?

Just for the benefit of all interested, I've just tried the above and it works fine. It's easier for people to just install the generic headers rather than look up their current linux image and install the headers for that.

---

### Post by drdanielfc on 2012-11-08
> **Benchamoneh said:**
> Do you have to install the specific headers to make this work? Can't you use linux-headers-generic? Just curious as I'm concerned with what would happen when a new image comes out, would that just break again and require you to install the new headers and then reinstall the current driver?

Turns out the answer to that question is a big fat YES (it does break it).

To solve, Ctrl+Alt+T
```
sudo apt-get install linux-headers-3.5.0-18-generic
sudo apt-get remove nvidia-current
sudo apt-get install nvidia-current
```

I didn't try with the generic so can't tell you if that works.

---

### Post by zephod on 2012-11-10
Excellent - headers, uninstall, reinstall works.

Assuming you get a clean boot then you can do this if you want latest:

```
sudo apt-get install nvidia-current-updates
```

---

### Post by d4nc00per on 2012-12-11
Just installing linux headers fixes this!?!?!?!?!?!  I recently upgraded from 12.04 and then decided to do a fresh install, on installing my nvidia drivers, Unity wouldn't work and it took me forever on Google before I found this thread. I absolutely love Ubuntu but isn't this something that can be avoided by just installing these headers automatically during the install of Ubuntu? Would cause a lot less distress and earache.

---

### Post by teknojunkey on 2013-01-02
i finally got this working, i have to change the header to match mine

sudo apt-get install linux-headers-3.5.0-18-generic
sudo apt-get install linux-headers-3.5.0-21-generic

---

### Post by david_215 on 2013-01-16
None of the above worked for me with my 3.5.0-21-generic headers and GeForce GT 440 video card.  What DID work was downloading the latest linux driver from the nvidia website (version 310.19), and running the installer manually.  This READ ME contains the installation instructions:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/index.html)

Basically, I opened a terminal window, uninstalled the existing nvidia driver:
sudo apt-get remove --purge nvidia-current

Then I stopped the X server:
sudo service lightdm stop

Navigated to the folder into which I downloaded the nvidia file, and ran the installer:
sh NVIDIA-Linux-x86_64-310.19.run

Finally, I restarted X server:
sudo service lightdm start

And all was well with the world.

---

### Post by nesur on 2013-01-16
You don't need to manually install headers for each new kernel version, just install linux-headers-generic:
[INDENT] [I]sudo apt-get install linux-headers-generic
[/I][/INDENT]and that meta-package will always pull the latest version of the headers.

---

### Post by WolfWuerd on 2013-02-05
Actually, oizukitom, I'm quite upset too.  I've enjoyed Ubuntu for close to a decade and have boasted that it was among the most stable O/Ss out there.  When I upgraded from 11.04 to 12.10 I had a good deal of trouble getting my NVidia drivers to work (the Nouveau driver was painfully slow and glitchy).  All was well until I allowed the most recent kernel update, and then I was back to single-screen, no borders, no toolbars and some windows refused to accept focus.  With the fix in this thread I've been able to resolve the issue but I'm not waiting to see if I have to do this after each header update.  I'll try Kubuntu and if that isn't more stable then I'll have to use the W****** word at my local computer store.  I can't afford to research work-arounds for "stable" releases every month or so.

---

### Post by jmdennis on 2013-02-08
> **WolfWuerd said:**
> Actually, oizukitom, I'm quite upset too.  I've enjoyed Ubuntu for close to a decade and have boasted that it was among the most stable O/Ss out there.  When I upgraded from 11.04 to 12.10 I had a good deal of trouble getting my NVidia drivers to work (the Nouveau driver was painfully slow and glitchy).  All was well until I allowed the most recent kernel update, and then I was back to single-screen, no borders, no toolbars and some windows refused to accept focus.  With the fix in this thread I've been able to resolve the issue but I'm not waiting to see if I have to do this after each header update.  I'll try Kubuntu and if that isn't more stable then I'll have to use the W****** word at my local computer store.  I can't afford to research work-arounds for "stable" releases every month or so.

Just so you know I used Kubuntu and it seems more stable with Nvidia as I used the newest one listed the 310 driver and it worked great in Kubuntu.  I was trying Ubuntu to see what it was like and had nothing but problems.  I also had problems with the Nouveau driver as some times it would go to a black screen and just post error messages so I have to use the real nvidia driver.

---

### Post by MichZem on 2013-03-05
Do you have any update, regarding your Kubuntu experience? I also have some troubles with Ubuntu, since the last 3 month ... Re-install it didn't solve the problem but just create other ones ... 
Seems like the stable release is not stable as it should, in specific configuration/hardware ... 

Thanks for updating , Mich

---

### Post by tlan on 2013-04-11
> **david_215 said:**
> None of the above worked for me with my 3.5.0-21-generic headers and GeForce GT 440 video card.  What DID work was downloading the latest linux driver from the nvidia website (version 310.19), and running the installer manually.  This READ ME contains the installation instructions:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/README/index.html)

Basically, I opened a terminal window, uninstalled the existing nvidia driver:
sudo apt-get remove --purge nvidia-current

Then I stopped the X server:
sudo service lightdm stop

Navigated to the folder into which I downloaded the nvidia file, and ran the installer:
sh NVIDIA-Linux-x86_64-310.19.run

Finally, I restarted X server:
sudo service lightdm start

And all was well with the world.

This worked for me with this exception, sudo apt-get remove --purge nvidia*
to remove all nvidia, 

I use the latest driver provided by nvidia which is 310.44 at the time of this writing.
I also installed a fresh copy of 12.10 in anticipation of 13.04

---

### Post by williammanda on 2013-05-04
> **nesur said:**
> You don't need to manually install headers for each new kernel version, just install linux-headers-generic:
[INDENT] [I]sudo apt-get install linux-headers-generic
[/I][/INDENT]and that meta-package will always pull the latest version of the headers.

I too was having the same issue with Nvidia and Ubuntu 12.10 64 bit...the borderless wallpaper without a desktop. I did as you suggested...1. Made sure I was using the nouveau driver. 2. sudo apt-get install linux-headers-generic. 3. Loaded the Nvidia driver I wanted to use. Thanks!

---

