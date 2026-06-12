---
title: "Upgrade to 10.10 caused slow graphics problem : intel mobile chipset"
date: 2010-10-13
forum: General Help
---

### Post by ravi.xolve on 2010-10-13
I upgraded from version 10.04 to 10.10. I have got this slow graphics problem a lot. And this doesn't need to happen all the time. Here are some of the events that I noticed:

1. Video plays using mplayer and vlc are like slideshows with unsteady sound. But a fe w they do play ok for say 10 minutes or so. This happens with the flash videos in FIrefox too (using adobe flash plugin)

2. While typing on the Konsole or in a text box the update of the type to the screen sometimes is very slow. And I can't tell why but is does happen many times that the repetition of the keyboard doesn't happen. shell commands are executed very slow.

3. Scrolling up and down in the firefox shows artifacts and the screen is not updated wholly.

I total the computer is not so responsive as it used to be. My laptop is Core 2 duo with 3 GiB RAM. Following is the output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

```

In short my VGA controller is: 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Can you please help.

---

### Post by ravi.xolve on 2010-10-14
Ok more observations and I can tell you all guys (and gals ;-) ) that  this is not the problem with the X.org alone. Even while playing music  in the Amarok it gets hiccups.

And on console also the input becomes laggy. I tried turning off the KWin effects to no help.

My laptop is Lenovo G550.

---

### Post by martin_w on 2010-10-14
I've been using Ubuntu for a while now and had absolutely 0 issues.  Decided to install Kubuntu 10.10 which has cause numerous graphics  related issues. I've  got a DELL Latitude E6500  with an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07). If I can't resolve  this, will probably go to Ubuntu 10.10 or 10.04 which was perfect.

Pitty, as I'm liking it otherwise....

---

### Post by ravi.xolve on 2010-10-15
> **martin_w said:**
> I've  got a DELL Latitude E6500  with an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07). If I can't resolve  this, will probably go to Ubuntu 10.10 or 10.04 which was perfect.
Pitty, as I'm liking it otherwise....

So this is with KDE only? I suspect otherwise. Because audio need not be shaggy. The non-KDE applications should have been working fine.

---

### Post by CesarOscar on 2010-10-15
I am using gnome and my graphics issues are compiz related, neither the effects nor the compiz options works. I have read of many gde users having the same issue. It is not secluded to a single desktop environment

---

### Post by xanadux on 2010-10-15
I found a solution on this page: [http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/](http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/)

You need to make edits to ~/.kde/share/config/kwinrc under the sections  [Blacklist][Blur], [Blacklist][Lanczos], and to the line OpenGLIsUnsafe=true (change to false).

Good luck!

Here is the relevant information:

hsantanna               [October 13, 2010 at 14:43]("http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/#comment-312")

                   You have to edit ~/.kde/share/config/kwinrc
 

At the lines [Blacklist][Blur] and [Blacklist][Lanczos] you have to add your GPU.
 This will disable the advanced features that those bugged drivers don’t support.
 To know what you have to add (driver description), paste this on terminal:
 echo “`glxinfo | grep ‘OpenGL renderer string’ | sed -e ‘s/^.*:  //’`:-:`glxinfo | grep ‘OpenGL version string’ | sed -e ‘s/^.*: //’`”
 

The result is something like this:
 Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
 

Copy and paste the entire line.
 In my case, I have 2 graphics cards Intel/ATI (switchable)
 I added both at ~/.kde/share/config/kwinrc
 with resulted on this:
 [Blacklist][Blur]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2,Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
Ati=Radeon HD 3650:-:3.3.9901
NVIDIA=GeForce 6150/PCI/SSE2:-:195
 

[Blacklist][Lanczos]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2,Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
Intel=GM45 Express Chipset GEM 20100328:-:7.8.2,GM45 Express Chipset GEM  20091221:-:7.7.1,965GM GEM 20100328 2010Q1:-:7.8.2,965GM GEM 20091221  2009Q4:-:7.7.1,Ironlake Mobile GEM 20100328:-:7.8.2,Mesa DRI Intel(R)  Ironlake Mobile GEM 20100330 DEVELOPMENT :-:2.1 Mesa 7.10-devel
 

Note that already was some drivers there before I added mine. 
 If you do this, everything will work pretty much well.
 Both, my Intel Arrandale (from i5) and my Radeon Mobility HD 4550 are working good with almost all effects enabled.
(There are one or another that cause problems so i disabled those.)
 

