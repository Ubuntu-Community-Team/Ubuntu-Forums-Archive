---
title: "Network interface disassociates"
date: 2009-12-07
forum: General Help
---

### Post by apoth on 2009-12-07
I've upgraded to 9.10. Every time I connect to the wireless network I get maybe a minute of usage and then it disconnects.

Using WPA Personal. This is the network controller:
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

This is what I'm seeing in dmesg ad infinitum:

```
[ 1057.326847] eth0: associated
[ 1068.347613] eth0: disassociating by local choice (reason=3)
[ 1069.820524] eth0: authenticate with AP 00:1e:2a:19:25:ee
[ 1069.824920] eth0: authenticated
[ 1069.824925] eth0: associate with AP 00:1e:2a:19:25:ee
[ 1069.828349] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[ 1069.828353] eth0: associated
[ 1080.851723] eth0: disassociating by local choice (reason=3)
[ 1092.308294] eth0: authenticate with AP 00:1e:2a:19:25:ee
[ 1092.312732] eth0: authenticated
[ 1092.312735] eth0: associate with AP 00:1e:2a:19:25:ee
[ 1092.316199] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[ 1092.316202] eth0: associated
[ 1095.958588] eth0: disassociating by local choice (reason=3)
[ 1104.512761] eth0: authenticate with AP 00:1e:2a:19:25:ee
[ 1104.514238] eth0: authenticated
[ 1104.514241] eth0: associate with AP 00:1e:2a:19:25:ee
[ 1104.516863] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[ 1104.516870] eth0: associated
[ 1114.518869] eth0: disassociating by local choice (reason=3)
[ 1115.960299] eth0: authenticate with AP 00:1e:2a:19:25:ee
[ 1115.961781] eth0: authenticated
[ 1115.961784] eth0: associate with AP 00:1e:2a:19:25:ee
[ 1115.964535] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[ 1115.964539] eth0: associated

```

Using NetworkManager, not wicd or similar.

Any suggestions? Thanks.

---

### Post by JBAlaska on 2009-12-07
Are you using the **Broadcom STA driver** listed in *System, Administration, Hardware Drivers*? If not that is the one you want to use.

Also try disabling ipv6 support in the network manager applet.

---

### Post by apoth on 2009-12-07
IPv6 already disabled. Using the B43 driver (only one listed).

---

### Post by apoth on 2009-12-07
I found a reference to the broadcom sta driver being provided by bcmwl-kernel-source. Installed it, rebooted. No wireless networks available.

If I modprobe wl this happens:

```
FATAL: Error inserting wl (/lib/modules/2.6.31-16-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and this appears in dmesg:

```
[  155.327483] lib80211: common routines for IEEE802.11 drivers
[  155.327487] lib80211_crypt: registered algorithm 'NULL'
[  155.332402] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  155.332409] wl: Unknown symbol lib80211_get_crypto_ops
```

Going back to b43 'works', but the network doesn't even stay up for 10 seconds sometime!

---

### Post by JBAlaska on 2009-12-07
[COLOR="Blue"]Edit: you beat me to it, did you try to enable the STA in hardware drivers, and maybe blacklist the B43?[/COLOR]

If the driver in Hardware Drivers does not say "Broadcom STA driver", that may be the problem.

You can get the proper driver listed by installing the STA driver:

First go to System, Administration, Software Sources and make sure "Proprietary drivers for devices (restricted) is checked.

Then do this in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Reboot and the STA driver should be available in Hardware Drivers.

Note: You *MAY* have to blacklist the B43 driver, but since I no longer have a puter with a Broadcom chip-set I can't recall if this is necessary.

---

### Post by StuartN on 2009-12-07
> **JBAlaska said:**
> [COLOR="Blue"]Edit: you beat me to it, did you try to enable the STA in hardware drivers, and maybe blacklist the B43?[/COLOR]

If the driver in Hardware Drivers does not say "Broadcom STA driver", that may be the problem.

I installed 9.10 on a laptop with this chipset recently. The Broadcom STA (wl) and the B43 driver were both available in the Live CD, but not after installation. This is a silly bug.

However it did work perfectly (WPA encryption) after installing STA / wl, whichever name it goes by, using Synaptic.

---

### Post by JBAlaska on 2009-12-07
Yup, this fixes that problem:
```
sudo apt-get install bcmwl-kernel-source
```

But apoth may need to blacklist the B43 as well:
```
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by apoth on 2009-12-07
modprobe wl works now I've removed the wireless backports... just going to try a reboot so everything's nice and clean to see how it gets on.

---

### Post by apoth on 2009-12-07
No dice. The new driver doesn't appear in the hardware drivers list, wireless networks don't work.

modprobe wl seems to work without error. I've tried blacklisting b43 as recommended.

---

### Post by JBAlaska on 2009-12-07
Now I'm at a loss, this has always worked on kernels prior to 2.6.31-16. Do you see the STA driver if you boot to the LiveCD? if so there may be another module you need to blacklist, "b43-fwcutter" or "ssb" I can't really remember, sorry.

Any Broadcom experts please feel free to jump in here..

Edit: Try doing this:
```
lspci -nn
```
And see if there are any references or errors relating to B43

---

### Post by cmhwebster on 2009-12-12
I have exactly the same problem as apoth i.e. Broadcom 4306 (rev 03) wireless card that works (just about) with the b43 driver, but drops out every couple of minutes.  I've tried all the things described above but nothing seems to help.

