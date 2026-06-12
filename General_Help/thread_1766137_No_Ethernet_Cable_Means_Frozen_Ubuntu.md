---
title: "No Ethernet Cable Means Frozen Ubuntu?"
date: 2011-05-24
forum: General Help
---

### Post by imasynper on 2011-05-24
I installed Ubuntu 11.04 on my girlfriends laptop a couple days ago...had the Ethernet cable plugged in to do the install...loaded fine the first time after the install. Unplugged the Ethernet cable when I had the wireless network set up and it froze. Restarted and it wouldn't even load the desktop. Didn't make the connection at first...thought there was something wrong with Unity. After about a day and a half worth of searching Unity problems/desktop freezing and solutions, I stumbled across this: 
> **NormanFLinux said:**
> Do you have a Broadcom card? You have  probably noticed the desktop works when you run Ethernet but it locks up  when your wireless connection is active. 

You'll need to upgrade the kernel to fix the issue. 2.6.39.0 did it for me.

11.04 just runs fine now.
This solution was to update the kernel, but that didn't work for me. Now I'm stuck.

---

### Post by imasynper on 2011-05-24
It seems today I can't re-create the same scenario that was  happening yesterday. Now I can't log into normal Ubuntu(with unity) at  all. Regardless of whether the ethernet cable is plugged in or not. I can log into Ubuntu Classic(no effects) but if I try to use wireless, it connects for about 2 minutes, then disconnects and won't reconnect. Are these 2 separate issues? Or is it all the same? Ideally I'd like to be able to use the Unity desktop, but if for whatever reason I can't, I at least need a reliable wireless network.

---

### Post by enimeizoo on 2011-05-24
Well, it is probably not the best advice, but 11.04 is still buggy, so you might consider installing a previous version instead... (10.10 or even 10.04, that probably would save you time and efforts) Or maybe just a different desktop (kde is really nice, by the way).
I also had a wifi issue, I solved it by installing wicd and then uninstalling network-manager. It worked fine after a reboot.

---

### Post by coffeecat on 2011-05-24
@imasynper, in the space of this very short thread you seem to have been subjected to two generalisations which may not be helpful in your particular situation. The quote that you post in your first post may very well be true for that person's particular Broadcom card and driver combination (there are at least three different Broadcom wireless drivers and about a dozen or more Broadcom wireless chipsets), but is not true for everyone. For example, Natty and Unity run just fine on my HP netbook with a Broadcom wireless card. Wireless works well and doesn't cause lockups.

You haven't said whether you have a Broadcom wireless card and, if so, which one. Let's find out. You can't troubleshoot wireless without knowing exactly which chipset you have. Open a terminal and post the output of:

```
sudo lshw - C network
```Next, the previous poster said that 11.04 is buggy. That's a bit like saying food doesn't taste nice. It depends on the particular food and the preferences of the taster! Similarly with Natty. All software has bugs. Some people are experiencing bugs which they can't live with; others not. I have Natty running sweetly on four different machines. Is it buggy for me? No. Is it buggy for some? Of course. So instead of writing off Natty for you just yet, let's look a little further into your problems and hardware.

You ask, "Are these 2 separate issues?" I don't know. They could be related, or they could be quite separate issues. Let's investigate the lack of Unity. A good place to start is with your graphics card/driver combination. While you have the terminal open, post the output of:

```
sudo lshw -C display
```

---

### Post by imasynper on 2011-05-24
Thanks for the replies. @enimeizoo Thanks for the tip on WICD...installed it and it works much better then network manager, but my wireless still drops out.  With WICD I can at least reconnect. @coffeecat I was aware that I was making generalizations, but after A LOT of searching, general is all I could find haha. I do have a broadcom wireless card, but here's the info for you:

```
~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:62:13:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:e2:24:e3
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)

``````
~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff
```

---

### Post by coffeecat on 2011-05-25
@imasynper, oh no, I didn't intend to imply that you had made generalisations. :) I meant that you had been the recipient of generalisations.

Anyway, to practical issues. Re-reading your first two posts again, it seems that you only had the freezing at first, but that subsequently you do seem to have 2 separate and unrelated issues, namely: wireless is unstable, and you can't  log in to Unity.

You have the Broadcom BCM4312 card which I don't have direct experience of. However, there is a long thread here which might have something for you:

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

It starts as an "unable to download firmware" but widens out to a larger discussion about various Broadcom cards with some fixes. This next may not add anything for you, but it is a useful documentation page for Broadcom wireless:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Your X1200 graphics card is fairly long in the tooth now and is no longer supported by ATI in the proprietary driver, so you are limited to the open source radeon driver which you are already using. However, according to this...

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

... your card should be capable of 3d acceleration with the radeon driver. That means it should be capable of running compiz = capable of running Unity. Which it clearly did at first. 

A thought: when you first experienced a freeze, you said you restarted and it was then that it wouldn't load the Unity desktop. How did you do the restart? If it was a forced power-down, some filesystem damage could have been caused and this might explain the failure to load Unity. Also - in that day and a half of searching did you try any other configuration changes?

---

### Post by NormanFLinux on 2011-05-25
Since you upgraded the kernel, try this with your Broadcom wireless driver. Uninstall bcmwl-source kernel and install b43fwcutter, firmware b43-installer. Both of those packages should give you a working wireless Internet without freezeups. Install them both and see if you can log in without needing an Ethernet connection.

---

### Post by imasynper on 2011-05-25
Ya I would think that Unity should work, I had 10.10 running previous to this and I had compiz running at full. As for the power down I switched to the console(ctrl-alt-f1), and rebooted. And no I didn't try any other changes...just updated the kernel.

@NormanFLinux tried your suggestion, but got an error trying to install that driver. Coincidentally, coffeecat's first link provided the solution for that, so I installed the firmware-b43-lpphy-installer instead, which didn't give me an error, but unfortunately didn't fix the problem.

---

### Post by imasynper on 2011-05-27
Anyone have any more suggestions? Even if just to get wireless working properly. The dropping out is getting tiring.

---