Ah, I have to say that if you can’t enable effects anymore because  the option is disabled on KDE, you have also to edit  ~/.kde/share/config/kwinrc and change OpenGLIsUnsafe=true to false.

---

### Post by ravi.xolve on 2010-10-16
Right now I am using xfwm4 (XFCE window manager) and the problem of jittery graphics is not solved. e.g. while changing the menus in application menu of KDE I still get the jitters. I suspect the problem is elsewhere.

Also I have noticed high CPU usage if I turn on Kwin effects.

---

### Post by james_xxx on 2010-10-16
When I try running:

```
echo “`glxinfo | grep ‘OpenGL renderer string’ | sed -e ‘s/^.*: //’`:-:`glxinfo | grep ‘OpenGL version string’ | sed -e ‘s/^.*: //’`”
```

I get this:

```
grep: renderer: No such file or directory
grep: string’: No such file or directory
sed: -e expression #1, char 1: unknown command: `&#65533;'
grep: version: No such file or directory
grep: string’: No such file or directory
sed: -e expression #1, char 1: unknown command: `&#65533;'
“:-:”
```

Any suggestions?

---

### Post by ravi.xolve on 2010-10-16
Are you copying and pasting into console. Magically its not happening as expected.

Try this:

glxinfo | grep 'OpenGL renderer string'

---

### Post by ravi.xolve on 2010-10-16
Any ideas why this is happening? To keep KWin out of my way I am running xfwm4 (XFCE window manager) and running mplayer. Again a slide show type video output with jittery audio.

---

### Post by Rendsvig on 2010-10-17
I have experienced jerky video playback and audio after upgrading to 10.10 as well. Slight lack in typing. I'm on a Lenovo X301.

---

### Post by hsantanna on 2010-10-19
seems that the echo command was brooked by the blog engine.. the problem is those " '``' "

here is a link to the correctly formated echo command:

[http://paste.ubuntu.com/516514/](http://paste.ubuntu.com/516514/)


> **james_xxx said:**
> When I try running:

```
echo “`glxinfo | grep ‘OpenGL renderer string’ | sed -e ‘s/^.*: //’`:-:`glxinfo | grep ‘OpenGL version string’ | sed -e ‘s/^.*: //’`”
```

I get this:

```
grep: renderer: No such file or directory
grep: string’: No such file or directory
sed: -e expression #1, char 1: unknown command: `&#65533;'
grep: version: No such file or directory
grep: string’: No such file or directory
sed: -e expression #1, char 1: unknown command: `&#65533;'
“:-:”
```

Any suggestions?

---

### Post by joe1600 on 2010-10-19
> **hsantanna said:**
> seems that the echo command was brooked by the blog engine.. the problem is those " '``' "

here is a link to the correctly formated echo command:

[http://paste.ubuntu.com/516514/](http://paste.ubuntu.com/516514/)


OUTPUT WHAT I GET HELP

Software Rasterizer:-:2.1 Mesa 7.9-devel

---

### Post by AfterCrash on 2010-10-22
> **ravi.xolve said:**
> Are you copying and pasting into console. Magically its not happening as expected.

Try this:

glxinfo | grep 'OpenGL renderer string'

Hi my name is Brandon. I just installed Ubuntu 10.10 on my Toshiba l350 satellite laptop. I have a Intel Mobile 4 Chip-set. Before this installation I was using windows 7 and hap perfect graphics. I play a game called Quake Live. [www.QuakeLive.com](www.QuakeLive.com). Its a free FPS game. Now that I have moved over to Linux I am experiencing poor frames per second, lag in game, graphics are all messed up. I entered this into my terminal: 

glxinfo | grep 'OpenGL renderer string'

my return was:

afterburn@afterburn-workstation:~$ glxinfo | grep 'OpenGL renderer string'

OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

afterburn@afterburn-workstation:~$ 

Im not real experienced with Linux. But I am a computer geek and with the right direction I could solve this. Can anyone help me ? I've searched many forums. And I haven't found a solution..

Thanks for any help!

- Brandon.

---

### Post by Calorus on 2010-10-23
Yah, just to clarify, this isn't a Kubuntu only issue, it's a Meerkat wide problem. I'm having the same issue on a Lenovo X200. All help appreciated.

---

### Post by wieman01 on 2010-10-23
This is extremely disturbing... I got the same issue as the OP described on two laptop PCs with Intel Mobile Chipsets. Every upgrade comes with its own set of problems, and they tend to get nastier with each upgrade. We cannot even watch videos anymore. This is a sad state of affairs.

---

### Post by puzatik on 2010-10-23
> **xanadux said:**
> I found a solution on this page: [http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/](http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/)

You need to make edits to ~/.kde/share/config/kwinrc under the sections  [Blacklist][Blur], [Blacklist][Lanczos], and to the line OpenGLIsUnsafe=true (change to false).

Good luck!

Here is the relevant information:

hsantanna               [October 13, 2010 at 14:43]("http://skitterman.wordpress.com/2010/09/05/look-before-you-leap-kubuntu-maverick/#comment-312")

                   You have to edit ~/.kde/share/config/kwinrc
 

At the lines [Blacklist][Blur] and [Blacklist][Lanczos] you have to add your GPU.
 This will disable the advanced features that those bugged drivers don’t support.
 To know what you have to add (driver description), paste this on terminal:
 echo “`glxinfo | grep ‘OpenGL renderer string’ | sed -e ‘s/^.*:  //’`:-:`glxinfo | grep ‘OpenGL version string’ | sed -e ‘s/^.*: //’`”
 

