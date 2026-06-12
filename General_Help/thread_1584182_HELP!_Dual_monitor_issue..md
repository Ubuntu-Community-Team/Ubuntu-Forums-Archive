---
title: "HELP! Dual monitor issue."
date: 2010-09-28
forum: General Help
---

### Post by teh'p3nsi0n3r on 2010-09-28
Ok so I've finally got round to adding a 2nd monitor to my rig. 

Everything is working fine except for Compiz/Desktop effects. The card i have is a ATI Radeon 9550. The main monitor i use is a Samsung Syncmaster T200HD. Compiz has always worked fine at resolution of 1680 x 1050 by itself before adding a 2nd monitor.

After a little searching about i believe that the driver i am using is the default "radeon" driver. And the ATI Catalyst drivers. (have tried anyway). No longer support my card. And it is not possible to use any old drivers on ubuntu 10.04 from previous versions. So I am stuck with the default drivers.

Compiz Also works fine when the desktop is set to duplicate on both screens. But I am "extending" the desktop on to the 2nd monitor as i do not want to duplicate my desktop on 2 screens, and this is where i am having problems.

When I have the screens set to extend, the desktop effects switch off. Now i beleive this is something to do with resolutions being over a certain size i read?. I am not sure if this is true.

I am running my Samsung syncmaster T200HD at 1680 x 1050, and my old CRT at a reslution of 1280 x 1024.

I have tried reducing these resolutions to a very low resolution on both monitors (still set to extend) but trying to enable desktop effects still does not work.

Here is some terminal information below, if it is of any help?.

Thanks.



Running this in the terminal , i got the following.


> hwinfo --gfxcard
23: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4153
  Unique ID: VCu0.yvUasOMnfI3
  Parent ID: vSkL.ITQqGs0XM26
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV350 AS"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4153 "RV350 AS"
  SubVendor: pci 0x148c "C.P. Technology Co. Ltd"
  SubDevice: pci 0x2087
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  I/O Ports: 0xde00-0xdeff (rw)
  Memory Range: 0xfe9e0000-0xfe9effff (rw,non-prefetchable)
  Memory Range: 0xfea00000-0xfea1ffff (ro,prefetchable,disabled)
  IRQ: 16 (197302 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00004153sv0000148Csd00002087bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: radeon
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

24: PCI 100.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4173
  Unique ID: NXNs.xaX+Y0hKOmF
  Parent ID: vSkL.ITQqGs0XM26
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: graphics card
  Model: "ATI RV350 AS [Radeon 9550] (Secondary)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4173 "RV350 AS [Radeon 9550] (Secondary)"
  SubVendor: pci 0x148c "C.P. Technology Co. Ltd"
  SubDevice: pci 0x2086
  Memory Range: 0xe8000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xfe9f0000-0xfe9fffff (rw,non-prefetchable)
  Module Alias: "pci:v00001002d00004173sv0000148Csd00002086bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

---

### Post by teh'p3nsi0n3r on 2010-09-30
bump!

---

### Post by goodolandy on 2010-09-30
Hi there, I am familiar with your problem having experienced it many times over a 4-5 year period that I tried to switch from Windows to Linux.  Unfortunately the only advice I have is to possibly upgrade your video card.

I am using the ATI HD 4350 and it wasn't until I decided to try Ubuntu 10.04 when I was able to finally have both wide dual screen desktop and Compiz working together and I owe it all to Ubuntu Hardware Drivers feature which downloads the proper Catalyst driver and enable it.

With all previous attempts over the years, I could never get the proprietary ATI driver to install, no matter what distro I tried and the default drivers, even after manually editing the xorg.conf file, one wide desktop and Compiz just would not allow each other to work at the same time.

---

### Post by teh'p3nsi0n3r on 2010-10-03
hi, thanks for your reply mate. Looks like i am going to have to bare it. :)

---

### Post by teh'p3nsi0n3r on 2010-10-07
Ok so i have just tried a live usb of ubuntu 10.10, still using the radeon 9550 ati card, previous could not get compiz to work with the dual monitors on 10.04 (i know the reasons for this as previously mentioned).

I have just tried a live usb for 10.10 and compiz seems to now work with dual monitors, this is a big improvement. :)

But half of the screen on 2nd monitor looks funny. its not displaying correctly, but the other half it does, the 1st monitors looks fine (no issues). its as if the 2nd monitor isnt stretching all the way accross. But disabling compiz fixes this issue.

Still I am impressed that compiz will actually enable now using extended mode. Any ideas how i can fix the 2nd monitor would be appreciated. 

I have attached an image to show an example of the issue. As you can see, one window is on the left monitor, then showing the rest of the window on the right. (with compiz enabled). It is the rest of the monitor that you can see looks "garbled".

