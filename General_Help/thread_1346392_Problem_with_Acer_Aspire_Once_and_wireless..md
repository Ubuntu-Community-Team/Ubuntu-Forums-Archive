---
title: "Problem with Acer Aspire Once and wireless."
date: 2009-12-05
forum: General Help
---

### Post by sean09 on 2009-12-05
I'm using an Acer Aspire One D250-1151 netbook, and I'm having a bit of trouble. On both Ubuntu 9.10 **AND** Ubuntu Netbook Remix, the following problem happens. When using Live CD, networking/wireless works. Just activate the wireless drivers under Hardware Drivers and it's good. That works only using Live CD during the installation. However, when it gets fully installed, it doesn't work. Drivers don't show up anymore to activate, no network connections, nothing. Obviously this is a big problem for me and I would appreciate any help I can get.

Thank you. :)

---

### Post by sean09 on 2009-12-05
Anyone?

---

### Post by wilee-nilee on 2009-12-05
Some have had problems so lets identify your wireless card in the terminal.
lspci

Here is a very long thread.
[http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529)

---

### Post by MickS on 2009-12-05
I had the same problem with my D150, Unfortunately I cant find the thread which helped me and I can't remember the exact details but essentially all I had to do was boot up the installed version then plug in the usb stick that I installed from, open it in Dolphin in my case, then navigate to a folder called pool, in there somewhere is a deb but I can't remember what it's called. Double clicked on it and it installed the drivers. Rebooted the Acer and the wireless worked and has ever since.


Mick

---

### Post by sean09 on 2009-12-05
> **MickS said:**
> I had the same problem with my D150, Unfortunately I cant find the thread which helped me and I can't remember the exact details but essentially all I had to do was boot up the installed version then plug in the usb stick that I installed from, open it in Dolphin in my case, then navigate to a folder called pool, in there somewhere is a deb but I can't remember what it's called. Double clicked on it and it installed the drivers. Rebooted the Acer and the wireless worked and has ever since.


Mick

Alright, that's something. Thanks! Would anyone happen to know what .deb this is?

---

### Post by fooman on 2009-12-05
like winee-nilee suggested....open a terminal and type:

```
lspci
```

then post the output back here.  that will tell us what wireless card you have.

---

### Post by sean09 on 2009-12-05
This is what I got:

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)


---

### Post by fooman on 2009-12-05
open synaptic (system > administration > synaptic package manager) and search for "bcmwl-kernel-source"

install it if is not already installed...reinstall it if it is installed.

reboot after that and see if its working.

---

### Post by sean09 on 2009-12-06
> **fooman said:**
> open synaptic (system > administration > synaptic package manager) and search for "bcmwl-kernel-source"

install it if is not already installed...reinstall it if it is installed.

reboot after that and see if its working.

I see no exact "bcmwl-kernel-source" but I do see "bcmwl-modalises" which says Broadcom 802.11 STA Driver on it. Yet there's no option to install or reinstall. They're greyed out.

---

### Post by fooman on 2009-12-06
ok,  you may have to enable the "retricted" repos to see it...

open synaptic and in the toobar click settings > repositories

under the "ubuntu software" tab....make sure the first 4 choices have check marks next to them (main-universe-restricted-multiverse).  then click "close".

you will see a message saying that the repos have changed,  click closed on there as well.

next,  in synaptic click on the "reload" button to refresh the newly added repositories....then search again for the "bcmwl-kernel-source" package and either install or reinstall it.

hope that helps.

---

### Post by MickS on 2009-12-07
As luck would have it the last kernel upgrade wrecked my system so I had to re install it (avoid the latest kernel).
This is what I did, installed Ubuntu off the stick, unplugged the stick, rebooted then plugged the stick  back in, navigated to the deb file on the stick:-  pool>restricted>b>bcmwl> and the file is bcmwl kernel source plus jadda jadda doesnt matter 'cos there is only one, double click and install it even thought it says it is installed already. Rebooted yet again and it connects easily, worked for me.


Mick

---

### Post by JBAlaska on 2009-12-07
First go to System, Administration, Software Sources and make sure "Proprietary drivers for devices (restricted) is checked.

Then do this in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Reboot and the STA driver should be available in Hardware Drivers.

---

### Post by Sorwen on 2009-12-07
I had a similar problem with my Compaq 1100DX. I don't know how advisable the steps are, but I used post #10 from this thread I found(through the usb install thread) here [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/449268](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/449268) and it worked like a charm.
 
> 
Simple workaround at [[COLOR=#0033aa]http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html[/COLOR]]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html")
I did the command line method. Plug in to a wired network connection and run:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
After using those two commands it has been smooth.

---

### Post by cozski on 2010-01-13
Hey

I have an Acer Aspire One GZ8 - the WiFi obviously don't work OOTB with Netbook Remix. I've followed the advice in this thread and believe I now have to blacklist acer_wmi by adding this line: "blacklitst acer_wmi" at /edc/modprobe.d/blacklist then restart my computer. Where & how do I add this line? Thanks :)

---

### Post by cozski on 2010-01-13
> **cozski said:**
> Hey

I have an Acer Aspire One GZ8 - the WiFi obviously don't work OOTB with Netbook Remix. I've followed the advice in this thread and believe I now have to blacklist acer_wmi by adding this line: "blacklitst acer_wmi" at /edc/modprobe.d/blacklist then restart my computer. Where & how do I add this line? Thanks :)

