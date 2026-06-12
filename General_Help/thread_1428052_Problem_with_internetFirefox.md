---
title: "Problem with internet/Firefox"
date: 2010-03-12
forum: General Help
---

### Post by maedhros777 on 2010-03-12
Hello. I'm new to Linux, and I recently decided to try out Ubuntu. I used the Wubi installer so it's on Windows (just to see if I liked Ubuntu) and it works fine, but with one exception: the internet (or maybe just Firefox) isn't working. The internet connection worked just fine on XP. On Ubuntu, it says that it was able to connect to the wireless network, but when I try to go to any page on Firefox it just keeps trying to load perpetually and never connects to the site, eventually just showing the "Server not found" page. Any help will be greatly appreciated.

---

### Post by coffeecat on 2010-03-12
A question first. What make/model wireless-router do you have, and how old is it?

Next: a diagnostic test. This problem often used to be caused by IPv6 issues where the router firmware was old. This shouldn't be a problem these days, but let's check it out anyway.

In firefox, type 'about:config' (no quotes) in the address bar. Dismiss the 'here be dragons' warning and type 'ipv6' (again, no quotes) in the filter. You should see just one line: "network.dns.disableIPv6'. Change the value to true by clicking on it. Restart firefox and see if that makes any difference.

If it does, we need to do some more investigation. If not, then there are other things to look at.

---

### Post by maedhros777 on 2010-03-12
I tried disabling ipv6, but Firefox still isn't working, unfortunately. I also went and checked my wireless router and it's a Linksys router, wireless-g broadband. I'm not really sure how old it is.

---

### Post by coffeecat on 2010-03-12
Despite what the GUI is telling you, let's make sure it really is connecting to the router.

Open a terminal (Applications > Accessories) and post the output of:

```
sudo ifconfig
```When it prompts you for your password (it means your login password) it doesn't look as though anything is going in when you type. It is. That throws a lot of people.

Since you haven't got internet connectivity in Ubuntu, copy and paste the output to a text editor (Applications > Accessories > Gedit) and copy the saved file to a USB stick so that you can post it from Windows. Make sure you add the filename extension .txt otherwise Windows will not open it. And when you open it in Windows, try both Notepad and Wordpad. There are different conventions for text files between Windows and Unix systems and one of those two will display your gedit file all on one line - I can't remember which offhand.

Also, while still in Ubuntu and with the terminal open, try:

```
ping 192.168.1.1
```That's the internal address for a Linksys router. If you're connected the router will respond. If not, not.

---

### Post by maedhros777 on 2010-03-12
Here's the output from "sudo ifconfig":
 
```
 
eth0 Link encap:Ethernet HWaddr 00:13:20:17:34:0e 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:208 errors:0 dropped:0 overruns:0 frame:0
TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:20514 (20.5 KB) TX bytes:20514 (20.5 KB)
wlan0 Link encap:Ethernet HWaddr 00:1c:df:68:5b:fc 
inet6 addr: fe80::21c:dfff:fe68:5bfc/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:2935 errors:0 dropped:0 overruns:0 frame:0
TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:360841 (360.8 KB) TX bytes:55649 (55.6 KB)
wmaster0 Link encap:UNSPEC HWaddr 00-1C-DF-68-5B-FC-36-38-00-00-00-00-00-00-00-00 
UP RUNNING MTU:0 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```
 
I also tried pinging the router like you said, but I guess it's not connected because it just says:
 
```
connect: Network is unreachable
```

---

### Post by maedhros777 on 2010-03-12
Actually, I just realized that it doesn't even say that I'm connected to the network anymore. I tried reconnecting but it asks for the WEP key and when I enter the key, it just keeps trying to connect and then asks for the key again, repeating indefinitely. ](*,) This is getting pretty frustrating.

---

### Post by coffeecat on 2010-03-12
Yes, not connected. The ifconfig is not easy to read but, if you look under the wlan0 part (wlan0 is code for your wireless device), you'll see there's no assigned IP address, which would be 192.168.1.64 or thereabouts with a Linksys router. Which confirms the failed ping.

OK, let's go back to basics. What is your wireless network device? Is it a PCI card, USB card or inbuilt laptop card? In fact, are you using a desktop or laptop? When you click on the network manager icon near the top-right (usually next to the audio volume icon), can you see your wireless network? If you can, when you click on your wireless network, does it prompt you for your passkey?

