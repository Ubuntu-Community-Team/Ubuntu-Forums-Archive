---
title: "Wifi Problem"
date: 2012-08-04
forum: General Help
---

### Post by Miss on 2012-08-04
Hi all

This is my computer

[http://www.cnewindow.com/101-inch-3g-tablet-pc-phone-with-windows-7-capacitive-screen-intel-n450-166gmhz-2g-160g-memory-p-2309.html](http://www.cnewindow.com/101-inch-3g-tablet-pc-phone-with-windows-7-capacitive-screen-intel-n450-166gmhz-2g-160g-memory-p-2309.html)

I have made it duel boot however I cannot get the wifi and touch screen working.

Can anyone help me resolve this please

Many thanks

---

### Post by Dylan1473 on 2012-08-04
Unfortunately I don't know anything about touch screens. What is wrong with your wifi?

---

### Post by drifterpaul on 2012-08-04
Hi Dylan1473,

The wifi on my friends tablet is not picking up the wifi signal at all. When we use the Ethernet cable, no problems. I'm thinking the ubuntu isn't recognizing the wifi card?

Best,
Paul

---

### Post by Dylan1473 on 2012-08-04
Well, I've never used a tablet before so I'm embarassed to admit I'm not sure how it works with typing and such - do you have like a mouse and keyboard hooked up to it so you can do terminal commands? If so, please open up a terminal, type the following commands, and post the output to each.

```
lspci | grep Network
``````
sudo iwconfig
```and maybe

```
sudo ifconfig
```though I only need to see the output for the wlan section for that one.

---

### Post by drifterpaul on 2012-08-04
Hi Dylan,

No probs I'll get that done it is wired to a keyboard & mouse.

Best,
Paul

---

### Post by drifterpaul on 2012-08-04
> **Dylan1473 said:**
> Well, I've never used a tablet before so I'm embarassed to admit I'm not sure how it works with typing and such - do you have like a mouse and keyboard hooked up to it so you can do terminal commands? If so, please open up a terminal, type the following commands, and post the output to each.

```
lspci | grep Network
``````
sudo iwconfig
```and maybe

```
sudo ifconfig
```though I only need to see the output for the wlan section for that one.

Hi Dylan,

This is the result

kayperry@kayperry-laptop:~$ lspci | grep Network
kayperry@kayperry-laptop:~$ sudo iwconfig
[sudo] password for kayperry: 
lo        no wireless extensions.

eth0      no wireless extensions.

kayperry@kayperry-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:36:01:75  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe36:175/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2258290 (2.2 MB)  TX bytes:182631 (182.6 KB)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:232166 (232.1 KB)  TX bytes:232166 (232.1 KB)

kayperry@kayperry-laptop:~$

---

### Post by Dylan1473 on 2012-08-04
Well, that's not good. Try typing:

```
sudo ifconfig wlan0 up
```to see if that helps.

Also, please just type

```
lspci
```and post the full output to that in code tags. There'll be a lot of it. I'm hoping you just happen to have a network card that doesn't have "Network" in the name rather than Ubuntu not recognizing it. Otherwise, you might have to install some new drivers, if you can get it to work at all. You can hook it up to ethernet if necessary right?

---

### Post by steeldriver on 2012-08-04
you could also do 

```
lshw -C network
```which doesn't rely on matching a particular device name string - and also gives some driver and firmware info

---

### Post by drifterpaul on 2012-08-04
Hi Dylan,

I don't think it looks too good :( also I'm not sure what code tags are, sorry, but this is what I got from the terminal.

kayperry@kayperry-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for kayperry: 
wlan0: ERROR while getting interface flags: No such device

kayperry@kayperry-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
kayperry@kayperry-laptop:~$

---

### Post by Dylan1473 on 2012-08-04
I don't think lshw comes installed by default, does it? This would actually be really helpful, but it maybe requires you have a working internet connection of some kind. You can install it through the terminal with

```
sudo apt-get install lshw
```I believe. It might be installed by default on a full install though. I know I don't have it, but mine is built up from a minimal install.

EDIT: Code tags are the little asterisk icon when you're creating your post, it puts text in a little box which will scroll if it gets too big so that large outputs don't take up too much space. It's considered good practice with log files and such. There was less there than I was expecting anyway so it doesn't really matter.

---

### Post by drifterpaul on 2012-08-04
> **steeldriver said:**
> you could also do 

```
lshw -C network
```which doesn't rely on matching a particular device name string - and also gives some driver and firmware info

This is what I got, I haven't a clue to what a superuser is tho. 

kayperry@kayperry-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
                    
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:36:01:75
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:e800(size=256) memory:febdf000-febdffff memory:fdff0000-fdffffff memory:febe0000-febfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
kayperry@kayperry-laptop:~$ 

I'm just going to install the other part you mentioned and see if it will.

---

### Post by drifterpaul on 2012-08-04
This is what we got.

kayperry@kayperry-laptop:~$ sudo apt-get install lshw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 345 not upgraded.
kayperry@kayperry-laptop:~$

---

### Post by Dylan1473 on 2012-08-04
That command wouldn't have worked if lshw wasn't installed, I guess it is there by default. In any case, to run as superuser you just need to put sudo in front, like so:

```
sudo lshw -C network
```

I'm seeing no wireless adapter so far, hopefully that helps. The product page you linked to unfortunately doesn't say anything about the wireless adapter beyond "supports 802.11b/g/n" and doesn't provide a model number or anything so I'm not sure I can find the chipset.

---

### Post by drifterpaul on 2012-08-04
> **Dylan1473 said:**
> That command wouldn't have worked if lshw wasn't installed, I guess it is there by default. In any case, to run as superuser you just need to put sudo in front, like so:

```
sudo lshw -C network
```I'm seeing no wireless adapter so far, hopefully that helps. The product page you linked to unfortunately doesn't say anything about the wireless adapter beyond "supports 802.11b/g/n" and doesn't provide a model number or anything so I'm not sure I can find the chipset.

Well this is what we got, but my friend got the tablet from ebay and from China with no tech details not even a userman

kayperry@kayperry-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:36:01:75
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:e800(size=256) memory:febdf000-febdffff memory:fdff0000-fdffffff memory:febe0000-febfffff
kayperry@kayperry-laptop:~$

---

### Post by Dylan1473 on 2012-08-04
Wireless chipsets are often not listed or occasionally even falsely listed (most likely unintentionally, of course, it's just that things can be tricky around them). It really looks as though Ubuntu is not recognizing your card. It may be possible to fix it by installing some new drivers but I don't know how you'd go about learning which without knowing the chipset. You might be able to figure it out from Windows, though I'm not sure how.

I may have one last potential solution, give me a moment to look into it and I'll either edit this post or post a new one.

---

### Post by drifterpaul on 2012-08-04
No probs Dylan, she's connected to the www via cable at the moment. If your solution doesn't work it may be a case of taking it to a shop to get them to find out the chipset or just getting a usb wifi key.

---

### Post by Dylan1473 on 2012-08-04
Okay. Most usb adapters should work. As should most internal ones, for that matter. I have an older high powered alfa AWUSO36h on the rtl8187 chipset which works beautifully but it's 802.11b/g only, you'll probably want something with 802.11b/g/n support. Atheros cards are also known to be really well supported.

So, here's my last potential solution, and I'm not sure what consequences it might have or if maybe it's already there or what. This is something I've never had to do before (at least not on this level) nor am I 100% certain I'm telling you to do it right. So for sure exercise extreme caution, maybe wait for someone to happen along to second if this will help or if it's necessary or whatever.

Wifi in Linux is under constant development and Ubuntu isn't the most cutting edge distribution (for which there are very excellent reasons; it allows for things to be tested before they're released to regular users). Basically, you can install more up to date drivers if you want. They could be glitchy though and it's not something I understand very well. This is the command I believe you'd have to give:

```
sudo apt-get install linux-backports-modules-cw-3.3-3.2.0-24-generic
```You'll likely have to reboot afterwards (or restart several services, but it'd probably be simpler just to reboot).

that should install some new wireless drivers if I've got the right package. Even if the installation goes perfectly there's no guarantee it will resolve this problem. And I'd just like to stress, again, that I really barely know what I'm doing here. Hopefully the new drivers will allow your card to be recognized. And hopefully it doesn't mess up your system so bad you end up having to reinstall Ubuntu or something. At least the package name will always be recorded here so you know what to uninstall if it messes things up.

---

### Post by drifterpaul on 2012-08-04
Many thanks for that, I'll speak to my friend and see what she want's to do, gonna be a long night I think :) 

Thanks again
Paul

---