Sorry, that should read ZG8 ;)

---

### Post by bkratz on 2010-01-13
> **cozski said:**
> Sorry, that should read ZG8 ;)




Are you sure that you have the same wireless card?

If not go to the terminal and type in 

lspci | grep Wireless

(that is LSPCI in lowercase)

---

### Post by cozski on 2010-01-13
It's Atheros AR5001 Wireless Network Adapter (rev 01). 

I think I understand the process of blacklisting acer_wmi by navigating to /etc/modprobe.d/blacklist and opening the file and simply adding the line... but where exactly should I add it and when I open the file it says it's Read-only which I suspect means I cant save the changes?

---

### Post by bkratz on 2010-01-13
> **cozski said:**
> It's Atheros AR5001 Wireless Network Adapter (rev 01). 

I think I understand the process of blacklisting acer_wmi by navigating to /etc/modprobe.d/blacklist and opening the file and simply adding the line... but where exactly should I add it and when I open the file it says it's Read-only which I suspect means I cant save the changes?

First, I believe the blacklist has to have a .conf at the end in newer versions of Ubuntu. Are you trying to do this in the terminal? If so, I just simply did

gksudo gedit /etc/modprobe.d/blacklist.conf and did a simple save (without changing anything, but I could have).

Is acer_wmi what you want to add to the blacklist?
If so, you would just have to make an entry such as
blacklist acer_wmi

I don't know what acer_wmi is, but if this is what you want....

---

### Post by bkratz on 2010-01-13
Oh, I just found where you got it.

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

---

### Post by cozski on 2010-01-13
> **bkratz said:**
> Oh, I just found where you got it.

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Yeah, I took the info from there... 

I navigated to the folder as you did and inserted blacklist acer_wmi at the bottom, saved, rebooted... no WiFi.

I noticed that I don't have any proprietary drivers when I check for Hardware Drivers... should this be he case?

Thanks

---

### Post by cozski on 2010-01-13
I also noticed that after I had done this, the wireless icon no longer allowed me to 'enable wireless' when I right-clicked it. So I have taken the blacklist acer_wmi entry back out of the blacklist.conf file and rebooted, but this still doesn't allow me to enable wireless. Prior to making any of those changes I could at least check the 'enable wireless' option, even if it couldn't see a wireless connection. Still no internet :(

---

### Post by bkratz on 2010-01-13
> **cozski said:**
> I also noticed that after I had done this, the wireless icon no longer allowed me to 'enable wireless' when I right-clicked it. So I have taken the blacklist acer_wmi entry back out of the blacklist.conf file and rebooted, but this still doesn't allow me to enable wireless. Prior to making any of those changes I could at least check the 'enable wireless' option, even if it couldn't see a wireless connection. Still no internet :(

Can you copy paste the outputs of the following commands back here (use the code tags above to make easier to read----#)

1) lspci | grep Wireless
   (LSPCI in lowercase)
2)  sudo iwlist scan

3)  sudo lshw -C network
(that is LSHW in lowercase)

---

### Post by cozski on 2010-01-13
Hey... I don't have access to the Internet for my netbook right now - have to use ethernet connection at work tomorrow so I'll do as you requested then. Hope that's okay. Thanks.

---

### Post by cozski on 2010-01-13
> **bkratz said:**
> Can you copy paste the outputs of the following commands back here (use the code tags above to make easier to read----#)

1) lspci | grep Wireless
   (LSPCI in lowercase)
2)  sudo iwlist scan

3)  sudo lshw -C network
(that is LSHW in lowercase)

In respect of the scan (2) I'll be at work so it wont pick up my home connection if that's the purpose of it... will this matter?

---

### Post by bkratz on 2010-01-13
> **cozski said:**
> In respect of the scan (2) I'll be at work so it wont pick up my home connection if that's the purpose of it... will this matter?



No we just want to see if it sees anything at all.

---

### Post by cozski on 2010-01-14
lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```sudo lshw -C network

```
cozski@cozski-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:23:8b:a2:26:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.9 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:55200000-5523ffff ioport:3000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:56:7b:98:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:54100000-5410ffff
```

---

### Post by bkratz on 2010-01-14
This thread has a lot on information re: your card. Check out post #38 first.

[http://ubuntuforums.org/showthread.php?t=1309072&page=4](http://ubuntuforums.org/showthread.php?t=1309072&page=4)

---

### Post by spiderbatdad on 2010-01-14
> **cozski said:**
> 
sudo lshw -C network

```
cozski@cozski-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:23:8b:a2:26:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.9 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:55200000-5523ffff ioport:3000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:56:7b:98:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:54100000-5410ffff
```

This card should work out of the box on Karmic. Was your installation an upgrade?
Anyway, you should have a file called /etc/modprobe.d/blacklist-ath_pci.conf If you don't, create it. In the file goes:
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

---

### Post by cozski on 2010-01-14
Hey... well I'm a little bamboozled... after I posted the info above I went round to my girlfriends house and just checked my wireless connections to see if it picked anything up and it picked up her connection and those around her no problem. I cant say I did anything to make this happen... it was just there... so, I guess that's a resolution then :D

Thanks to all those who gave me support/advice - really appreciated!

---