The result is something like this:
 Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
 

Copy and paste the entire line.
 In my case, I have 2 graphics cards Intel/ATI (switchable)
 I added both at ~/.kde/share/config/kwinrc
 with resulted on this:
 [Blacklist][Blur]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2,Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
Ati=Radeon HD 3650:-:3.3.9901
NVIDIA=GeForce 6150/PCI/SSE2:-:195
 

[Blacklist][Lanczos]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2,Mesa DRI R600 (RV710 9555) 20090101  TCL DRI2:-:2.1 Mesa 7.10-devel
Intel=GM45 Express Chipset GEM 20100328:-:7.8.2,GM45 Express Chipset GEM  20091221:-:7.7.1,965GM GEM 20100328 2010Q1:-:7.8.2,965GM GEM 20091221  2009Q4:-:7.7.1,Ironlake Mobile GEM 20100328:-:7.8.2,Mesa DRI Intel(R)  Ironlake Mobile GEM 20100330 DEVELOPMENT :-:2.1 Mesa 7.10-devel
 

Note that already was some drivers there before I added mine. 
 If you do this, everything will work pretty much well.
 Both, my Intel Arrandale (from i5) and my Radeon Mobility HD 4550 are working good with almost all effects enabled.
(There are one or another that cause problems so i disabled those.)
 

Ah, I have to say that if you can’t enable effects anymore because  the option is disabled on KDE, you have also to edit  ~/.kde/share/config/kwinrc and change OpenGLIsUnsafe=true to false.


THANK YOU VERY MUCH!!! It has helped me. Guys, you should replace symbol ‘ with ' and all this scripts will work...

---

### Post by ravi.xolve on 2010-10-24
I upgraded to the new kernel update available through apt-get. Still on the same problem.

For KDE users: I installed compiz and I found that its lot more compatible to KDE than before. The general responsiveness of the system increased. And its effects are smoother than those of kwin.

---

### Post by SwissBushIndian on 2010-10-24
> **ravi.xolve said:**
> I upgraded to the new kernel update available through apt-get. Still on the same problem.

For KDE users: I installed compiz and I found that its lot more compatible to KDE than before. The general responsiveness of the system increased. And its effects are smoother than those of kwin.

And does compiz eliminate any of the problems you experianced before? Or is it just a general note? Because I still have problems with Kwin as well as compiz, although they're not always the same. Kwin has more problems with text-buildup, while compiz spazzes out on video-playback.

---

### Post by wieman01 on 2010-10-24
Interesting observation... During network activity I can play video without a problem, not lagging whatsoever. When I turn wireless off, same old problem.

So when I ping Google via command line while I watch videos, everything works flawlessly. Could someone else try please and report back?

This could also be due to aggressive CPU scaling?

---

### Post by ravi.xolve on 2010-10-25
@[SwissBushIndian]("http://ubuntuforums.org/member.php?u=199270") No it doesn't.

---

### Post by SwissBushIndian on 2010-10-25
> **ravi.xolve said:**
> @[SwissBushIndian]("http://ubuntuforums.org/member.php?u=199270") No it doesn't.

Allright.

Well, I haven't had much time since my last post. I have noticed one thing thought: What causes the most problems for me is GTK. 95% of the rendering errors I get are in GTK apps, which for me is: Eiffel Studio, Firefox and Thunderbird. This obviously puts me off quite a bit, as this is my stable (or at least, was until now) production system. I guess I have no other choice than to delve into this as soon as I get time. But I'm still hoping an update will fix most of this by then...