If you don't see your network this way, open a terminal again. If your wireless device is a PCI card or a laptop inbuilt, try this command:

```
lspci
```Look for the line with "Wireless" and/or "802.11" in it and post it as before. This way we can see what your wireless chipset is - important if there are driver issues to deal with.

If it's a USB device, try:

```
lsusb
```and post the lot.

Can you connect your machine to the router with an ethernet cable? If so, try that and it should connect automatically. I know you won't want to do that routinely, but it would get you connected to get this issue sorted out. It'll make it easier posting those terminal outputs. It would also get you connected to do some software updates which might be a good idea anyway.

---

### Post by coffeecat on 2010-03-12
> **maedhros777 said:**
> Actually, I just realized that it doesn't even say that I'm connected to the network anymore. I tried reconnecting but it asks for the WEP key and when I enter the key, it just keeps trying to connect and then asks for the key again, repeating indefinitely. ](*,) This is getting pretty frustrating.

I hadn't seen that when I posted just now. OK, it's seeing your network but not connecting. Post the terminal outputs I suggest and also the answers to the questions.

One other question: why WEP and not WPA?

---

### Post by maedhros777 on 2010-03-12
Okay, so when I click on the Network Manager icon it has the network listed, but when I scroll over it there are two options: "linksys" and "Auto linksys" (the network name is "linksys"). When I click on either of them, it endlessly asks for the WEP key (I don't know why it's not WPA, it just asks for WEP and I know the network's WEP key).
 
Also, my computer isn't a laptop, but I don't know if it's PCI or USB. So I tried both of the commands in the terminal, and didn't see "Wireless" or "802.11" in "lspci", here's the output:
 
```

00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
04:02.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)

```
 
And here's the output from "lsusb":
 
```

Bus 001 Device 004: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 003: ID 050d:8053 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
 
Unfortunately I don't know where an ethernet cable is. I probably have one around somewhere, I'll look for it.

---

### Post by coffeecat on 2010-03-12
> **maedhros777 said:**
> I don't know if it's PCI or USB.

....

And here's the output from "lsusb":
 
[CODE]Bus 001 Device 003: ID 050d:8053 Belkin Components

It's a USB. In fact, you should be able to tell. There'll be a USB dongle attached to the machine somewhere with "Belkin" printed on it.

OK, I've googled "050d:8053" and the news is mixed. That's the device ID code. According to [this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB") it worked out of the box in Jaunty (9.04) but not in Karmic, but doesn't give any further information. Which I find decidedly odd, since that card seems to be N-capable, therefore a fairly recent one.

And according to [this link]("http://www.linuxmint.com/wiki/index.php/Linux_Mint_friendly_Wifi_cards") you will need ndiswrapper, which will be fun. :?

> **maedhros777 said:**
> (I don't know why it's not WPA, it just asks for WEP and I know the network's WEP key).

The encryption type (WEP or WPA) is determined by the router. You (or someone) must have chosen WEP when the router was first set up. The reason I queried this is because WEP is now fairly easily cracked. If you have a WPA-capable router and wireless card you are better with WPA. Anyway, that's a bit theoretical at the moment.

I have no experience of ndiswrapper. I've been lucky in that I have nearly always chosen wireless devices (several of them) which have 'just worked' in Linux. Usually better than in Windows. May I suggest you start a new help thread in the Networking and Wireless forum, [here]("http://ubuntuforums.org/forumdisplay.php?f=336"). That way you'll get noticed by the wireless experts - hopefully. Link this thread in your post and give the relevant information we've managed to obtain already. Particularly the lsusb output and that fact that the device ID is "050d:8053 Belkin" and that according to what's turned up courtesy of Google, the chipset is probably Ralink RT2870. See [here]("http://cateee.net/lkddb/web-lkddb/RT2X00.html"). Knowing the chipset is most important when troubleshooting wireless issues.
 
Lest you think that wireless is usually a problem (outdated information on the net suggests it is), most wireless devices just work out of the box in Ubuntu. I'm afraid you've been unlucky.

I hope it gets sorted.

---

### Post by maedhros777 on 2010-03-12
Okay, I guess I'll try out ndiswrapper. Hopefully that'll work, but if not I'll try the forum you suggested. Too bad this whole thing happened, I was afraid I wasn't going to be able to use Ubuntu.
 
Anyway, thank you so much for your help. I never would have been able to do this by myself. :)

---

