---
title: "Ubuntu Karmic Koala No Wireless with Gateway NV52"
date: 2009-11-11
forum: General Help
---

### Post by Native Dialect on 2009-11-11
I recently switched from Jaunty to Karmic via Ubuntu Studio. I have a Gateway NV52 laptop, which has an Atheros wireless card. I have tried various methods posted on these forums and other forums, and none of yielded the results I hoped for. I have tried downloading Madwifi (various versions) and have tried using sudo commands I found online, and still no luck. 

Is there no way to use sudo apt-get to have it instantly install MadWifi? Is there some other known issue for 9.10 and the latest Atheros card? I need help getting my wireless up and running. It is the only thing holding me back from switching completely over to Ubuntu rather than dual booting with Windows Vista. Any help would be greatly appreciated.

---

### Post by steviefordi on 2009-11-11
Assuming your wireless is built in, post the results of:

```
sudo lspci | grep -i 'atheros'
```

and we'll try to work out what driver you need.

You probably need to blacklist the madwifi drivers and install the newer ath5k driver.
ath5k was included in a 'backport modules' package for 8.10 as described on this page:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
possibly in a similar package for 9.10.

---

### Post by Native Dialect on 2009-11-11
Here are the results 

09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Native Dialect on 2009-11-11
Bump

---

### Post by Crafty Kisses on 2009-11-11
You're probably going to have to blacklist the MadWifi drivers, and as stated above you might need the backports package, not sure what it's called in Karmic but I'm guessing it's the following:
```
linux-backports-modules-karmic
```
According to [this]("http://packages.ubuntu.com/karmic/linux-backports-modules-karmic") page, that is what the package is called.

---

### Post by Native Dialect on 2009-11-11
Gave that a shot and no dice. I went through synaptic to look for that particular package. Installed it. Still no wireless setup in my Network Settings. Any other ideas? And I am grateful to those who respond.

---

### Post by Native Dialect on 2009-11-12
Bump

---

### Post by Native Dialect on 2009-11-12
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lite-On Communications Inc Device 6600
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath9k


That is the important information about my wireless card.

---

### Post by steviefordi on 2009-11-12
Looks like you're using ath9k instead of ath5k.

Give this a shot...

```
sudo modprobe -r ath9k
sudo modprobe ath5k
```

If that works, you'll need to blacklist the ath9k driver.

By the way, I understand your frustration - the reason I'm helping you is that I had a similar problem with my Atheros card -  but I think forum rules dictate that you should only bump after 24 hours of unanswered post. Don't get yourself blacklisted.

---

### Post by Native Dialect on 2009-11-12
I entered that first command, and this is what I got

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 


Then I entered that second code, and this is what it said 

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

Does this mean that the ath drivers are already blacklisted? I have been using a lot of different online solutions and I believe that one of them may have already suggested a blacklisting of some drivers (not sure if they were ath or madwifi).Thank you so much for all of the help everyone. I have been using Ubuntu since Edgy, but I am still not that well versed yet. So it is a learning experience.

---

### Post by Native Dialect on 2009-11-13
This is not a bump. I just wanted to say that I gave up on Karmic Koala for now and downgraded to Jaunty Jackalope. It actually has the drivers for my wireless card and offers better compatibility throughout. Hopefully by the time Lucid Lynx arrives, they will have worked out things for Karmic. Thank you for all of those who contributed to the trouble shooting situation, but it seems to be a far more complicated situation than originally thought.

---

### Post by steviefordi on 2009-11-13
I'm glad you're finally sorted. It did look like you were in some sort of blacklist hell. Not only had you dabbled with all three Atheros drivers (madwifi, ath5k and ath9k) but looks like you'd had a dip into NDISWrapper as well.

I had similar problems getting my Atheros wireless card going. Trouble is there is so much old information on the net, if you don't fully understand what you're doing (which I didn't) you end up editing important configuration files in ways you don't understand. Then if you do find a blog or something which does have the right info on it, it won't work because of something you've followed previously.

Out of interest, what driver has Jaunty settled upon? It would be a good idea for you to know.

---

### Post by drpjkurian on 2009-11-14
> **Native Dialect said:**
> This is not a bump. I just wanted to say that I gave up on Karmic Koala for now and downgraded to Jaunty Jackalope. It actually has the drivers for my wireless card and offers better compatibility throughout. Hopefully by the time Lucid Lynx arrives, they will have worked out things for Karmic. Thank you for all of those who contributed to the trouble shooting situation, but it seems to be a far more complicated situation than originally thought.

Hi
I am very sorry to hear that you have downgraded to Jaunty.
well you can try my thread for Madwifi installation.
Please visit my thread [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by Native Dialect on 2009-11-15
> **steviefordi said:**
> I'm glad you're finally sorted. It did look like you were in some sort of blacklist hell. Not only had you dabbled with all three Atheros drivers (madwifi, ath5k and ath9k) but looks like you'd had a dip into NDISWrapper as well.

I had similar problems getting my Atheros wireless card going. Trouble is there is so much old information on the net, if you don't fully understand what you're doing (which I didn't) you end up editing important configuration files in ways you don't understand. Then if you do find a blog or something which does have the right info on it, it won't work because of something you've followed previously.

Out of interest, what driver has Jaunty settled upon? It would be a good idea for you to know.

I am guessing that is what happened. Somewhere along the line of using three different driver solutions, I created some blacklist loophole of doom. But I am okay with Jaunty. It is stable and runs like a dream. And as for the driver that Jaunty uses to run my Atheros card, it uses ath9k. 

*-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:5f:fb:e9:71
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

---

### Post by disciplefk on 2010-04-25
This is a little bit of a hijack, I have a gateway NV52.  The wireless currently works ok, with minimal trouble (coming out of hibernate is always an issue it seems) but there is an issue with the computer freezing.  I have the same trouble in windows, but the problem was fixed by updating my NIC drivers.  So I assume finding alternative Atheros drivers in ubuntu will also resolve the problem.  Any advice?

---

