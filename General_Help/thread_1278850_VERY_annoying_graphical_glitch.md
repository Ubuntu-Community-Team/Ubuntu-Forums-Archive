---
title: "VERY annoying graphical glitch"
date: 2009-09-30
forum: General Help
---

### Post by baffle-boy on 2009-09-30
i just started using ubuntu. I burned the .iso to a cd, and installed it (as dual boot with windows XP) but whenever i try to use ubuntu, there is some VERY annoying horizontal  lines that constantly move down either side of the screen. they get longer and move a lot whenever i do something (like left clicking and drawing a box, or opening firefox) but stay relatively the same length if i do nothing. these do not show up in windows xp, any ideas what they are? or more importantly how to fix them?

---

### Post by Littleweseth on 2009-09-30
Hi;

What hardware are you using? More specifically, what exact kind of video adapter?

It may help us if you post the output of lspci; this will tell us *exactly* what kind of graphics adapter you have. Example :

```

caradoc vhosts.d # lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:01.0 RAID bus controller: LSI Logic / Symbios Logic 53C1510 (rev 02)
00:02.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
***00:03.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC 215IIC [Mach64 GT IIC] (rev 7a)***
00:04.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 51)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller


```

---

### Post by baffle-boy on 2009-09-30
eerrmmmm, yeah im not THAT technologically inclined, just above aerage, i suppose i could just open my computer up and see what it says... or is there a command prompt in XP to tell me about my graphics card? please explain how to do that.

---

### Post by LoneWolfJack on 2009-09-30
he wants you to type

```
lspci
```

in a console window and post the output ;)

---

### Post by akakingess on 2009-09-30
Just to be a little more specific, open up a terminal by going to Applications----->Accessories------->Terminal, and that will open up a terminal window into which you would type lspci and it will give you an output like Littleweseth posted. Then just copy and paste that output into your next post. Preferably using the code tags around it, when entering your post and when you are about to paste in your output click on the # sign and it will give you a  and just be sure to paste it in between those (makes it easier for us to read.

Edit: To be able to see the # sign as an option you have to choose go advanced down at the bottom of your post entry. I know I am going into way to much detail, but the more info you can give us, the better we can assist you.

---

### Post by baffle-boy on 2009-09-30
thank you all SO much for your help, i mat just get rid of ubuntu if the problem is becasue of my graphics card, but if it can be fixed by, say, an upgraded RAM... im going to get one anyways. well here is the output:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
owner@Mckay-Home:~$ 
```

---

### Post by akakingess on 2009-09-30
don't give up just yet, I am not an expert, but a lot of these guys on this forum are and if you remain patient, someone will be able to at least give you some ideas to try that may be a quick and easy fix, so just give it a day or two and see what kind of info comes into this thread. Stick in there and I think your issue will get resolved, but I would like to ask what are the specs on your computer (i.e. laptop, desktop, processor, RAM, and any other info that you can think to give us, because it may not just be your graphics card. Again, the more info we have, the more likely we (or at least the more knowledgeable guros) can help you.

---

### Post by baffle-boy on 2009-09-30
well, to tell you the truth, im not very sure of what hardware specs it has, its considerably old (not sure how many years its been since i bought it). it has a VERY small RAM, hence why im looking to upgrade it, it has two hard drives, one about 230 GB and the other is around 60 GB (ubuntu is installed on the 60 GB). im sorry i cant provide more information, i never really payed much attention to it... i just hope someone can look at that output i posted and help...

---

### Post by akakingess on 2009-09-30
When you say not much RAM, are you talking like 128 MBs, or 256 MBs, or 1 GB? What do you consider small amount of RAM, because some graphics cards will pull from your RAM and that could be another issue, could you boot into Windows XP and right-click on My Computer and see how much RAM exactly is installed in it, and any other info that you think may be useful for us?

---

### Post by baffle-boy on 2009-09-30
wow, i didnt know it told you about the RAM there... well, it says i have a 480MB RAM and it says processor 300+ (i doubt that means anything >.>)

(i feel so bad that i signed up here to ask a question, but you are all being so nice and helping a lot (i just hope it can be fixed))

---

### Post by wdzieczny on 2009-09-30
I don't know how you installed it but if you can get access to the boot parameters through grub (hit esc when grub is loading) try booting with this code ```
linux resolution="1024x738" noprobe
``` You can see if its a video card problem or not that way. You can replace 1024x738 with your native resolution.

---

### Post by Littleweseth on 2009-10-01
After googling your video card identifier (searched "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"), I found this forum thread :

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1224660](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1224660)

Apparently *this is a known bug*, [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/317658](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/317658). SiS graphics adapters are always a little bit dodgy...

**There is a workaround** given in my first link above : please attempt to follow it and post back if you run into any difficulties.

Once you resolve the problem, you may also want to post your solution back here, and to the Launchpad bug report, so the issue can be fixed for the next release of Ubuntu.

- L.

---

### Post by akakingess on 2009-10-01
You should be fine with that much RAM, one of the beauties of Linux/Ubuntu (not a RAM hog like M$ OSs), and the suggestion from wdzieczny is a great one, so I would try that next.

---

### Post by baffle-boy on 2009-10-01
could you please be more specific, as i said before, im a... n00b. i pressed esc numerous times to no effect. do you want me to open a command line? because im pretty sure the correct key for that is D... just rephrase that in newbie language please.

as a side note, i realized that the lines on the left and the lines on the right are simply REPLACING the images from either side (if the left one is on something blue, the corresponding line on the right is blue, vice versa)

---

### Post by Littleweseth on 2009-10-01
To quote from the forum post I linked to :

> 
please try adding sisfb to /etc/modules to solve this issue.

1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"
3) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/X11/xorg.conf"
4) In Section "Device" make sure there is a line specifying the sis driver:
Driver "sis"


The files should end up looking similar to this:


== /etc/modules ==
fuse
lp
sisfb
== ==

== /etc/X11/xorg.conf ==
Section "Device"
Identifier "Video Device"
Driver "sis"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Video Device"
EndSection
== ==


Just follow steps 1-4.

- L.

---

### Post by baffle-boy on 2009-10-01
well, i followed the instructions, and it appears that it MAY have reduced the effect... a fair bit. just to be sure i did it correctly my "modules" file is like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sisfb
```and my xorg.conf is like this:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
    Driver          "Sis"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```but its still bad enough for me to want to NOT use it... i wonder if the problem will persist in kubuntu, or linux mint...

EDIT: i just realized that the line i added in the .conf appears to have two extra spaces when i post it here, but look ok IN the xorg.conf... i wonder why?

---

### Post by Littleweseth on 2009-10-01
> **baffle-boy said:**
> and my xorg.conf is like this:

```
...
Section "Device"
    Identifier    "Configured Video Device"
    Driver          "Sis"