Edit: I use KDE, hence I've been able to figure out what's causing most of the breakage. QT is just fine, except for a few hickups with 3D rendering, but I'm attesting that to my old graphics and the intel-drivers. I can totally live with that. What I can't really live with is having some of my most used software going bezerk on me.

Hoping someone else will have come to a similar conclusion so that I'm not the only one out there :D

---

### Post by ravi.xolve on 2010-10-29
It says that 2.6.35 has some slow IO problems. Take a look at point 4.

[http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-36-1103009.html?page=6](http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-36-1103009.html?page=6)

---

### Post by wieman01 on 2010-11-01
I just upgraded to 2.6.36 RC8 and all problems seem to have disappeared. I can watch videos and all just fine.

If anyone does not know how to upgrade the kernel, let me know.

---

### Post by ravi.xolve on 2010-11-02
@wieman01 Is it available in repos?

---

### Post by wieman01 on 2010-11-02
> **ravi.xolve said:**
> @wieman01 Is it available in repos?
No, unfortunately not. You will need to download the headers and the kernel image and install both of them. 

In case anyone needs further instructions, let me know and I'll summarize them for you.

---

### Post by cozmicharlie on 2010-11-02
> **wieman01 said:**
> 
In case anyone needs further instructions, let me know and I'll summarize them for you.

Please do - that would be very helpful.  I have had nothing but problems with 2.6.32-25

---

### Post by wieman01 on 2010-11-02
Alright, let's give this a try... Open a terminal and install the headers first:
```
wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-rc1-maverick/linux-headers-2.6.37-020637rc1_2.6.37-020637rc1.201011020905_all.deb
sudo dpkg -i linux-headers-2.6.37-020637rc1_2.6.37-020637rc1.201011020905_all.deb
```
Now decide what type of CPU you have got and install the image:

_**AMD64:**_
```
wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-rc7-maverick/linux-image-2.6.36-020636rc7-generic_2.6.36-020636rc7.201010070908_amd64.deb
sudo dpkg -i linux-image-2.6.36-020636rc7-generic_2.6.36-020636rc7.201010070908_amd64.deb
```
_**Other CPUs:**_
```
wget http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-rc7-maverick/linux-image-2.6.36-020636rc7-generic_2.6.36-020636rc7.201010070908_i386.deb
sudo dpkg -i linux-image-2.6.36-020636rc7-generic_2.6.36-020636rc7.201010070908_i386.deb
```
Then reboot your system. You should be ready to go. You cannot do much damage if you don't know what sort of CPU you got, the system won't let you install an incompatible package anyway.

You find the latest kernels [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

---

### Post by SwissBushIndian on 2010-11-02
This is just a small warning, because I would usually suspect everybody of taking this step to know that they're doing. The new kernel is, pretty much, from the testing branch (which is, at this moment, pre-natty-narwal alpha), and could therefor cause problems. Going back to the old kernel is no problem.

I've tried this before, compiling the kernel for myself directly from linus' sources, and it hasn't fixed my ff problems, so atm my biggest concern is the intel drivers. I'm going to test the debs these days, but still wondering if I'm the only one with gtk issues in KDE.

---

### Post by wieman01 on 2010-11-03
> **SwissBushIndian said:**
> This is just a small warning, because I would usually suspect everybody of taking this step to know that they're doing. The new kernel is, pretty much, from the testing branch (which is, at this moment, pre-natty-narwal alpha), and could therefor cause problems. Going back to the old kernel is no problem.

I've tried this before, compiling the kernel for myself directly from linus' sources, and it hasn't fixed my ff problems, so atm my biggest concern is the intel drivers. I'm going to test the debs these days, but still wondering if I'm the only one with gtk issues in KDE.
It's true, there is a risk involved which I missed to mention. But luckily you don't have to compile from source yourself and just install the DEB's. I wish I would have had an option... But the upgrade worked out.

---

### Post by SwissBushIndian on 2010-11-07
Unless you're fast enough for no debs being around ;) Compiling a kernel isn't that much of a hassle anyway. But, in retrospect, not worth any effort if you're still dragging around the same old problems.

---

### Post by ravi.xolve on 2010-11-13
I upgraded to new kernel update available from the apt-get : linux-image-2.6.35-22-generic but i still get the same buggy performance. whats your report people.

---

### Post by wieman01 on 2010-11-14
> **ravi.xolve said:**
> I upgraded to new kernel update available from the apt-get : linux-image-2.6.35-22-generic but i still get the same buggy performance. whats your report people.
A manual upgrade to higher versions resolves this problem however.

---

### Post by ravi.xolve on 2010-11-15
> **wieman01 said:**
> Interesting observation... During network activity I can play video without a problem, not lagging whatsoever. When I turn wireless off, same old problem.

So when I ping Google via command line while I watch videos, everything works flawlessly. Could someone else try please and report back?

This could also be due to aggressive CPU scaling?

I found any IO can make your PC look good. If I continuously press arbitrary keys or keep moving the mouse the system keeps reponding. Looks like some problem with the IO interrupts, :rolleyes:
And now I have to just continuously tap the keys for the system to shutdown. 

I will be upgrading to the new kernel and will tell how it happ

---

### Post by wieman01 on 2010-11-15
> **ravi.xolve said:**
> I found any IO can make your PC look good. If I continuously press arbitrary keys or keep moving the mouse the system keeps reponding. Looks like some problem with the IO interrupts, :rolleyes:
And now I have to just continuously tap the keys for the system to shutdown. 

I will be upgrading to the new kernel and will tell how it happ
That is correct, I noticed the same thing. I move the cursor, all videos work fine.

An kernel upgrade should do the job.

---

### Post by ravi.xolve on 2010-11-15
From:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc1-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc1-maverick/)