If I isntall the bcmwl-kernel-source module and reboot, my Ubuntu 9.10 installation no longer even recognises my wireless interface i.e. wlan0 disappears completely from the lists when I do iwconfig or ifconfig, and Network Manager can't see it either.

The same machine (Dell Inspiron 9100) worked fine in exactly the same location when it was running Windows XP so it can't be a problem with wireless reception.

I've been through all the online help I can find, and I've tried the ndiswrapper solution previously, but that didn't work any better.

It seems the best I can achieve is to get maybe 90 seconds of internet connection at a time.  I can't even use the Ubuntu machine to post this message!

So here's another unhappy would-be Ubuntu user who'd be very happy to learn of any solution to this problem!

---

### Post by apoth on 2009-12-19
```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 81)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 81)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72 [GeForce 7300 LE] [10de:01d1] (rev a1)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)

```

---

### Post by apoth on 2009-12-19
I did an upgrade via the update manager, not a live CD.

Just ran the live CD though and it didn't offer a wireless interface to connect with, and hardware drivers offered the b43 driver only.

So I guess, support for my card is broken in 9.10. Ouch. :confused:

---

### Post by StuartN on 2009-12-19
> **apoth said:**
> So I guess, support for my card is broken in 9.10. Ouch. :confused:

I think the detection is a bit screwed, but support for my card is still present. After you run the Live CD you can open Synaptic and install the driver for your card, if support is still present, and after that the hardware drivers might magically suggest the latest driver - that is want my Broadcom did anyway.

---

### Post by apoth on 2009-12-19
> **StuartN said:**
> I think the detection is a bit screwed, but support for my card is still present. After you run the Live CD you can open Synaptic and install the driver for your card, if support is still present, and after that the hardware drivers might magically suggest the latest driver - that is want my Broadcom did anyway.

But it only suggests b43, which drops the connection within seconds.

---

### Post by apoth on 2010-01-09
I still haven't been able to get this working. :(

---

### Post by apoth on 2010-01-22
```
[  546.508104] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  546.508159] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  546.692376] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  546.876101] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 1)
[  546.878352] eth0: direct probe responded
[  546.878356] eth0: authenticate with AP 00:1e:2a:19:25:ee (try 1)
[  546.880036] eth0: authenticated
[  546.880056] eth0: associate with AP 00:1e:2a:19:25:ee (try 1)
[  546.882885] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[  546.882889] eth0: associated
[  556.904083] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  556.904132] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  557.088392] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  557.272100] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 1)
[  557.274343] eth0: direct probe responded
[  557.274347] eth0: authenticate with AP 00:1e:2a:19:25:ee (try 1)
[  557.276290] eth0: authenticated
[  557.276312] eth0: associate with AP 00:1e:2a:19:25:ee (try 1)
[  557.278725] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[  557.278728] eth0: associated
[  561.840605] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  561.840657] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.024372] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.208103] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 1)
[  562.408040] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 2)
[  562.410302] eth0: direct probe responded
[  562.410306] eth0: authenticate with AP 00:1e:2a:19:25:ee (try 1)
[  562.411986] eth0: authenticated
[  562.412008] eth0: associate with AP 00:1e:2a:19:25:ee (try 1)
[  562.414476] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[  562.414480] eth0: associated
[  562.432064] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.432115] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.616370] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.800101] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 1)
[  562.802355] eth0: direct probe responded
[  562.802359] eth0: authenticate with AP 00:1e:2a:19:25:ee (try 1)
[  562.804043] eth0: authenticated
[  562.804071] eth0: associate with AP 00:1e:2a:19:25:ee (try 1)
[  562.806524] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[  562.806527] eth0: associated
[  562.824047] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  562.824100] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  563.016109] eth0: deauthenticating from 00:1e:2a:19:25:ee by local choice (reason=3)
[  563.200074] eth0: direct probe to AP 00:1e:2a:19:25:ee (try 1)
[  563.202331] eth0: direct probe responded
[  563.202336] eth0: authenticate with AP 00:1e:2a:19:25:ee (try 1)
[  563.204935] eth0: authenticated
[  563.204955] eth0: associate with AP 00:1e:2a:19:25:ee (try 1)
[  563.209037] eth0: RX AssocResp from 00:1e:2a:19:25:ee (capab=0x411 status=0 aid=1)
[  563.209040] eth0: associated

```

Same behaviour under 10.04. :(

---

### Post by larson0699 on 2010-05-13
As I need the newer kernel for KMS to function properly with my Intel graphics, downgrading < 2.6.31 isn't a solution for me, nor should anyone be forced back from the current stable release. Is this even on the agenda for the kernel devs yet? Is the fault with a revision in the b43 module or the wireless code itself? Why has the issue persisted for _half a year_ without remedy? This is a nuisance, and we Broadcom folks are getting left out in the cold. And forget going the crippled wl (STA)/ndiswrapper route.

To recap my [post]("http://bbs.archlinux.org/viewtopic.php?id=70094") in a different forum, my card is a BCM4306 rev.3 (14e4:4320) in an HP Compaq nx6110 notebook -- the ssb module supports both that and the b44 Ethernet which works splendidly. As far as daemons are concerned, I have tried the network with and without Wicd, and I use dhclient for my DHCP broadcast. It is my hope that enough users are affected (the above link refers to a thread about Ralink/RT61 devices in a similar loop) that eventually we can focus our concerns on less basic functions of our OS pending a fix. I know I come off hasty this post, but our frustration should at the very least be acknowledged. This serves as a bump for a hopeful nod from upstream.

---

### Post by apoth on 2010-06-06
My other half is getting pretty annoyed now at still having a network cable trailing through the house!

---