I am only trying this from a live usb at present, will installing this to hard disk make any difference? is there any files or fixes i can amend?.

thanks.

---

### Post by robert shearer on 2010-10-07
I am at work now but tonight I will try switching on compiz effects and report.
My card is close (9250) and also uses the radeon driver as it is now unsupported by ATI.
I am just happy and grateful to have dual monitors set-up and work so easily with this card being as it is unsupported. :)

The open source radeon drive improves with every release and can't be far off the performance the closed source ATI driver used to achieve, in older versions of Ubuntu, when the card was supported. :)


Edit.......
OK, tried enabling compiz and "extra desktop effects" and all works fine.
I can grab a wobbly window and drag it wobbling and screaming to the second monitor where it fills the screen fine. :)

My monitors are Acer 16" CRT 1024 x 768 @ 85Hz as main in normal orientation and a dell 15" LCD 1024 x 768 @60Hz rotated left.

I have a 9550 card on another box and if I get the time this weekend I will try it as a dual monitor and report.

---

### Post by teh'p3nsi0n3r on 2010-10-15
> **robert shearer said:**
> I am at work now but tonight I will try switching on compiz effects and report.
My card is close (9250) and also uses the radeon driver as it is now unsupported by ATI.
I am just happy and grateful to have dual monitors set-up and work so easily with this card being as it is unsupported. :)

The open source radeon drive improves with every release and can't be far off the performance the closed source ATI driver used to achieve, in older versions of Ubuntu, when the card was supported. :)


Edit.......
OK, tried enabling compiz and "extra desktop effects" and all works fine.
I can grab a wobbly window and drag it wobbling and screaming to the second monitor where it fills the screen fine. :)

My monitors are Acer 16" CRT 1024 x 768 @ 85Hz as main in normal orientation and a dell 15" LCD 1024 x 768 @60Hz rotated left.

I have a 9550 card on another box and if I get the time this weekend I will try it as a dual monitor and report.

Hi Robert, 

cheers mate, thanks for reporting your findings. Did you find time to try out your other setup with the 9550 card?.

regards.

teh'p3nsi0n3r :)

---

### Post by messner on 2010-10-15
I have the same problem on the radeon:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

---

### Post by robert shearer on 2010-10-16
> **teh'p3nsi0n3r said:**
> Hi Robert, 

cheers mate, thanks for reporting your findings. Did you find time to try out your other setup with the 9550 card?.

regards.

teh'p3nsi0n3r :)

Mowed the lawns, dug out the hen house, went to the Garage lot to get the quote for the new garage, cleaned the house, washed the dogs.... and ran out of time :( will try again this weekend :)

---

### Post by teh'p3nsi0n3r on 2010-10-16
> **robert shearer said:**
> Mowed the lawns, dug out the hen house, went to the Garage lot to get the quote for the new garage, cleaned the house, washed the dogs.... and ran out of time :( will try again this weekend :)

Hi Robert!

seems you've been pretty busy then! lol!. no problems, just whenever you get time mate to check your setup, totally apreciated.


[QUOTE=messner]I have the same problem on the radeon:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01) [/QUOTE]

hopefully this is issue will be addressed soon. I understand ATI have have discontinued drivers for the radeon 9550 series but the open source driver has come along way since I tested on 10.04. I could get dual monitors, but not with compiz. So a slight improvement here. Hopefully there is a fix/update for this issue soon.

---

### Post by teh'p3nsi0n3r on 2010-10-26
Hi Robert, 

wondering if you've had any lucky with the radeon 9550 card? I have been trying for weeks now, still no luck with compiz and dual monitors. :(

---

### Post by robert shearer on 2010-11-03
> **teh'p3nsi0n3r said:**
> Hi Robert, 

wondering if you've had any lucky with the radeon 9550 card? I have been trying for weeks now, still no luck with compiz and dual monitors. :(

Yes, lots of lucky with it :)
Works fine. Same performance as the 9250 on the other rig.
> "extra desktop effects" and all works fine.
I can grab a wobbly window and drag it wobbling and screaming to the second monitor where it fills the screen fine. 


same set-up of monitors as in my previous post so my resolutions are different.
 However you posted that....> I have tried reducing these resolutions to a very low resolution on both monitors (still set to extend) but trying to enable desktop effects still does not work. so it seems it might be hardware rather than configs ?.

have you got round to installing instead of running from a usb ?? and if so has that cured it ??

Cheers,
Bob the Tardy.):P

---

### Post by teh'p3nsi0n3r on 2010-11-07
Hi robert, thanks for your reply. :)

are you running ubuntu 10.10?. And you have compiz working with both monitors using the radeon 9550?.

