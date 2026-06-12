---
title: "XPS M1330 with 10.04 Lucid Lynx"
date: 2010-05-03
forum: General Help
---

### Post by x C0MMAND0 x on 2010-05-03
Before I upgrade, what are some issues anybody has been having with upgrading/installing 10.04? I currently have Dell XPS M1330 running 64bit 9.04, and will be doing a clean install.

Any issues for anybody out there? I know it just came out, but I am still curious...

---

### Post by tekkidd on 2010-05-03
I would recommend waiting two or three months then doing a small dual boot and use it enough just to make sure all works well. then if you don't have any issues go on to doing a complete install

---

### Post by lviggiani on 2010-05-03
Hi,
I have a XPS M1330 and I upgraded from Karmic 64 bit to Lucid.
Everything went fine (I've not tested wifi and bluetooth yet).
I only got some troubles with nvidia and compiz (I had latest nvidia drivers from nvidia vdpau team)
After upgrade I could not enable desktop effects. So I did a
```
sudo apt-get remove --purge nvidia-*
```
then I removed nvidia-current folders under lib and lib32 (you'll get a message saying that the folder were not deleted as not empty).
The I reinstalled
```
sudo apt-get install nvidia-common nvidia-current
```
Reboot and then sekect "hardware drivers" in order to use the driver.

CAUTION: here I got some troubles with compiz not starting properly. You might see windows without decorations (borders and title bar). If so, refer to this thread:
[http://ubuntuforums.org/showthread.php?t=1470735]("http://ubuntuforums.org/showthread.php?t=1470735")

I hope it helps.

---

### Post by x C0MMAND0 x on 2010-05-04
Sounds good, thank you.

What about:

-Volume buttons / eject button / touch controls?
-IR Remote?
-Webcam?
-Mic (specifically volume, I know there have been issues in the past)
-Brighness step (IE if you fn-Up_arrow to increase brightness does it go up by one step or does it jump like in the past?

I know I can boot to a live CD and test myself, but I haven't had time and I also think that a good solid thread with multiple asked questions for people can be very helpful.

---

### Post by Aeonox on 2010-05-04
Touch controls (playback and volume) don't work, except CD eject. Remote not working, but I'm not sure if my battery died. Mic works fine, I didn't have a volume problem with Skype. Webcam is good too. Brightness increases stepwise.

---

### Post by x C0MMAND0 x on 2010-05-05
That seems like a big deal if the touch buttons don't work...I believe the IR remote is tied in with those buttons which makes sense if one doesn't work the other won't either.

---

### Post by gear.h34d.2012 on 2010-05-05
I have an XPS M1530, the rig one step up from the M1330, and in both Karmic and Lucid everything works flawlessly. Never had an issue. Keep in mind that I'm running 32-bit, however.

---

### Post by prupert on 2010-05-05
Me to, running Lucid 32-Bit, so far no problems other than pre-existing bugs in Lucid. Not used the touch buttons other than Efect. It seems pretty much the same as Karmic, except it boots in 20 seconds...

---

### Post by l!nny on 2010-05-05
m1330 Ubuntu 10.04 64-bit fresh install.  Previously had Dell's customized version of Ubuntu 9.04.

So far everything is working.
wifi (Dell 1505 card using Broadcom driver)
sound - volume is good both recording and playback 
(internal mic = mic 1, external mic = mic 3 in sound preferences)
webcam
all touch buttons and remote
dual monitors (laptop + LCD using Nvidia current drivers)

untested
bluetooth (don't have)
HDMI (haven't had the chance)

linny

---

### Post by aw4lly on 2010-05-06
Hey guys,

I have the 1530 with Intel wireless card, I had a heap of trouble with this on 9.10, hoping to fix it with clean install. Has anyone tried this configuration?

Thanks

---

### Post by ccfiel on 2010-05-06
Hey guys,

How about suspend/hibernate? do you have any issue in xps m1330?

chris

---

### Post by Famicommie on 2010-05-06
> **x C0MMAND0 x said:**
> Sounds good, thank you.

What about:

-Volume buttons / eject button / touch controls?
-IR Remote?
-Webcam?
-Mic (specifically volume, I know there have been issues in the past)
-Brighness step (IE if you fn-Up_arrow to increase brightness does it go up by one step or does it jump like in the past?

I know I can boot to a live CD and test myself, but I haven't had time and I also think that a good solid thread with multiple asked questions for people can be very helpful.

Using the XPS M1330 with intel video card and broadcom wireless card. 64-bit vanilla Ubuntu.

-Wifi works with both fw-cutter and the STA drivers.
-All of the touch controls work fine. Volume movement feels smooth. Mute properly toggles. Skip/stop/play buttons work from within Rhythmbox, and it can be opened with the plastic "house" button.
-Suspend functions properly. Hibernate crashes the computer, but that's most likely because I encrypt my home directory?
-Scrollbars on touchpad function properly.
-Function keys work as marked. Fn-F1 hibernates (and crashes on me lol) Fn-F3 shows battery level. Fn-up and Fn-down now toggles between four steps of brightness.

Yet to test:
-HDMI out
-Touch controls in Movie Player
-Microphone

Can't test:
-Camera (I'm rough on laptops lol)
-Fingerprint reader (see above lol)
-The remote (I move too much)

If you want to use the STA drivers, grab the deb with any necessary dependencies and throw them onto a usb drive. Otherwise you have to ethernet. Fw-cutter pretty much requires a temporary ethernet connection because it pretty much just runs a script that downloads some drivers and extracts the binary blobs from them. It's possible to just pull the drivers and change the shell script, but it's a huge pain in the ***. If you can't get ethernet for fw-cutter, stick with STA.

I've also noticed that when I first disconnect from a power source, the battery meter reads off ten hours or some nonsense like that. As it runs it becomes more accurate.

---

### Post by ccfiel on 2010-05-07
Hello Guys,

Can someone confirm this bug in xps m1330. [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/553687]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/553687"). Thanks!

chris

---

### Post by x C0MMAND0 x on 2010-05-09
I have never had hibernate work on my XPS M1330, only suspend.  I have not tried it in Lucid,yet.

---

### Post by ccfiel on 2010-05-12
Commando,

does suspend in lucid work in xps m1330?


chris

> **x C0MMAND0 x said:**
> I have never had hibernate work on my XPS M1330, only suspend.  I have not tried it in Lucid,yet.

---

### Post by korvins on 2010-05-15
Hi 

I can confirm that Hibernate and Suspend are not working with Lucid after an upgrade from Karmic. 

Hibernate option disappeared and suspend simply blocks the screen. 

Please fix this, since it is a very annoying regression.

---

### Post by ccfiel on 2010-05-16
that's bad :( hope it will be fix. 

> **korvins said:**
> Hi 

I can confirm that Hibernate and Suspend are not working with Lucid after an upgrade from Karmic. 

Hibernate option disappeared and suspend simply blocks the screen. 

Please fix this, since it is a very annoying regression.

---

### Post by ceasol on 2010-05-17
Suspend and Hibernate in my Dell XPS M1330 work's like a charm (Ubuntu 10.04)

No special configurations... My Laptop did come with Dell's Ubuntu 7.10 and I'm just doing upgrades, never a new "clean" installation.

My only issues (so far) are:
When Ubuntu start I have all the consoles messages and not the nice Ubuntu purple screen.
The video card's fan start running fast and noisy but after a couple of minutes stops.

---

### Post by GeoMX on 2010-05-22
> **ceasol said:**
> Suspend and Hibernate in my Dell XPS M1330 work's like a charm (Ubuntu 10.04)

No special configurations... My Laptop did come with Dell's Ubuntu 7.10 and I'm just doing upgrades, never a new "clean" installation.
I have a XPS M1330 too (clean install of Ubuntu 10.04), but have these issues:
[list]
[*]Brightness OSD does not work correctly, if rasing its level once and then lowering it, the OSD would show two rasing steps, not one and a lowering one. It happens the other way around. Brightness adjusts correctly, just the OSD is the one that don't.
[*]Volume changes too fast when using multimedia volume keys.
[*]Boot screen has low resolution.
[/list]

> **ceasol said:**
> 
My only issues (so far) are:
When Ubuntu start I have all the consoles messages and not the nice Ubuntu purple screen.
Does it appear for a moment or not at all? You can try this:
```

$ sudo gedit /etc/initramfs-tools/conf.d/splash

```
Add this text to the file:
FRAMEBUFFER=y
Save it and update initram:
```

$ sudo update-initramfs -u

```
Reboot to test it.

If you can see the boot screen now, you have the explanation here:
[http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)

And an alternative to have this boot screen in full resolution:
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by psychosibes on 2010-05-26
Hi, Upgraded (not clean install) from 8.04.4 a few days ago to 10.04 and everything seems to be working fine,..suspend, wifi, usb, bluetooth, SD card reader and all applications. I even have my wifi light on now! The only issue i have found is with Skype and that the menu text is the same colour as the menu background until you move the pointer over it, then that option becomes highlighted. All in all, I am very very pleased.

I am running the 32 bit version on a 2007, Dell XPS M1330, not dual booting.

Excellent job!

:P

---

### Post by x C0MMAND0 x on 2010-05-26
For the volume step, try this: 

1. Open up gconf-editor
2. Go to apps > gnome-settings-daemon
3. Change volume_step as needed.  I tried 3.

That fix worked for me in Jaunty, I don't know if it is still the same in Lucid.

---

### Post by GeoMX on 2010-05-29
I checked it and found that the step was set to 6 :p, thanks for the info :).

---

### Post by neeraj2608 on 2010-06-01
> **korvins said:**
> 
Hibernate option disappeared

This happened to me too and I was stumped until I discovered that my swap partition under Karmic was no longer being loaded in Lucid.

Forgot to mention: I don't own an XPS. Just mentioned it in case you have a similar problem.

---

### Post by x C0MMAND0 x on 2010-06-01
> **GeoMX said:**
> I checked it and found that the step was set to 6 :p, thanks for the info :).

Glad that worked for you.

---

### Post by soderstrom on 2010-06-06
> **gear.h34d.2012 said:**
> I have an XPS M1530, the rig one step up from the M1330, and in both Karmic and Lucid everything works flawlessly. Never had an issue. Keep in mind that I'm running 32-bit, however.

Everything works fine with 32-bit version? Then I shall try it because I've been using the 64-bit version of Lucid Lynx now for a while and have to admit that not everything works like it should. Wifi connection interrupts often and is weak. Also had frequent system crash and freezing, bad usage of memory and GTK+ doesn't always start correctly, but overall I am pleased with Ubuntu and currently trying to make the rest of the family and friends to try it as well. But guess it's better to recommend 32-bit version to start with ;)

Was gonna ask if it's possible to save all settings in my current system before changing to 32-bit? I spent hours setting up my system and finding good software to use, so don't wanna do that all over again.

---

### Post by florianderouck on 2010-06-11
I have some other troubles with this setup.

My Wifi works but it tends to cut me off each 5 minutes.
My battery life indicator doens't work at all and my battery lasts about half long @ ubuntu then on my windows 7 boot.

---

### Post by psychosibes on 2010-06-12
Two weeks on from my last post and to say that everything I use on 10.04 is still working (except the Skype menu colours) flawlessly. For the first time ever I can say that. No crashes, no freezes, no errors. Wow!

---

### Post by louisiana84 on 2010-06-27
I own 2 XPS m1330s and upgraded both to 10.04 from 9.10. I've got disappearing icons on the panel (volume hasn't shown in two weeks, sometimes the battery doesn't display) and there is often some weird looking artifacts on boot-up. Otherwise, I'm happy.

---

### Post by xavlours on 2010-06-28
I have a 32bit with Nvidia xps 1330 with the A15 bios (I think it's the latest), I've used all ubuntu versions since Gutsy.

Working:
Suspend/hibernate works.
Webcam, sound/mic (skype) works out of the box.
Touch keys for sound and player, remote and wifi/capslock indicators work out of the box.

Problems:
The theme with dark backgrounds makes a few menus unreadable (Skype in particular).

I have problems with the fingerprint reader. It worked in Karmic so I'm a bit disappointed. I can acquire and verify fingerprints, but I can't associate them to a user. Man pages say the kernel is involved so I gave up on that one.

NVidia drivers also cause the startup screen to be low resolution, this is a known problem. With the default drivers the startup screen is perfect but you can't have desktop effects.

About desktop effects, I believe using too much blur and cube effects contributed to frying my first GPU ([x1330 graphic cards problems]("http://en.community.dell.com/dell-blogs/b/direct2dell/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx")), but of course Windows, FPS and other 3D stuff were probably the main cause. Default desktop effects have never caused me trouble.

Summary:
I like Lucid a bit better than Karmic, except for the fingerprint reader.

---

### Post by geoffm on 2010-07-05
I clean-installed 10.04 on my XPS M1330. Everything is fine, except mic and fingerprint-reader still don't work, but they never did anyway. However, it's annoying because now I need to record something!

Did anyone have to play with the configs to get the mic working?

Oh and there still are annoying glitches with using 2 monitors and changing their relative position.

---

### Post by soderstrom on 2010-07-07
> **aw4lly said:**
> Hey guys,

I have the 1530 with Intel wireless card, I had a heap of trouble with this on 9.10, hoping to fix it with clean install. Has anyone tried this configuration?

Thanks

No reply on this. I also have allot of troubles with the intel wiress card. Someone else have it and have not experienced any issues with bluetooth and wifi cutting of? or weak connection? The list is long for me...

---

### Post by rbfthomas on 2010-09-15
I've an xps M1530 running 64-bit.  I've had no troubles with wireless that a reinstall of the network utility (network-manager) didn't fix.  

What I'm having persistent trouble with is the webcam.  Oddly, it *did* work in an earlier version, but since the upgrade to Lucid, it's stopped.  Oddly, the blue light will come on if I fire up Cheese or even Skype video, but nothing displays.  Anyone have any luck with the 64-bit on the xps M1530?

---

### Post by haemphyst on 2010-09-17
Running Lucid 64-bit on my m1330, (in-place upgrade from Karmic) Intel graphics, no issues whatsoever.

Bluetooth - works
Media buttons - works
Camera - works (Cheese is awesome)
Desktop effects - works
Audio - works
SD Reader - works with all cards so far.
HDMI - works with my 42" Aquos
Wireless - works
Remote control - works (somewhat, or mostly, depending on the app)

A15 BIOS, 8GB of RAM.  500GB Seagate 7200RPM 16MB cache hard drive.

From power-on to password screen <20seconds.  Win7 never came CLOSE to that kind of boot time.  From password to actually browsing the web?  Mmmm...  10, maybe 15 seconds.

Battery life is fantastic!  I have the high capacity battery, and I can easily go 3.5 to 4 hours, even with the 7.2K drive.  Plugging stuff into the USBs obviously shortens that, but I have been nothing but ecstatic with the performance and mobility of this combo.

Hibernate?  Don't use it, can't speak to it's capacity.  I set my PC to power off when I close my lid, which it does perfectly, every time.  Powers off when I hit the power button, as it should.

This was the best upgrade I've ever allowed to happen!

---

### Post by cogier on 2010-09-17
I am using a M1330 with 32 bit software. It works extremely well. I swapped the 160GB hard drive for a 40GB solid state drive and it boots in 22 seconds (to a USABLE desktop).

I have no issues I can think of. All the "extra" buttons, sound options, play, rewind etc, all work.

It works with 3G dongle using the very excellent Sakais3G. Compiz works well, there was one exception, I think it was "Reflection" than made the system unstable. I forget, but once I stopped using it all was well.

Unless you have a real reason to use the 64 bit software I suggest you don't. I tried it and all I got was problems.

Whatever, have fun with Ubuntu.

---

### Post by rykel on 2010-09-26
Hi, I just installed Ubuntu Lucid on a Dell XPS M1330 and the problem I have is with the wifi... it is able to see the networks, but it will NOT connect to any of them.

I tried changing the "generic-pae" kernel to "generic" but still no luck.

Please advise?

---

### Post by x C0MMAND0 x on 2010-11-23
My internal microphone does not work.  I can't believe I forgot to test it right away.  It doesn't even show up as a capture device in sound panel or in kmix.  Any ideas?

---

