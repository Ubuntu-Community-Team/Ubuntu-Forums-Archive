---
title: "Ubuntu CD won't boot on AMD A8-3850 APU"
date: 2011-11-25
forum: General Help
---

### Post by dntc0x on 2011-11-25
I tried searching a few times without success on the following:

I've made a cd of ubuntu 11.10, but it won't boot on an AMD A8-3850 APU with the Radeon HD6550D video.

I have an older Sony LCD monitor, but I can't find the model number (it came with an older sony pc that was several years old). Win7 uses a "Generic PnP Monitor" driver fine, but it doesn't show the model number either

When I reboot the pc in order to cd boot ubuntu, I see a small icon at the bottom of the screen for a few moments after the bios screen. If I press enter while the icon is up, I get some menus for language and some other options that are obviously 'linux' based.

However, regardless of whether I go through that menu or not, my display goes dark (sleep/standby) with the amber light. I suspect that the OS is not properly initiating the video section of the APU.

I've explored the cd in Win7 (installed OS), and it seems to have the appropriate number of folders, etc.

I'm sure that I'm not the only one that this has happened to, but I can't seem to find a solution in existing forums.

I've tried using ubuntu from cd in the past, and always have a problem where it won't boot, or it won't access the network for internet, etc.

I'm interested in checking out ubuntu, but every time that I've tried it never works. I don't want to "install" it unless I think that it is worth it.

If someone has some fairly simple things to try, I'd appreciate it. But for all the claims of ubuntu being "easy", it never has been for me, at least in booting from cd.

Thanks!

---

### Post by dcstar on 2011-11-26
> **dntc0x said:**
> I tried searching a few times without success on the following:

I've made a cd of ubuntu 11.10, but it won't boot on an AMD A8-3850 APU with the Radeon HD6550D video.

I have an older Sony LCD monitor, but I can't find the model number (it came with an older sony pc that was several years old). Win7 uses a "Generic PnP Monitor" driver fine, but it doesn't show the model number either

When I reboot the pc in order to cd boot ubuntu, I see a small icon at the bottom of the screen for a few moments after the bios screen. If I press enter while the icon is up, I get some menus for language and some other options that are obviously 'linux' based.

However, regardless of whether I go through that menu or not, my display goes dark (sleep/standby) with the amber light.
.........

How long do **you** wait?

---

### Post by robert shearer on 2011-11-26
> When I reboot the pc in order to cd boot ubuntu, I see a small icon at the bottom of the screen for a few moments after the bios screen. If I press enter while the icon is up, I get some menus for language and some other options that are obviously 'linux' based.

When you reach this point hit F6 and arrow down to "nomodeset' and hit enter to put a check in the box next to it.
do the same for "nodmraid" then hit **esc** and then **enter** to continue booting.

if this does not work, reboot, do the above again but after esc then use **backspace** to remove '-quietsplash' from the line at the bottom of the screen and hit enter...you will then get a series of text lines and when/if the live cd stops you can copy the line it stopped on and post here to give some more targeted info..:)

First guess is a graphics card problem and you may want to try the alternate install cd, however this pre-supposes a level of linux knowledge you may not be comfortable with..:(

> But for all the claims of ubuntu being "easy", it never has been for me, at least in booting from cd.

This is most probably hardware related, other operating systems have these troubles too and it is not Ubuntu's fault, just as it is not Microsoft's fault nor Apples.
 It is more likely the lack of support for Open Source by one or more of the vendors of the **hardware** in your pc.
This is unfortunate but given that you purchased a pc to work with Windows in the first instance then it is understandable...:)

Keep at it and post back your progress, We are all keen to help you...:)

---

### Post by dntc0x on 2011-11-27
I waited several minutes after my monitor 'goes to sleep'. I noticed that the cd continues for a while, like maybe it's still reading. However, after a while the cd pretty much stops...but still no video.

---

### Post by dntc0x on 2011-11-28
> **robert shearer said:**
> [I]When you reach this point hit F6 and arrow down to "nomodeset' and hit enter to put a check in the box next to it.
do the same for "nodmraid" then hit **esc** and then **enter** to continue booting.[/I]

