---
title: "Ubuntu 11.04- Wifi suddenly stopped working"
date: 2011-05-23
forum: General Help
---

### Post by Poopsi on 2011-05-23
I have an asus EEE 1015N. Everything worked fine yesterday. I packed my computer, and went back home. After turning it back on, not only it didn't connect to the wifi network, but it did not even detect it. I know it's not broken or anything like that because when I boot into windows it works fine.

I've been trying every solution given in the "sudden wifi problems" threads in the forum (including checking the wifi power button, and trying to manually  assign an access point to it), but to no avail. Any ideas?

---

### Post by Poopsi on 2011-05-23
update: I get this from nm-tools




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcm80211
  State:             disconnected
  Default:           no
  HW Address:        48:5D:60:10:49:09

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:69:3E:FF

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by Poopsi on 2011-05-28
For what it's worth, while trying Linux Mint Debian, I've met with the same problem. Anyone have any idea on how to fix this?

---

### Post by sammiev on 2011-05-28
Have you rebooted for router yet? Remove the plug for 1 min and try it again as I have had the same problem as you. GL :)

---

### Post by grahammechanical on 2011-05-28
There are some terminal commands that might help.

```
cat /etc/network/interfaces
```This will tell you what is in a file called interfaces. You should see

> auto lo
iface lo inet loopbackand nothing else. If there is anything else in there then edit it out and reboot. I did this last night with an installation of Ubuntu Studio and it fixed my problem getting any connection (wired or wireless) to the router. You will need to open gedit with the command

```
sudo gedit
``` then browse to the filesystem etc folder and then the network folder and open the interfaces file.

```
rfkill unblock wifi
``````
sudo ifconfig wlan0 down
``` followed by ```
sudo ifconfig wlan0 up
```I think that the reasoning is that it is best to take down the wireless adapter and then take it up.

```
 lshw -C network
```

This will show one of four states. Claimed = driver loaded but not functioning. Unclaimed = no driver loaded. You may need to go to additional drivers or install Ndiswrapper. Enabled = driver loaded. So check the connections to the router. Disabled = Well, it says it all.

See if these things help.

Regards.

---

### Post by Poopsi on 2011-05-29
Update: I'm wondering if this is related to this bug 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677)

Nonetheless installing the old driver didn't work by itself. However, maybe the other stuff I did before interfered. Any ideas?

Edit: also: It seems more related to extreme slowness and/or packet loss than outright non-function. It does detect a nearby wifi (not my own)
Worth noting again that I know that the wifi router works flawlessly, because when I boot onto windows or ubuntu 10.10 I can connect without problem.
(the problem is that I worry about not being able to upgrade ubuntu versions ever again)

---

### Post by rguerra on 2011-06-10
Hi,

I have the same problem under Lucid Lynx. Just switched on and off the pc. Yesterday I could detect the wifi. Today I can't. Didn't do anything in between. There is a detail however, that might be a clue: yesterday I had a crash in the sequence of a recurrent problem with highlighted text (sometimes the cursor becomes blocked in the highlight text function and blocks the whole system: can't do anything other then press the power button and shut down). However, I rebooted the pc and had wifi internet as usual. Then I shut down at the end of the day and restarted today. And today I have no wifi.

I have checked the command

cat /etc/network/interfaces

It works as expected. The output is

auto lo
iface lo inet loopback

Then I have used

rfkill unblock wifi
sudo ifconfig wlan0 down
And apparently had no problem:

guerra@rguerra-laptop:~$ rfkill unblock wifi
rguerra@rguerra-laptop:~$ sudo ifconfig wlan0 down
[sudo] password for rguerra: 
rguerra@rguerra-laptop:~$ 

But then, in the last command there is a problem:
rguerra@rguerra-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Invalid argument
rguerra@rguerra-laptop:~$ 

The result of

lshw -C network is DISABLED:

rguerra@rguerra-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:38:0e:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:fcffe000-fcffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:7d:ea:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.10.2 latency=0 multicast=yes
       resources: irq:31 ioport:e800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6fe0000-f6feffff(prefetchable) memory:fdef0000-fdefffff(prefetchable)

By the way, issuing the command

iwconfig


gives

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Is it possible to help me with these informations?

Thanks,

Rui

---

### Post by rguerra on 2011-06-12
Hi again,

Just for the case somebody has the same problem and comes to this discussion, here's what I found:

1. This problem appears to affect lots of users.
2. I couldn't spot a simple solution. Most of the discussions I found finish without an "happy end".
3. The solutions I tried to follow are not easy and depend on not so easy matters as configuring boards, etc. Even so, in most cases this is not helpful.
4. I think there is here a unidentified bug that ubuntu developers should seek. Apparently this bug is not restricted to a specific version: I had it 10.04, but other users report similar problems. For instance, the beginning of this discussion started with a 11.04 user.
5. I solved my problem upgrading from 10.04 to 10.10.
6. I hope the problem does not repeat - I just have one more upgrade to use!

Rui

---

### Post by slug45 on 2011-06-18
Hi there,
I've having this problem which forced me to go back to 10.10, but I spared some more time and found a workaround.
I have an  Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01) which works by installing linux-firmware-nonfree on 10.10, but it doesn't on 11.04.
I found this [post]("http://www.jrhenkelmann.net/index.php?option=com_content&task=view&id=34") and I tried his solution. I had to install 2.6.38-10-generic and the nvidia drivers from xorg-edgers and upgrade the system a couple of times with a wifi-usb adapter and reconfigure xorg (nvidia-xconfig).

Now, finally, I have 11.04 with 3d and wifi :).

Try upgrading the kernel, but not to a very recent version because it can broke other things (like the nvidia privative drivers).

---

