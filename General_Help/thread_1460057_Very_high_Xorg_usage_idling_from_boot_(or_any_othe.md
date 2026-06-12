---
title: "Very high Xorg usage idling from boot (or any other time)"
date: 2010-04-22
forum: General Help
---

### Post by carn1x on 2010-04-22
From boot up with no applications loaded I get around 40-60% CPU load from Xorg in top, whilst in System Monitor, no process appears to be high CPU, however the usage graph indicates both cores dancing around between 40-70%.

I have an Acer 6930G which is:

Core 2 Duo 2Ghz
3Gb DDR2
Nvidia 9600M GS

I guess in my head I'm wondering if it's the nvidia drivers? I'm running the 185 drivers I think, or whichever are currently recommended by the OS. Is there better alternatives I should try?

I wouldn't mind except for the fact that the system seems very noticeably slow, and since I've only recently just converted from Windows as my dominant OS, I'm feeling somewhat disheartened and hope this can be fixed. I can handle formatting every 3 months as long as it keeps my system from performing sluggish!

Looked over the launchpad bugs, can't see anything that relates to my situation without some other conditions, sorry if I missed something.

Included JPG of system monitor and top in case there's any information gems there.

Please help!

Thanks for any advice :)

---

### Post by carn1x on 2010-04-22
Ok on the basis of:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/439138/comments/2](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/439138/comments/2)

I tried logging out and back in, and now Xorg usage seems to be down in top to under 10%. If I load System Monitor, Xorg usage in top goes up to 15%, and if I start moving the mouse around instigating animations etc, like the close/minimize/maximize button mouse overs, Xorg starts to rise up to 30%+, but dies back down again. Despite the seemingly low usage in top, System Monitor still seems to register 40-60% average usage on both cores. Also, the system still feels quit sluggish and many of the hover animations seem to skip frames or lag behind the mouse movement.

This is not the case on my Dell which has a Core Duo 1.6Ghz, 1Gb RAM, Intel GMA graphics which has, other than drivers, almost the exact same setup in terms of installed software and other things that might be loading in the background.

---

### Post by Archmage on 2010-04-22
What version are you using? If it is the 10.04 Beta - than you are at the wrong forum, since it is not stable yet (and the bug is already reported there).

---

### Post by carn1x on 2010-04-22
Sorry should have said, I'm on 9.10

---

### Post by klemes on 2010-04-22
Well admittedly this a slight problem.What can I tell ,on some machines Ubuntu and Linux in general, is better suited than on others as you 've already discovered so far with your two laptops.
On the basis of your problem now may I suggest to only use top and not the gnome-system-nonitor to assess the CPU activity as the later consumes far too many CPU cycles(18% CPU usage in your attached pictures).
The 37% of CPU usage your xorg consumes cannot be considered too high with compiz turned on and stuff like this but you say your laptop still feels  laggish so there must be a slight problem there.
I would suggest turning off unnecessary compiz plugins for the moment.
as for other drivers for your card besides the proprietary which in most cases work fine there is only the option of the open source nv driver which sadly offers no 3D acceleration so you will not be able to run compiz,and the option of nouveau drivers which I would not suggest at this phase of their development and in any case you shouldn't need to revert to those.
An other option would be to download the drivers appropriate for your card directly out from the NVIDIA site after uninstalling your current ones and give them a shot as they usually are more recent that the ones used in the official repos with important bugfixes in many cases and offering improved performance.
They offer a script for installation which you run as root with sh ./NVIDIA(rest_of_package_name) and the installation is most time relatively straightforward.Be warned though that you will need to install some packages in your system (most notably the kernel headers for your running kernel) but.the installer will give hints about what it needs to compile the nvidia kernel module needed by the driver.Also you must keep in mind that in every kernel upgrade you will have to repeat the installation procedure as thje driver depends from a module that has to be build every time for teh current kernel.
Do not be deterred though and go ahead if you feel you need the latest driver for your card....:guitar::)

---

### Post by carn1x on 2010-04-22
Cool, thanks for the comprehensive advice! I'll give the nvidia site drivers a whirl when I'm less likely to be interrupted! :D

---

### Post by carn1x on 2010-04-22
Well I seem to have screwed things up now :S

I flirted with runlevels and found out ubuntu seems to do things differently, although I didn't actually modify anything. I also read that CTRL ALT F1 / F2 can get you to command prompt away from X to install nvidia drivers.

So (after uninstalling the Nvidia drivers) I decided to check out CTRL ALT F1 / F2 to see what it was like. CTRL ALT F1 just took me to a black screen with with cursor, no text, and seemingly no PC activity or response to the keyboard, so I CTRL ALT F6 / F7 (can't remember which worked) and got back to X. 

So I thought I may as well try CTRL ALT F2 as well to see if that's any different. That went to a similar screen of black with white cursor, except this time there were a few small blocks of aqua with 999999 or ;:;:;;:; splodged a few times on the screen. 

Also CTRL ALT F6/7 did not get me back to X and no other key presses I could think of did anything, so like any good Windows user I forced shutdown by holding the power button.

Now when I reboot, it boots to desktop then after 5-10 seconds it automatically seems to go to this corrupted graphics stage of black screen with a bunch of 99999 or ;:;;:;;:; blocks all over it. I tried CTRL ALT F7 and it seemed to show the ubuntu desktop whilst still using the same low graphics text mode, but with streaks of the orange ubuntu background across it, and still with splodges of 9999 and :;:; blocks.

Can anybody help me back on the straight and narrow?

Thanks for rescuing me somebody!

---

### Post by carn1x on 2010-04-24
After a whole bunch of issues preventing me from trying the advice of this thread, I finally got around to installing the 195.x drivers from Nvidia's site, although I have actually reinstalled Ubuntu as well to get to this point >_< so I guess I won't know if the 195.x solved the problem, or if it was some other aspect.

Either way, CPU usage is now rock bottom :) Thanks!