EndSection
...
```

Type 'sis' with no capitals. Remember that pretty much everything is case-sensitive in Linux, so 'Sis' may be a completely different animal to 'sis'. In this case, 'Sis' doesn't even exist; so xorg will be falling back to the default (buggy) driver you've already been using, instead of the 'sis' driver that may fix your problem.

---

### Post by akakingess on 2009-10-01
I don't think you need to go to Linux Mint, that would be for machines with the minimal hardware required, and I don't think you're there. It would be worth a shot to try kubuntu, but if you still see the issue, then I would have to think it would be hardware conflict that we aren't noticing. Obviously, it may be worth a shot to try kubuntu just as part of troubleshooting if you are willing to take the time to try it.

---

### Post by Littleweseth on 2009-10-01
Also, this wasn't explicitly mentioned in the guide I linked to, but there's a 'step 5' : restart Xorg (which reloads the driver.)

Logging out and logging in again should be sufficient, but a reboot wouldn't hurt.

Sidenote; The problem here is that the incorrect driver is getting loaded by default, because autodetection of SiS graphics adapters is buggy (see Launchpad bug above.) This problem would be common to both Ubuntu and Kubuntu, because they both use the same hardware autodetection scripts.

---

### Post by baffle-boy on 2009-10-01
ok, well I tried it the way i posted above, with the capital S but without the two spaces, without the capital S but with the spaces, without the  capital S or the spaces, and i rebooted EACH time. nothing seems to work, in fact the progress bar for shutting ubuntu down is higher up and plit apart into many horizontal lines now that i made the alterations... so obviously this is not my problem, i suppose its time to figure out how to un-install ubuntu...

---

### Post by Littleweseth on 2009-10-01
Before you do that, try one more thing...

**Replace the driver 'sis' with 'vesa'.** This is the last-resort fallback which works in 100% of cases (excluding faulty hardware.)

Sidenote : please be a bit more positive about things. It makes people more willing to help you...

Sidenote2 : Usually the drawback associated with falling back to the VESA driver is that it doesn't support any kind of 3D acceleration; this isn't an issue here because that SiS adapter has no 3D acceleration features *anyway.* (Reference : [http://ubuntuforums.org/showthread.php?t=450176](http://ubuntuforums.org/showthread.php?t=450176) )

---

### Post by baffle-boy on 2009-10-01
well thanks a lot for the help littleweseth, i cant try that out today, but i definitely will tommorrow (it's past my bedtime ;) ) ... by the way, how was i being "not positive", i'm UBER SUPER MEGA sorry for feeling discouraged that my (supposed to be) shiny new OS isn'y working right, and if its my saying that i should uninstall it now, that would be because i was going to try kubuntu (but thanks for the... advice anyways, i prefer pessimism XD)

---

### Post by baffle-boy on 2009-10-01
EDIT: YES!!!!! IT WORKED!! THANKS SO MUCH! (caps win) thank you all very much for trying so hard to help me, and especially you littleweseth, for fixing it! xD!

---

### Post by Littleweseth on 2009-10-02
No worries. :) Please mark the thread as solved, and post a comment to the Launchpad bug report so others know the problem still exists, and how you solved it.

- L.

---