I installed the kernel 2.6.37-rc1 i386 version. Its working fine except with graphics at some point being redrawn incorrectly. e.g. firefox address bar, KDE tas bar, amarok playlist album covers; all go by some move movement over them (they are repainted ofcourse).

I couldn't install headers because there was dependency problem. I think cyclic dependency. But at least no jerkiness.

---

### Post by VAB on 2010-11-15
My resort is if it works don't touch it! not even to mention upgrade.
An upgrade is not necessarily better. So I retreat and go back to the version it was working. ubuntu is not what it used to be similar problems with graphics were solved only by downgrading. sad but so it is.

---

### Post by ravi.xolve on 2010-11-21
@VAB

"lower version" thats the point. I just downgraded the kernel to version 2.6.32 and its cool. Working all fine!

---

### Post by bigbrovar on 2010-12-24
> **ravi.xolve said:**
> @VAB

"lower version" thats the point. I just downgraded the kernel to version 2.6.32 and its cool. Working all fine!
I am having this problem too and it can be quite an annoyance. Can you share how you were able to downgrade your kernel to 2.6.32?

---

### Post by ravi.xolve on 2010-12-25
@bigbrovar

From the link you can download the debs of [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) download the kernel 2.6.32 .

Install kernel image, genenal headers (suffixed by all) and platform specific headers (suffixed by your platform e.g. i386)

---

### Post by ianbrown75 on 2010-12-30
not sure how to explain this because i am kinda a noob, or at least not a linux expert. anyways. I up dated to natty narwal from 10.04. now my one game that i play online will not work. it is quakelive. I am not having anyhelp from them, I am hoping that this community would be a little more friendly. The game runs, but th FPS(frames per second) are really low, and the sound is choppy. I am figuing that this is a video card issue, but i am not seeing any threads on my laptop. it is a toshiba satellite a105 s4201. not sure how to find the graphics card, or any other information. so if you can help, let me know..

---

### Post by ravi.xolve on 2010-12-31
Please tell your kernel version: Use this command:

```
uname -a
```

and paste the output.

Also tell your graphics chip. Use the command

```
lspci | grep 'VGA'
```

and paste the output.

---

### Post by dcstar on 2010-12-31
> **ianbrown75 said:**
> not sure how to explain this because i am kinda a noob, or at least not a linux expert. anyways. I up dated to natty narwal from 10.04. now my one game that i play online will not work. it is quakelive. I am not having anyhelp from them, I am hoping that this community would be a little more friendly. The game runs, but th FPS(frames per second) are really low, and the sound is choppy. I am figuing that this is a video card issue, but i am not seeing any threads on my laptop. it is a **toshiba satellite a105** s4201. not sure how to find the graphics card, or any other information. so if you can help, let me know..

**Intel GMA 950**

[http://ubuntuforums.org/showthread.php?t=1103916](http://ubuntuforums.org/showthread.php?t=1103916)

---