if this does not work, reboot, do the above again but after esc then use **backspace** to remove '-quietsplash' from the line at the bottom of the screen and hit enter...you will then get a series of text lines and when/if the live cd stops you can copy the line it stopped on and post here to give some more targeted info..:)

First guess is a graphics card problem and you may want to try the alternate install cd, however this pre-supposes a level of linux knowledge you may not be comfortable with..:(



This is most probably hardware related, other operating systems have these troubles too and it is not Ubuntu's fault, just as it is not Microsoft's fault nor Apples.
 It is more likely the lack of support for Open Source by one or more of the vendors of the **hardware** in your pc.
This is unfortunate but given that you purchased a pc to work with Windows in the first instance then it is understandable...:)

Keep at it and post back your progress, We are all keen to help you...:)

I did the first part [F6] in italics above. The cd booted to the linux equivalent of a command screen.

The relevant part of the screen read as follows:
[INDENT]To run a command as administrator (user "root"), use "sudo <command>"
See "man sudo_root" for details.

Ubuntu@ubuntu: ~$
[/INDENT]At least the monitor stayed on to the prompt.

I haven't tried removing the '-quietsplash' part. I figured that I'd tell you about the first part to see if you have more ideas

Thanks

---

### Post by robert shearer on 2011-11-29
Progress !...:)

Looks more and more a graphics card problem...
More info needed so do this...
boot as before and get to the 'command screen' showing the prompt..
```
Ubuntu@ubuntu: ~$
```
then type ...
```
lspci -nn | grep VGA
```
(note..the l in lspci is a **lower-case L** and  **|** is on the key with the backslash \ (below backspace key) use shift to get **|** )

then hit enter and the screen will printout some info about the graphics card then returns to the prompt(Ubuntu@ubuntu: ~$ ) .Copy that info and post back.

Next, while you are at that command line prompt type this and hit enter..
```
startx
```
and post back any info it returns.


Looks like driver support is the problem..
[http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2)

---

### Post by dntc0x on 2011-12-01
> **robert shearer said:**
> Progress !...:)

Looks more and more a graphics card problem...
More info needed so do this...
boot as before and get to the 'command screen' showing the prompt..
```
Ubuntu@ubuntu: ~$
```then type ...
```
lspci -nn | grep VGA
```(note..the l in lspci is a **lower-case L** and  **|** is on the key with the backslash \ (below backspace key) use shift to get **|** )

then hit enter and the screen will printout some info about the graphics card then returns to the prompt(Ubuntu@ubuntu: ~$ ) .Copy that info and post back.

Next, while you are at that command line prompt type this and hit enter..
```
startx
```and post back any info it returns.


Looks like driver support is the problem..
[http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2)

I did what you said and got the following:
[INDENT]Current version of Pixman

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 2 02:03:36 2011
(==) Using system config directory "usr/share/x11/Xorg.confid"
(EE) Failed to load file "fglrx" (module does not exist, 0)
(II) [KMS} drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
(EE) RADEON (0): chipset: "SUMO" (chipID= 0x9640) requires KMS
(EE) Screen(s) found, but none have a useable configuration.

Fatal server error:
No screens found

Please consult the TheX.org Foundation  [EMAIL="Support@http://wiki.X.org"]Support@http://wiki.X.org[/EMAIL]

Please also check the log file at "/var/log/Xorg.0.log"

ddxSigGiveUp: Closing log

xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

[/INDENT]It went back to the Ubuntu prompt and that's all.

After reading the phoronix.com forum it's apparent that the cd boot versions of ubuntu are not ready for this APU. 

I might check back in a few months to see if that problem has been fixed, but I'm far too busy to mess around with an install to my HD when I just wanted to try it out (not necessarily switch to it).

Thank you for your help.

---

### Post by tr333 on 2012-01-21
I've had success with connecting via the HDMI interface on my motherboard that has an A8-3850 APU. I haven't yet been able to get the VGA port working, except in recovery mode.

