---
title: "Lost wifi with upgrade to 11.4"
date: 2011-04-29
forum: General Help
---

### Post by Total Noob on 2011-04-29
I have lost wifi access with the upgrade to 11.4.

Previously, the receiver icon showed on left click a menu of available networks, and on right click, available network by network settings for editing. The menu also included enable wireless connection and enable wired connection. I have wireless enabled.

But with the upgrade, the same menu appears on left click or right click, and they both show a greyed out "wireless disconnected" tab, so you can't connect from there, the tab is disabled. There's also no place else to go to find available networks or to lock into one. There also does not seem to be a place to find wired networks either.

I installed my wifi network in it, and put in the correct password and set it to come on automatically, and 3x restarts did not yield any changes. Apparently network finding is disabled in this version or at least my copy.

It isn't the computer: I'm on line with it now on the Windows XP side.

This is doubly problematic because if I can't get on line, I can't download a fix, and even if I could by downloading it to the Windows side, it is probably a binary with some very scripts and meticulous BASH coding or tarballing something else that I have no idea how to do even with a walk through by an expert because most of the time the experts assume I know as much about using a Linux terminal and code as they do, and I basically know absolutely nothing, it is all Greek to me from the point at which they say "open a terminal." "Go to root" might as well be said in Chinese as far as its usefulness to me. 

What is the plan here? A complete redo from the get go?

Thanks.

---

### Post by ghiottolino on 2011-04-30
I had the same problem.

This happens because some drivers for wireless devices (in my case Broadcom) are not totally open source and they need the user to accept a licence agreement. Therefore the upgrade deinstalled those drivers.

The easies way to reinstall them is to connect to the Internet with your machine (via cable, or via smart phone tethering) and then click on system settigns > additional drivers. You should be able to see the suggested drivers to install.

I am pretty sure you can install such drivers manually, but this requires a bit more expertise.

Greetings,
Nicola

---

### Post by efes50cl on 2011-04-30
i  have lenovo 3000 v 200 and this didnt work for me. i coulnt enable wireleless

---

### Post by TBABill on 2011-04-30
Whenever posting about wifi issues (or other hardware issues), the only way someone can even begin to guess at the problem is to know all the symptoms and the hardware in question plus whatever you have done to get the correct driver and firmware installed or configured. If you post back more info on your machine we can assist.

Codes to run to give info to paste back here:

```
lspci
``` gives you a list of your internal devices (if they are PCI and not internal USB)

```
lsusb
``` lists all your USB devices

```
sudo lshw -C network
``` gives you your network config (but not device info)

```
lsmod
``` will list all drivers currently running

There are more, but these can help depending on what you need to discover.

---

### Post by grahammechanical on 2011-04-30
I installed 11.04 beta about a month ago and it recognised my ethernet connection at once and it was simple to set up the wireless connection. The left and right click menus are combined. It think this is good as all we need to say is click the icon, instead of left click and right click.

Do you see the line Enable Network? Is there a tick mark against it? If not then both wired and wireless networking is disabled. This is why you do not see any wireless networks.

Regards.

---

### Post by Total Noob on 2011-04-30
Ok. I have the info produced after the above queries. It is below.

But the bigger question is, how does Canonical expect people, especially Noobs like me, to use their stuff if there is going to be intermittent grief like this with no prior warning when the update nag arrives? 

If the issue really is the sufficiency of the wifi driver, why has Ubuntu gone backwards on functionality? 

This was not a problem before, and I have been using Ubuntu on that compute for several years, going back to 8.4, and it was only before that that I needed some kind of additional programming to get wifi going (which someone was kind enough to walk me through because I have no idea about the thousands of abbreviations and parameters needed to give a computer instructions, having abandoned the desire to learn and memorize codes like that when I stopped using punch cards in college 30 years ago and became a confirmed end user with no desire to further participate in programming with languages like Fortran and Pascal).

Moreover, I don't like the new desktop, and it seems to me the redesign -- expressly to make Ubuntu seem less like Windows -- is quite poor and unfriendly,. 

When you maximize an app, the app icons disappeared from the left. Since they have taken away the apps menu from the top toolbar, and since Canonical would never give a "Start" button, there's no way to launch another before minimizing the app you are on first. It also seems like app icons can't be put on the toolbar for quick launch, as was possible in 10.10. 

The change means extra work that slows you down and is thus pretty much thoughtless.