I installed Ubuntu 10.10 to my hard disc (ran all of the updates). But still getting the same results!. 

Which are: Compiz is working. Both monitors. (duplicating the screen mode works fine. the problem still lies with extended mode in which compiz works fine).

The issue is: **I still seem to get some glitching on the 2nd monitor in extended mode**. (16' CRT). 

I have attached another picture of my 2nd monitor to show another example of what's happening. The first monitor 20' HD flat screen is running perfectly fine.

I do not understand why it could be the hardware since you are running the exact same card? and same OS? and you have your setup working :).

Edit: btw, i do not know if it is worth mentioning. Extended mode in windows 7 works perfectly fine. So i know it is not the hardware.

---

### Post by robert shearer on 2010-11-07
> **teh'p3nsi0n3r said:**
> Hi robert, thanks for your reply. :)
are you running ubuntu 10.10?. And you have compiz working with both monitors using the radeon 9550?.
The issue is: **I still seem to get some glitching on the 2nd monitor in extended mode**. (16' CRT). 

I do not understand why it could be the hardware since you are running the exact same card? and same OS? and you have your setup working :).

Edit: btw, i do not know if it is worth mentioning. Extended mode in windows 7 works perfectly fine. So i know it is not the hardware.

1)Running 10.10 0n the 9250 card and 10.04 on the 9550 (though a live cd of 10.10 on the 9550 is good too) Compiz works with both monitors with 9550.

2)As my crt is my **main monitor** it is connected to the vga out on the 9550.  The dvi out goes to the dvi in on my dell flat-screen and I use the extended desktop option configured through System>Preferences>Monitors.

you could try swapping monitors main vs secondary and see if that makes a difference ? doubtful :(
Have you made a custom xorg.conf for any reason or are you running the default installation ? (my set ups work OOTB with the default)

As you say that the same hardware works with W7 it seems odd that the default Ubuntu does not when mine does (and does so with 10.04 as well !) If it weren't for that I would say cables would be worth checking. 

I will ponder more though, hopefully, someone can suggest other options to try....:)

**edit...** just looked at your screen-shot. Is the glitch only apparent when running VLC or with everything ? 
(I'm not a great video user so have not tried VLC on the secondary monitor. (generally use my main crt for photo editing and the lcd for folder view and tool-bars (gimp etc)

If the former then it may be a VLC or resources issue and not X at all. ?
Or that the open-source radeon driver is not quite there just yet compared to the ATI driver you use with Win7. ?

---

### Post by messner on 2010-11-09
My external monitor works like a charm now after bug-fix update ;)

---

### Post by robert shearer on 2010-11-09
> **messner said:**
> My external monitor works like a charm now after bug-fix update ;)

So perhaps for the benefit of others you could explain what this 'bug-fix update'  is and provide links.

---

### Post by starredsteria on 2010-11-10
I'm having the same issue.. but I have an Acer Aspire One (1024x600) with Samsung (1920x1080) dual monitor. I can get effects working fine on each monitor by itself, but will not work as extended (same image in both won't work.. as it defaults my resolution to like 800x600). I originally installed 10.10 on Sunday... and couldn't get compiz through tweak didn't work. Went into appearance and could not change effects from 'none' to 'normal'. I end up getting an error "Desktop effects could not be enabled". So... I just did a clean install yesterday... updated proposed packages as other forums have suggested, have not downloaded anything else yet, but running dual monitor, I still get the same error when switching effects to Normal. (I'm assuming that compiz will only run when you have your effects set to 'normal' instead of 'none'.) 

lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel modules: i2c-i801
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Kernel driver in use: ath5k
    Kernel modules: ath5k


Any suggestions on fixing this? I've been on irc.. and everyone that's responded says theirs is working fine :(

---

### Post by robert shearer on 2010-11-11
Hi starredsteria, this thread is about dual monitors and **ATI 9550** cards.

If you put this into your favourite browser you should find several threads referencing **your** graphics card.

```
site:ubuntuforums.org Intel Corporation Mobile 945GME Express Integrated Graphics  dual monitors 
```

Here are a few that may have some answers for you...
[http://ubuntuforums.org/showthread.php?p=9912767](http://ubuntuforums.org/showthread.php?p=9912767)
[http://newyork.ubuntuforums.org/showthread.php?t=1440142](http://newyork.ubuntuforums.org/showthread.php?t=1440142)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1445243](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1445243)

---

### Post by messner on 2010-11-11
I did that:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1594087](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1594087)

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
Logout or restart and everything should work fine.

---

### Post by robert shearer on 2010-11-11
Thanks for the link messner, most helpful.

note, if you wrap your commands in code tags it gets rid of the inadvertent smilies :)  like so..

```
 sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

