---
title: "ATI  Radeon X1300 driver installation issue -"
date: 2009-08-27
forum: General Help
---

### Post by sprilutsky on 2009-08-27
Hi there,

My desktop has an ATI Radeon X1300 Video Card. Graphics are not looking good. I am having a problem with installing a proper driver for this Video Card on ubuntu 9.04.

1. Initially I selected the ATI packages available on the ubuntu Synaptic Package Manager:
    xserver-xorg-video-ati
    xserver-xorg-video-radeon
    fglrx-kernel-source
    xorg-driver-fglrx
    fglrx-amdcccle
    xserver-xorg-video-mach64
    xserver-xorg-video-mach64
    jockey-gtk
    jockey-common

2. After I installed all those packages, I still do not see my Video Card in Hardware Drivers - No proprietary drivers are in use on this system

3. Then I installed the new driver for ATI Radeon X1300 Video Card - 
[B]ATI Catalyst™ 9.8 Proprietary Linux x86 Display Driver:
[/B]*ati-driver-installer-9-7-x86.x86_64.run*

Once I installed it, it created 2 menu options under Applications: 
ATI Catalyst Control Center
ATI Catalyst Control Center (super user)

However, it does not work - once I click on either one, getting a message: "There was a problem initializing Catalyst Control Center Linux Edition. It could be caused by following:
No ATI Graphics driver is installed or ATI driver is not functioning properly. Please properly install it or configure it using  ***aticonfig***

When I am trying to run ***aticonfig***, I get an error:
***aticonfig: No supported adapters detected***

Did someone have a way to fix this issue. Please help,

Thanks

---

### Post by jocko on 2009-08-27
Ati's proprietary driver does not support your card.
They dropped support for anything older than the radeon HD 2xxx cards in april, and the older drivers that still support your card does not support the version of xorg in jaunty, so there is no way you can get any version of fglrx to work.

---

### Post by sprilutsky on 2009-08-27
That pretty much means that I gotta go with nVidia cards. Could you recoomend  a few low end VGA's ( do not have much money to spend).

I am wondering if a couple of new GeForce cards I found out are good for UBUNTU 9.04
and well supported:

PNY  GeForce 8400 GS 2.0 256MB PCIe Low Profile
PNY  GeForce 9500 GT 1024MB PCIe

If not, could you recommend one, please?

Thanks for all your help

---

### Post by P4man on 2009-08-27
You'll have no problems with either, and if youre not into gaming, even a 8400 will be (more than) fast enough. Now of course you could also get a newer ATI card, those are well supported,  unless you want to punish them for dropping support on your card :)

BTW, not sure what they charge for those cards, but on ebay you can pick up previous gen cards for next to nothing. Something like an nvidia 7800 or 7900.. Faster than those 2 you listed there, and might well be cheaper.

edit: just won a bid on a 8800GT for &#8364;35 :p

---

### Post by sprilutsky on 2009-08-27
I am sorry - I am new to Video Cards. Can you give me a good example of lower end newer card?

Thanks

---

### Post by P4man on 2009-08-27
Its almost impossible even for a geek to keep up to date with all those numbering schemes, so I cant blame you.

with nvidia, the first digit used to denote the generation. Geforce 4 cards where 4200, 4600, etc. Geforce 8 where 8400, 8800, ...they dropped that scheme pretty much now for the newest cards.. but anyway, the second digit gave an idea of the performance within a generation. a 6200 would be bottom end cheap card, a 6800 top end. 

New generation usually perform better than previous ones, but not THAT much, so a 6800 would be considerably faster than a low end Geforce 7 (say 7200).

Confused yet ? you should be :)

Anyway, 8400 would be a low end G8 card. Barely sufficient for modern games, but certainly more than good enough for compiz and stuff. A 9500 is a current lowend G9 card. Is faster than a 8400, no doubt, but hardly a "gaming" card. 

It all depends what you intend to do with it. If 3D games are not your thing, then even any Geforce 6 would be plenty fast for compiz. Heck, I bet even a Geforce 4 would do.

if you want a rather  cheap fast card that is  adequate even for modern modern games, I would for look  a 8800GT on ebay. Below that, a 7900GT is a good card for the money

If you're buying new, pretty much anything you can buy nowadays will be fast enough for not-gaming..

---

### Post by sprilutsky on 2009-08-27
Thanks for your reply. I am not that much concerned about the speed, because I am not a gamer (at least yet). I am very concerned about UBUNTU 9.04 taking it, because I already have ATI VGA, but UBUNTU does not recognize it, cannot add proprietary driver.

Thanks

---

### Post by P4man on 2009-08-28
Well, the opensource driver should work relatively well with your card if you're not concerned about 3D speed. 

Perhaps you want to clarify your issues with it ?

---

### Post by jocko on 2009-08-28
> **sprilutsky said:**
> Thanks for your reply. I am not that much concerned about the speed, because I am not a gamer (at least yet). I am very concerned about UBUNTU 9.04 taking it, because I already have ATI VGA, but UBUNTU does not recognize it, cannot add proprietary driver.

Thanks
Ubuntu recognizes it just fine, it's just that ati does not produce any proprietary driver for it, so the restricted driver manager does not detect that you have a card that is supported by the proprietary driver...
The open source driver (radeon) should still work fine if you are not a gamer.
I don't know the status of 3d acceleration on that card with the open driver, but if it doesn't work now it will probably work "soon" (= Ubuntu 9.10 or 10.04)...

