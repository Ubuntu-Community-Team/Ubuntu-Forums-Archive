---
title: "Eyefinity with HD5850?"
date: 2010-05-10
forum: General Help
---

### Post by espen@quadnetwork.com on 2010-05-10
A couple of months ago I got a new Radeon HD5850 card for my 3 monitor setup.
After installing it I found out that it won't work without an active DisplayPort adapter for the third monitor. Slightly annoyed I bought one and thought that everything was going to work out.
And it actually did... I was running a beta version of kubuntu 10.04 at the time and installed the fglrx drivers through synaptic. All 3 monitors came to life without any problems.:)
One day the update manager informed me that there were several updates ready, and one of them was fglrx related. I don't know what it was for because I didn't exactly expect that it would screw everything up, so I didn't pay much attention.
But after that, no more 3 monitor support...:shock:
I tried downloading and installing the driver directly from AMD, waiting for the 10.4 driver, do a fresh kubuntu install after the final was released, and also installing ubuntu.
Nothing worked. I still had only max 2 monitors, and to make it worse, dual monitor settings were reset after every reboot (yes, I ran the ati config with sudo).
Another thing I noticed was that 2D performance was horrible. Just dragging a window would cause a trail of "old" windows across the more than half the screen that stayed for over a second. I don't know if the window issue was there before I lost 3 monitor support though.

I was starting to think that my adapter might be broken. But today I tried installing windows 7, and as soon as the drivers were installed, all 3 monitors came to life...

So to sum up: What the hell is wrong with the AMD/ATI's Linux driver? I knew I wasn't going to get the same lever of functionality with ATI's Linux drivers, but this is absolutely crap!:evil:

Could there be something I did wrong during the install of the drivers thats causing this? Since the ATI control panel was working I assumed that the fglrx was loaded, but in frustration I forgot to check the list of loaded modules. Could the control panel work without the module being loaded?
I could just reinstall ubuntu and check, but after reaching frustration levels close to "destroy computer", I don't want to reinstall again without at least some possibility of getting a working system.

Sorry for my long rant, hope someone has some ideas.

---

### Post by quadproc on 2010-05-10
> **espen@quadnetwork.com said:**
> A couple of months ago I got a new Radeon HD5850 card for my 3 monitor setup.
After installing it I found out that it won't work without an active DisplayPort adapter for the third monitor. Slightly annoyed I bought one and thought that everything was going to work out.
And it actually did... I was running a beta version of kubuntu 10.04 at the time and installed the fglrx drivers through synaptic. All 3 monitors came to life without any problems.
This is a guess - the 10.04 beta used the ATI 10.3 driver?  If so, then going back to the ATI 10.3 driver might improve things.

I have seen some comments about the ATI 10.4 driver causing graphics problems.  I am running 10.3 and it is behaving well; I am also on Ubuntu 9.10.

One other thought: I have read of several people disabling KMS and thereby getting rid of a bunch of graphics problems.  The test review of KMS that I read showed a performance decrease with KMS enabled.:(

quadproc

---

### Post by espen@quadnetwork.com on 2010-05-11
I was running 10.3 both before and after the "fatal" update. So I have no idea exactly what that update did to the driver.
It was only after trying several combinations of driver installs and OS reinstalls that I figured it would help to wait and try the 10.4 driver.

Is there a chance that disabling KMS would solve the multi monitor issue?
Thats the most important issue for me.
Because the slooow graphics is something I can live with for the time being, but being unable to use all monitors is not something I can accept.

---

### Post by quadproc on 2010-05-12
> **espen@quadnetwork.com said:**
> I was running 10.3 both before and after the "fatal" update. So I have no idea exactly what that update did to the driver.
It was only after trying several combinations of driver installs and OS reinstalls that I figured it would help to wait and try the 10.4 driver.
Yes, that was a reasonable approach.

Did you completely remove all traces of the old driver (regardless of version) before you installed the new one?  I ask because I have seen strange and bizarre behavior due to vestiges of old drivers being left around when a new driver is installed.  I suspect that the installation process pulls in things like libraries and include files which are close enough to funtion but not close enough to function properly.

> 
Is there a chance that disabling KMS would solve the multi monitor issue?
Thats the most important issue for me.
Yes, that is a possibility.  I cannot say for sure because I haven't seen it myself but I have read several descriptions which sound very similar to your problem.

Good luck!

quadproc

---

### Post by zryder94 on 2010-05-18
Did you find a solution to your problem? I am trying to get my 3rd monitor to work in 10.04 LTS with my 5850..

---

### Post by espen@quadnetwork.com on 2010-05-22
I haven't had time to test it yet. I've had a lot of work to do thats dependent on a 3 monitor setup, so there hasn't been any time for testing. So regrettably the system is on Windows 7 until I have more spare time.

---

### Post by leo67 on 2010-06-03
Hi all,

I have exactly the same issue with my desktop PC dual-boot Win7/ubuntu 10.4: After having  installed freshly ubuntu 10.4 LTS and the ATI FPLG drivers, my radeon 5450 was properly recognised but the LCD connected to the VGA port was shown in grey in the Catalyst Control Center (screen black and non functional) whereas my 2 others LCD screens respectively connected to the DVI and Displayport-converter- VGA worked fine. No way to use the first screen and the video hardware acceleration is quite crappy (I have a laptop with an Intel GMA 900 under the same new ubuntu 10.4 and DVDs played by VLC are as good as under VLC windows for instance which is not the case for the desktop+ATI).

As I am more used to tweak Windows than Linux, a hand would would be welcome as how to get the best from Eyefinity compliant card.

Thanks.

---

### Post by edwebdev on 2010-08-05
Hi everyone,

I have this problem as well. Running up to date Ubuntu 9.10 with an ATI Radeon HD 5850 (won't upgrade to 10.04 due to horrible problems with the video card support).

Anyway, getting dual monitor to work is super easy. The setup works fine when I have two monitors plugged into the video card's two DVI ports.

However, I am trying to go to triple monitors, using the video card's displayport connection to connect a third monitor. Triple monitors works easily on Windows 7 Professional (it's a dual-boot system), but I can't get it to work under Ubuntu. The operating system sees the third monitor, but when I try to enable it, it tells me "could not find a suitable configuration of screens." All three monitors are identical Dell ultrasharp 2408wfp 1920x1200 screens.

Thanks,
Sean

---