---

### Post by klemes on 2010-04-24
Cool, glad you've fixed it.
Note:you do not have to mess with runlevels to install the nvidia driver package.
One way to disable X from running in Ubuntu is 
sudo /etc/init.d/gdm stop ,from a terminal and off you go.

The nvidia installer will complain but when you confirm it will proceed with the installation.
Keep it in mind for next time.
And as far as I am concerned the nvidia driver package is possibly the only only valid reason for me to install a package without the aid of the Debian package manager(apt,aptitude,Synaptic) in Ubuntu.

---

### Post by carn1x on 2010-04-24
Yeh I did gdm stop eventually! It installed without complaint, before I'd even run apt-get upgrade from a fresh install. I was expecting it to complain about dependencies.

---

### Post by klemes on 2010-04-24
Heard there were some overheating issues with the 195 series driver and the latest NVIDIA cards  but I guess it should have been fixed by now.Would not hurt to check though your card's temperature with lm-sensors or computertemp or any other utility you know of.

Edit: Yeap I checked the nvidia web site and they must have it fixed.There used to be a  warning there about 195 series drivers and possible overheating problems but now there is no more.

---

### Post by lumitoro on 2010-04-28
> **carn1x said:**
> Well I seem to have screwed things up now :S

I flirted with runlevels and found out ubuntu seems to do things differently, although I didn't actually modify anything. I also read that CTRL ALT F1 / F2 can get you to command prompt away from X to install nvidia drivers.

So (after uninstalling the Nvidia drivers) I decided to check out CTRL ALT F1 / F2 to see what it was like. CTRL ALT F1 just took me to a black screen with with cursor, no text, and seemingly no PC activity or response to the keyboard, so I CTRL ALT F6 / F7 (can't remember which worked) and got back to X. 

So I thought I may as well try CTRL ALT F2 as well to see if that's any different. That went to a similar screen of black with white cursor, except this time there were a few small blocks of aqua with 999999 or ;:;:;;:; splodged a few times on the screen. 

Also CTRL ALT F6/7 did not get me back to X and no other key presses I could think of did anything, so like any good Windows user I forced shutdown by holding the power button.

Now when I reboot, it boots to desktop then after 5-10 seconds it automatically seems to go to this corrupted graphics stage of black screen with a bunch of 99999 or ;:;;:;;:; blocks all over it. I tried CTRL ALT F7 and it seemed to show the ubuntu desktop whilst still using the same low graphics text mode, but with streaks of the orange ubuntu background across it, and still with splodges of 9999 and :;:; blocks.

Can anybody help me back on the straight and narrow?

Thanks for rescuing me somebody!

Looks like you have solved your problem. I crossed this very same problem when I upgraded from "kde 4.3.5" to "kde 4.4.2" and I also installed the latest nvidia binaries from some helpful ppa following great directions from a thread in this(ubuntuforuns.org) forum that I don't remember the link(sorry...my bad).
What cough my attention was the fact that you didn't know why [CTRL][ALT][F1] gave you a command line interface(CLI).
A good thing(some might say that it's not that good) about linux distributions is that the graphical interface that you are used to run in have a failsafe. Linux systems are based in a terminal just like the old UNIX and DOS, both were command line interfaces only. Microsoft decided to go fully graphical but *nix distros decided that it would be more stable to continue with the graphical over CLI (This is not a fact but i believe it is accurate so please correct me if I'm wrong.), so when you use [CTRL][ALT][F1] you are actually accessing the terminal (CLI) interface so that if your xorg(xserver) freezes you can still solve the problem in hand or just restart your xorg without restarting your machine. I used this to solve many problems with my graphics boards many times. There is no need to be proficient with CLI, but if you like to try new things you should try to find a way to backtrack your endeavorers with this failsafe feature before you actually try them.
That being said, i hope i didn't misread your post and just said things that you already knew. 

...wow, i just wrote this and i already now that my post is not helpful...
Try to boot into system rescue mode(i don't know exactly the key to bring up the grub boot screen) and uninstall any graphics driver that you installed previously in your system. Now rename you /etc/X11/xorg.conf to /etc/X11/[whatever you like, it's just a backup name] and restart. This should force xorg to create a standard xorg.conf and bring up graphical interface with low resolution. If this doesn't start xorg(your graphical interface) then you should consider hardware malfunction. Not much help again, so sorry, it's the best i can do...

bye

P.S.: [CTRL][ALT][F7] and [CTRL][ALT][F8] are usually the terminal's where Xorg starts.

---