So if it's important for you to be able to use all the resources of a graphics card, buy an nvidia card (or a newer ati card, but who's to say when they decide to drop support for that card? Two years from now? Two months?).
If it's not that important, keep the card you have and use the open source driver.

---

### Post by sprilutsky on 2009-08-28
Thanks for your reply.

That exact "radeon" open source driver you are referring to and where to get it? Does Ubuntu Synaptic Package Manager have it or somethere else?


So here are a few issues I have with my Radeon X1300 card:
1. When I watch movie or concert on Ubuntu, it is very blurry. Just for comparison, on Windows XP - it is perfect, very crisp and sharp

2. When I fire VirtualBox and it brings WindowsXP, I cannot resize the Windows XP screen inside the VirtualBox screen. I can resize VirtualBox sreen, which I can make pretty big, but XP screen cannot

3. Running eMule in Windows session, it does not connect to the File Sharing servers, just hangs (perhaps this nothing to do with the VGA, but...)

Thanks

---

### Post by P4man on 2009-08-28
> **sprilutsky said:**
> T
So here are a few issues I have with my Radeon X1300 card:
1. When I watch movie or concert on Ubuntu, it is very blurry. Just for comparison, on Windows XP - it is perfect, very crisp and sharp

Blurry? What application are you using? Are we talking web (flash?) or movieplayer or something?

> 2. When I fire VirtualBox and it brings WindowsXP, I cannot resize the Windows XP screen inside the VirtualBox screen. I can resize VirtualBox sreen, which I can make pretty big, but XP screen cannot


Not a videodriver issue. You have to install the virtualbox guest additions.

[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)
> 
3. Running eMule in Windows session, it does not connect to the File Sharing servers, just hangs (perhaps this nothing to do with the VGA, but...)

Definately not gonna be solved with other videodrivers :)
Refer to the virtualbox documentation on how to configure your network in vb, I think you need bridging, but im not sure.

Why do you want to run emule in virtualbox anyway? There is a native ubuntu client called amule. 

> sudo apt-get install amule

if you have universe and multiverse enabled. There are plenty other file sharing clients for ubuntu.


Thanks

---

### Post by sprilutsky on 2009-08-28
Hi there

Like it was recommended above, I tried to install opensource driver for my ATI Radeon x1300 VGA card.

I got it from this link on ubuntu: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I was exactly following the steps in the above doc. After I removed xorg-driver-fglrx, 
I installed those mesa drivers and changed /etc/X11/xorg.conf with what recommended in the doc (see link above).

Then, logged out, switched to the console (alt+ctl+F1) and logged back in.
Then I ran sudo ***/etc/init.d/gdm restart ***and ran into the issue:

Window popped up with this message - "Ubuntu is running in low graphics mode. You may nned to update your configuration to solve this"
[INDENT][I](EE) Problem Parsing the config file
(EE) Error Parsing the config file
[/I][/INDENT]I cliked on ok and later got onto the menu with 4 options, where troubleshooting was available. I selected it and clicked on ok. It displayed  several messages:
Fatal Server Error:
No screens found
Check /var/log/Xorg.o.log
[INDENT]Xf86CloseConsole: KDSETMODE failed:   Bad file descriptor
                            VT_GET_MODE failed:Bad file descriptor 
                            VT_GET_STATE failed:Bad file descriptor 
[/INDENT]I had a back up copy of xorg.conf and was able to put original one back, but obviously stopped installing open source ATI driver.

Also, there was another message/window all the time while I was playing with X11 stuff - was complaining that there is already appears another X11 

Here is the Xorg.conf:
tsp0001@desktop1:~$ cat /etc/X11/xorg.conf
Section "Device"
        Identifier      "Radeon X1300"
        Driver          "ati"
        BusID           "PCI:4.0.0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon X1300"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1024x768"
                Virtual 1024 768
        EndSubSection
EndSection

Section "DRI"
        Mode      0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
#################################

tsp0001@desktop1:~$ cat /var/log/Xorg.1.*

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux desktop1 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Aug 28 18:20:52 2009
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
    Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux desktop1 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Aug 28 18:20:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
    Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
tsp0001@desktop1:~$ 

Obviously I misconfigured something here. Can someone help, please?

One more thing: I am using Totem Movie Player 2.26.1 from Ubuntu 9.04 distribution, but it is not sharp at all. Is there a better movie player to use?

Thanks

---

### Post by P4man on 2009-08-30
You probably have a typo somewhere in that xorg.conf, but i can't immediately spot it. But tbh, you probably wasted a ton of time, because you shouldn't have to do *anything* to run the opensource ati drivers. They are loaded automatically.

Try this basic xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection
```

Note that "ati" is a wrapper, and it will select "radeon" automatically if appropriate for your card.

as for the blurry videoplayback.. I have no idea. You could try using any of a gazillion mediaplayers (Smplayer is my personal favourite) but Im not sure what the problem is exactly. If you make a screenshot of movieplayer playing back a movie, does it show what you mean? 
Or is not blurry, but rather that playback is not smooth (not enough frames per second) ?

---