In addition, the "System" and "Preferences" menus are now very hard to find, and are in very unlikely places. "System settings" are bizarrely grouped with the on/off button with no other similar application to be found there. I'm still looking for "preferences" and more specifically for "fonts" so I can install my favorites, so far no luck.

And I don't like the adjustment by which tabs and menus appear and disappear with no click, just cursor positioning. All of a sudden, there's a lot of guesswork to figure out what is going on and how things work, and for the most part, their has been regression in ease of use and functionality. Almost everywhere I go, the job takes extra clicks and more searching and bumming around in menus to find what may or may not be correct. 

Anyway, here's the material that was requested following queries.

```
lspci 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)


lsusb 
Bus 005 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

sudo lshw -C network
*-network:0              
       description: Wireless interface 
       product: AR2413 802.11bg NIC 
       vendor: Atheros Communications Inc. 
       physical id: 5 
       bus info: pci@0000:06:05.0 
       logical name: wlan0 
       version: 01 
       serial: 00:16:ce:14:09:aa 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:21 memory:b0100000-b010ffff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 7 
       bus info: pci@0000:06:07.0 
       logical name: eth0 
       version: 10 
       serial: 00:0a:e4:f6:00:a5 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s 
       resources: irq:20 ioport:3000(size=256) memory:b0110000-b01100ff


```

This is all gibberish to me. Does any of this point the way towards undoing the wifi failure? 

Thanks.

---

### Post by Slomn on 2011-04-30
[FONT=monospace]The same thing happened to me, I am new to ubuntu and have just upgraded to 11.04, After upgrading, I can no longer access the internet through my asus n-13 usb, I may have disabled wireless accidentally, the button is right next to enable networking, and, once clicked, never comes back again.
I entered the recommended commands in terminal and got back this


sage@sage-Dimension-4700:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sage@sage-Dimension-4700:~$ sudo lshw -C network
[sudo] password for sage: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:ddeee000-ddeeffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:6f:71:60
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:ddeed000-ddeedfff ioport:ccc0(size=64)
sage@sage-Dimension-4700:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  4 
binfmt_misc            13213  1 
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
nvidia               9766978  40 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec
p54pci                 17054  0 
p54common              32371  1 p54pci
snd_seq_midi           13132  0 
crc_ccitt              12595  1 p54common
mac80211              257001  2 p54pci,p54common
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
ndiswrapper           192828  0 
snd_timer              28659  2 snd_pcm,snd_seq
dcdbas                 14054  0 
cfg80211              156212  2 p54common,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
psmouse                73312  0 
parport_pc             32111  1 
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_hda_intel,snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
hid_logitech           17421  0 
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
e100                   40108  0 
hid                    77084  2 hid_logitech,usbhid

[/FONT]

---

### Post by Total Noob on 2011-04-30
Good and bad news. 

Good news: After posting #6, the damn thing worked fine without me doing anything I hadn't done before. Worked with it most of the afternoon, strong signal on my network.

Bad news: after a reboot, I was dead in the water again. Didn't do anything different that time either, and nothing. One thing I did notice was that I could at least get the thing to search for a network by tapping "find hidden network" and then editing the settings for my network, but it still couldn't actually find it, and when I checked the settings again, the settings had been reversed, and they simply would not stay remembered.

I think there is a significant flaw in the programming since it works intermittently, and since I can't hard wire into the network, and since no help is forthcoming on this site, I think I'm screwed.

---

### Post by _rH on 2011-05-29
> **Total Noob said:**
> 
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 

sudo lshw -C network
*-network:0              
       description: Wireless interface 
       product: AR2413 802.11bg NIC 
       vendor: Atheros Communications Inc. 
       physical id: 5 
       bus info: pci@0000:06:05.0 
       logical name: wlan0 
       version: 01 
       serial: 00:16:ce:14:09:aa 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:21 memory:b0100000-b010ffff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 7 
       bus info: pci@0000:06:07.0 
       logical name: eth0 
       version: 10 
       serial: 00:0a:e4:f6:00:a5 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s 
       resources: irq:20 ioport:3000(size=256) memory:b0110000-b01100ff

[/CODE]

Thanks.

Hi, I have the identical ath5 Atheros AR2413 controllers, and similar wifi issues on 11.04. 
I've made a few suggestions which worked for me at:

[http://askubuntu.com/questions/38466/atheros-ar2413-not-working-after-upgrade/45836#45836]("http://askubuntu.com/questions/38466/atheros-ar2413-not-working-after-upgrade/45836#45836")

---

