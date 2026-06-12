---
title: "Networking help"
date: 2011-07-27
forum: General Help
---

### Post by wanttomasterlinux on 2011-07-27
Hey everybody,
I have nearly-mastered windows and got a good grasp of MAC but I am an absolute beginner of Linux. Just installed Ubuntu couple of days ago. Linux is interesting but it really freaks out beginners unlike windows. My internet connection(Wifi) doesn't work, my best guess is that driver is not installed. I downloaded Linux-compatible driver but I have no idea how to install it, even after watching lots of crappy tutorials on the Youtube. Most experienced users fail to understand that, WE ARE BEGINNERS DOESN'T MEAN THAT SOFTWARE CENTER WOULD ALWAYS WORK FOR US!!! in fact, as far as I know, we don't use software center for third party software and it requires internet (well.......did I mention I wan't to install WLAN driver?) ;)
I am using Dell Inpiron 6400 and my Wlan card is dell Wlan mini 1390 (1395...)
Any help would be greatly appreciated but do understand that I am an absolute beginner. It would make life easier for me my friends :D

Cheers!

---

### Post by linuxuser12345 on 2011-07-27
> most experienced users fail to understand that, we are beginners doesn't mean that software center would always work for us!!! ^like!!^ :)

---

### Post by SoulTechnologist on 2011-07-27
What Ubuntu distro are we talking about? If you do installed it a couple days ago from the website I immagine it is the 11.04 is that correct? Then, how did you installed it, was it from a Live CD?

---

### Post by wanttomasterlinux on 2011-07-27
waoow, that was quick! ;)

Ubuntu - kernel 2.6.38
11.0x (something)

---

### Post by madhu542 on 2011-07-27
I am using 11.04, fyi there is no need of installing any network drivers once you install ubuntu, unlike in Windows.

Check list:
1. Network card.
2. Ethernet cable is properly plugged or not.

Open a terminal and check the following commands...

$ ifconfig

To see whether eth0 exists or not, if exists restart the networking to get the IP on eth0.

$ cat /etc/network/interfaces

If you couldn't see the following below information try to add these lines in that file using super user (root)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

Later restart your networking (or system) using

$ /etc/init.d/networking restart


for wifi:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by SoulTechnologist on 2011-07-27
madhu542 was quicker!!! Thank him!! And let us know if everything works fine...

---

### Post by wanttomasterlinux on 2011-07-27
Thanks to both of you for replying :)
@madhu, Newer versions of windows (from Millennium) automatically detect all the required drivers
anyways, I am actually talking about Wireless LAN here
I use Dell Inspiron 6400 and my Wlan adapter is Dell mini-PCI 1390
I used ipconfig and it shows my eth0 (does that mean the driver is installed?)
But again I want to use WiFi rather then Wired
I'll use the other code once you tell me to after considering that I want Wifi or Wlan

Thanks again :)
takecare

---

### Post by wanttomasterlinux on 2011-07-27
Here's more information that might help to solve the problem
on typing.........
**sudo lshw**
{Content trimmed}

*-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:16 memory:efcfc000-efcfffff

{Content trimmed}

*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:a0:59:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic fir

as you can see, it identifies my wlan device and uses a driver named b43, but then it says in the end and network is DISABLED!!! grrrrh

I tried to enable it by using the commmad **sudo modprobe b43** (b43 is the name of the driver used by linux), then i checked again using.....

lsmod

Module                  Size  Used by
b44                    35301  0 
arc4                   12473  2 
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
parport_pc             32111  0 
ppdev                  12849  0     

good, it shows the module b43 is loaded successfully

then typed


**lshw -c network**

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff

network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:a0:59:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic fir
 

same thing again, it tells me that **"your Wlan device is working perfectly fine, but wait..........actually its not working, you have disabled it sir"**  , I just have one thing to say, "wtf is wrong with ya bloody damn laptop" 
Apologies, I sometimes curse my laptop, we understand each other :)

