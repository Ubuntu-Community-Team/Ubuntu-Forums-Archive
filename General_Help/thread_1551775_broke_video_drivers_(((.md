---
title: "broke video drivers ((("
date: 2010-08-12
forum: General Help
---

### Post by Nimridil on 2010-08-12
A couple weeks ago I wanted to connect an external screen to my laptop running ubuntu 10.04. As nothing happened after I plugged the VGA cable in (except that the other screen went black instead of showing default stuff) I started googling for suggestions. Somebody out there advised installing nvidia drivers for that, so I grabbed NVidia binary X.Org driver from ubuntu software center. Nothing useful happened and as I didn't have time at the moment to continue messing with this I left of there.
The next time I boot into ubuntu I notice that the extra visual effect are not working, which I enjoyed very much. I got rid of the nvidia driver, but still wasn't able to turn the extra effects on.
I've been looking up stuff on the topic now and then all over the internet, but alas in vein.
Does anybody know how to restore the drivers to their original state? Or what else can be done?
Any help is appreciated.

---

### Post by earthpigg on 2010-08-12
system -> preferences -> visual effects

if that is set to 'none', your eye candy will be off.

system -> admin -> hardware drivers

what is listed there?

---

### Post by Nimridil on 2010-08-12
> **earthpigg said:**
> system -> preferences -> visual effects
if that is set to 'none', your eye candy will be off.
Sure I checked there. It doesn't let me switch to Extra and says "Desktop effects could not be enabled". I wish it was that simple :wink:

> **earthpigg said:**
>  system -> admin -> hardware drivers
what is listed there?
Nothing at all :(

---

### Post by earthpigg on 2010-08-12
what video card do you have?

```
lspci | grep nVidia
```

---

### Post by Nimridil on 2010-08-12
Here's the whole output of lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```I don't have a "separate" video card per se. For what I know mine is inbuilt into the motherboard. The only two things pertaining to graphics I see in the list are:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```Hope that helps...

---

### Post by earthpigg on 2010-08-12
Ah. Installed *nVidia* drivers and tried to put them in charge of an *Intel* integrated graphics card. The directions you followed where for someone with an nVidia graphics card (integrated or otherwise).

we need to undo all the changes nvidia-settings made.

```
sudo grep nvidia /etc/X11/*
```
and
```
sudo grep nVidia /etc/X11/*
```

should both return nothing for you, as you have no nVidia hardware on your computer. i suspect that is not the case?

what about this:

```
sudo grep nVidia /etc/X11/xorg.conf.backup
```

if that returns nothing, then we may have a viable backup we can use.

---

### Post by Nimridil on 2010-08-12
app-defaults  cursors  default-display-manager  fonts  imwheel  rgb.txt  X  xinit  xkb  Xreset  Xreset.d  Xresources  Xsession  Xsession.d  Xsession.options  Xwrapper.config

That's all I have in the /etc/X11/   And unfortunately no backup.

U r right, I should have thought ahead before installing that nvidia driver. But like somebody said in one the recent thread, the best way to figure things out is to tear everything apart and then put back together.

---

### Post by earthpigg on 2010-08-12
look in xorg.conf, see if there is any mention of nvidia.

copy/paste if there is, plz.

---

### Post by Nimridil on 2010-08-12
Well, as I said earlier I have no xorg.conf in /ect/X11/
I googled for other places where it might reside, but I don't have it there either.
I guess maybe that is, or at least in part, the source of the problem.
It there any way to restore it?

Thanks for trying to help my out with my issue, [earthpigg]("http://ubuntuforums.org/member.php?u=561472").

---

### Post by earthpigg on 2010-08-12
give this a shot:

> sudo Xorg -configure

from [here]("https://wiki.ubuntu.com/X/Config")

---

### Post by Nimridil on 2010-08-12
sudo Xorg -configure                         returns

> Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help.I tried to move /tmp/.X0-lock to a backup location, after that for the same command it spat this:

> _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


The /var/log/Xorg.0.log contained the same as the last output and three more lines

> (WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

---

### Post by earthpigg on 2010-08-12
oh. well then. the command doesn't want to be run with X running.

restart, holding shift down as the computer starts.

once at the grub screen, select the option that gives you a command line only.

then run the command.

---

### Post by Nimridil on 2010-08-12
When I press c in the grub, it doesn't recognize Xorg as a command from that command line.
I tried to but into recovery mode, but then the command line is for root, not my account, and so it created xorg.conf.new for root, and I'm not able to get into the root folder even with sudo.
I also tried ctrl+alt+f2, but apparently that doesn't stop X execution.

---

### Post by Nimridil on 2010-08-13
I've tried a whole bunch of stuff, but nothing seems to work.
Whatever I type to configure or reconfigure X, it always responds with:
> Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.If I try to kill the Xorg process from top by it's PID, it brings me at a login screen, and after I log in the Xorg is up again.

I tried to boot into recovery mode from grub and go to the little graphics repair wizard through dpkg. But when I get to the menu where it's asking me to either reset default configuration, or repair from a backup, or determine the configurations for my hardware, whatever I choose nothing happens.
The same goes for when I try to run 
```
sudo dpkg-reconfigure xserver-xorg
```absolutely nothing happens. I even tried to reinstall X
```
sudo apt-get install xorg --reinstall
```
It prints it's regular output, and probably does replace the files, but that doesn't fix anything.

Has anybody ever encountered anything similar or maybe have an idea of how this might be fixed.
Thanks

---

