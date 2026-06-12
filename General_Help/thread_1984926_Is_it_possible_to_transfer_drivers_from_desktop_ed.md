---
title: "Is it possible to transfer drivers from desktop edition to server edition??"
date: 2012-05-22
forum: General Help
---

### Post by RPGillespie on 2012-05-22
I have a wireless card that I want to use with ubuntu server edition. Only problem is, server edition doesn't have the right drivers to get the wlan card working. Ubuntu desktop edition does, however. In fact I'm using desktop edition right now. Is there a way I can pull the drivers from the desktop edition and put them into the server edition?

---

### Post by papibe on 2012-05-22
Hi RPGillespie.

No, but yes :D

If the Desktop Edition has the drivers is because either they were installed on the installation process, or later they were detected and downloaded.

In any case, it means they are on the repositories, thus available for install on the Server Edition.

Chances are they are already installed on your server as most network drivers are included in the kernel package (with some exceptions like PCMCIA cards).

I hope that helps, and tell us if you need more help with that.
Regards.

---

### Post by RPGillespie on 2012-05-22
I was able to find and connect to my network  on the setup screen for ubuntu desktop immediately after booting from the CD, whereas ubuntu server was unable to find any networks and was asking to try a specific SSID, etc., which didn't work.

How do I know which driver is being used for ubuntu desktop, and how can I get it from the repository onto ubuntu server? Is there an apt-get or something that would let me get the right one?

---

### Post by papibe on 2012-05-22
Run this on your Desktop running OK your wireless card:
```
sudo lshw -C network
```
Part of my output is this:
```
  *-network
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 5f
       serial: 00:23:15:7a:d5:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=[COLOR="Red"]iwlwifi[/COLOR]** driverversion=3.2.0-24-generic firmware=41.28.5.1 build 33926 ip=192.168.1.72 latency=0 link=yes multicast
```
There you can see that my driver is called iwlwifi. For more indormation about the driver you can run:
```
modinfo iwlwifi
```
From the first line you get the name of the file:
```
filename: /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/iw
lwifi/iwlwifi.ko

```
With that information you can check if it is on your server (it has to be the same version, i.e. 12.04).

I haven't find a command to get the actual package of the module/driver,  but you can get into: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and look for the file (package contains). In my case the driver can be found in several packages:
```
linux-image-3.2.0-23-generic-pae [not amd64]
linux-backports-modules-cw-3.3-3.2.0-23-generic-pae [not amd64]
linux-image-3.2.0-23-generic
linux-backports-modules-cw-3.3-3.2.0-23-generic
linux-image-3.2.0-23-lowlatency-pae [not amd64]
linux-image-3.2.0-23-lowlatency
linux-image-extra-3.2.0-23-virtual
```
I hope that helps, and tell us how it goes.
Regards.

BTW, if it is installed may be you just need to load it:
```
modprobe iwlwifi
```

---

### Post by RPGillespie on 2012-05-23
So I found that the driver being used is the ath5k driver for atheros chipsets, which I thought was included with the server edition. Turns out it is included with the server edition, I must've just missed something. 

Thanks for your help in identifying the driver, I appreciate it!

---

### Post by papibe on 2012-05-23
Great ):P

Just to add a little more info: instead of going, online you can check what installed package a file belongs by doing:
```
dpkg -S /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko

```
(note that I referenced the file using its absolute path).

In my case (12.04 Server):
```
**linux-image-3.2.0-24-generic-pae**: /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko

```
Regards.

---

### Post by dcstar on 2012-05-24
> **RPGillespie said:**
> I have a wireless card that I want to use with ubuntu server edition. Only problem is, server edition doesn't have the right drivers to get the wlan card working. Ubuntu desktop edition does, however. In fact I'm using desktop edition right now. Is there a way I can pull the drivers from the desktop edition and put them into the server edition?

These days the Ubuntu Server & Desktop kernels are the same. The differences between them were so trivial that a decision was made to merge them for 12.04 and onwards.

---