plzzz helppppppppppppppppp :(

---

### Post by varunendra on 2011-07-29
> **wanttomasterlinux said:**
> 
**sudo lshw**

*-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                **physical id: 0**
..
..
..
*-network **DISABLED**
       description: Wireless interface
       **physical id: 1**
       logical name: wlan0
I'm not sure, but it seems that you have two on/off switches for your wifi- one physical and one software based, and perhaps the software based one is switched off. If so, then I doubt that you and your lappy properly understand each other.. ;)

Please post the output of:
```
rfkill list all
```also:
```
iwconfig
```Let's hope it's not a big one. Here's a link you may find interesting if you doubt your drivers: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
(and I believe I do understand beginners, you seem a good one :)).


**PS:**
As a side note, whenever you post an output (especially long ones, but anyone in general), you should wrap it in 'code' tags. To do so, just select the pasted output text and click on the '#' symbol at the top of editing box. It makes the output look well formatted and easier to read.

---

### Post by westie457 on 2011-07-29
Run this in a terminal ```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer

``` you will be asked for your password. When typing nothing will show on the screen.

Then open Synaptic search for bcm and mark all the results with a green box for complete removal except for the two that you installed. A quick reboot will get your wifi up and running.

---

### Post by wanttomasterlinux on 2011-07-29
@Vanunendra Well you might be right, but I rather think my gadg didn't like the fact that I installed Linux when he was quite up and running happy with Windows!! ;)

here you what u asked for
ottoman@ottoman-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
ottoman@ottoman-MM061:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ottoman@ottoman-MM061:~$ 

Looking at the output, I think you would be surprised with the first as it make everything look fine. The second output is even more surprising coz it doesn't show my Wlan at all

---

### Post by wanttomasterlinux on 2011-07-29
@westie it says that b43-fwcutter is not found! :(
any other solution?

---

### Post by westie457 on 2011-07-29
> **wanttomasterlinux said:**
> @westie it says that b43-fwcutter is not found! :(
any other solution?

That is strange because that driver has been Ubuntu as non-free for at least 3 years and is in the repo's. Just to be on the safe side so you can get it open Synaptic go to Settings > repositories.
In the first tab of the window 'Ubuntu Software' check all the boxes except 'source code'. Next tab 'Other Software' check all of them, click on close. Dialogue window opens letting you know that sources have changed and need to be reloaded. Click on Okay, then click on reload. Now search for b43-fwcutter and then install it. Any problems come back here and we will try again.


===============================================================================================================
Another way to get b43-fwcutter is from the LiveCD. You will find the .deb package under /pool/main/b/b43-fwcutter double-click on it and install through the Software Centre.

---

### Post by varunendra on 2011-07-30
> **wanttomasterlinux said:**
> 
ottoman@ottoman-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ottoman@ottoman-MM061:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ottoman@ottoman-MM061:~$ 

Looking at the output, I think you would be surprised with the first as it make everything look fine. The second output is even more surprising coz it doesn't show my Wlan at all
Surprising indeed! Please post output of:
```
dmesg | grep -Ei "wlan|net|b43|b44"
```

And for the moment, try what westie457 suggested.

---

### Post by wanttomasterlinux on 2011-07-31
> **varunendra said:**
> Surprising indeed! Please post output of:
```
dmesg | grep -Ei "wlan|net|b43|b44"
```And for the moment, try what westie457 suggested.

hey, my wireless is working now, can you please how do i reinstall wireless tools?? (the one which allow you to use iwconfig )???

I am loving tinkering with linux! plzzz help ;)

---

### Post by varunendra on 2011-07-31
> **wanttomasterlinux said:**
> hey, my wireless is working now, can you please how do i reinstall wireless tools?? (the one which allow you to use iwconfig )???

I am loving tinkering with linux! plzzz help ;)
Use synaptic package manager. Type 'wireless-tools' in the search box and it should get listed. Choose to 'Completely Remove' it, apply, then reinstall.

---