[http://pad.lv/908659](http://pad.lv/908659)

---

### Post by tr333 on 2012-01-21
Maybe you can try testing with the latest [daily-live delevopment ISO]("http://cdimage.ubuntu.com/daily-live/") for 12.04/precise.  You can use [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) or [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create a bootable USB disk from the ISO.

---

### Post by imachavel on 2012-01-21
> **tr333 said:**
> I've had success with connecting via the HDMI interface on my motherboard that has an A8-3850 APU. I haven't yet been able to get the VGA port working, except in recovery mode.

[http://pad.lv/908659](http://pad.lv/908659)

ok I know very very little about what everyone is talking about, except to say a few things:

1) (EE) open /dev/fb0: No such file or directory

does that not say something?

now 2) are you using onboard graphics or a video card installed in a pcie slot?

3) start x doesn't work that is a problem, start x is the command used to load the gui from the bash(or other shell) command line

4) you are booting to the live cd? yes you gave the lspci -nn | grep VGA results. Mine are:


  01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV730XT [Radeon HD 4670] [1002:9490]

I would say the gpu isn't loading at all. But you say you can get to the terminal line. So it's not so much the gpu isn't working, but that the driver isn't updated enough to get beyond the most basic frame rate pixelation gpu rendering. Meaning your graphics card might not be working. Please go to bios, look for your graphics adapter, tell us the settings, try different settings. 

Also, are you going to consider installing ubuntu or just to keep booting to the live cd? What is on the hard drive right now? Anything? I'm sorry I can't assist you further but yet it does sound like a hard ware problem. Maybe from the bios run a memory test. the command line terminal version of loading the OS file system in linux is the linux equivalent of 'safe mode' for windows. If I knew a command to check and try to install or reinstall the drivers for your gpu, I would give it to you. I don't. But if you look at your bios(f2 upon boot) it SHOULD explain a bit about your gpu, if you are using onboard, or another gpu. Does it detect automatically?

---

### Post by imachavel on 2012-01-21
> **tr333 said:**
> I've had success with connecting via the HDMI interface on my motherboard that has an A8-3850 APU. I haven't yet been able to get the VGA port working, except in recovery mode.

[http://pad.lv/908659](http://pad.lv/908659)

if you can get the hdmi working but not the vga to your monitor, then that is because your pixelation graphic rendering settings are TOO HIGH! not the other way around. Try lowering them then reconnect with your vga i/o adapter to your monitor. What OP is facing is a driver/software/ hard ware problem. Not the same as just what connector type being used. Also yes good idea if he can burn another cd maybe that is the problem. Windows iso magic or whatever it's called usually has a way to detect what speed the cd is being burnt at, I'd try lowest settings. Well best of luck!

---

### Post by tr333 on 2012-01-23
I managed to get the VGA to work by disabling KMS on startup with the "nomodeset" kernel parameter.  It works for me because I'm only running Ubuntu Server without a GUI, so I don't need high-resolution graphics.  From what I've read in other places on the internet, the KMS drivers aren't yet 100% complete for Llano chipsets (but I could be wrong on this).

With Ubuntu, you would normally start the "lightdm" service from the commandline instead of running "startx" as lightdm is the new X Display Manager, replacing the old GDM.

---

### Post by grhayes on 2012-02-20
I was running several older agp cards when ubuntu updated from 11.04 to 11.10 they stopped working and well frankly I hate unity KDE is better than unity so switched to kubuntu while running an nvidia card.

However, my mother boards died after 9 years of hard use on that system. Upgrade to an AMD A8-3850 APU it has the built in amd 6550d gpu on the same chip as the quad cpu. I noticed it also doesn't work with any of the 11.10 versions and works fine with the 11.04 version.

The issue is 100% with the drivers. They should have stayed with the older ones or at least made sure all the same hardware was supported before switching to the newer ones.

Its bad decisions and choices like these that prevent people who would probably migrate from windows into not doing so. I only use windows for occasional games. I won't even develop for it any more.

---

### Post by grhayes on 2012-02-20
A little messing around got the AMD A8-3850 system up and running last night with Ubuntu on it.
I went back and installed 11.04 since the graphics drivers there were not broken. I then installed the ati drivers. They however are not updated enough to cover the 6550d gpu in the A8-3850 it puts a nice little water mark on the bottom right corner of the screen to let you know this.

Don't worry about it though. Upgrade to 11.10 from that and it will automatically install the proprietary drivers. Those work from what I seen so far.

It probably would be easier to install 11.10 if I knew more about the command line options with ubuntu to direct it to install specific drivers vs the graphical interface.

---

