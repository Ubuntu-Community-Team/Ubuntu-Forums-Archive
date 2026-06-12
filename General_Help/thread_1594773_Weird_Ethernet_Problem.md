---
title: "Weird Ethernet Problem"
date: 2010-10-12
forum: General Help
---

### Post by StreetWise on 2010-10-12
Hi, I did a fresh install of Ubuntu 10.04, then did the useual update to get all the latest fixxs.

I then downloaded the latest Nvidia driver from the official site and installed it.

After rebooting I noticed that I had no ethernet connection, I reformatted again and did it again but still the thing is happening.

Could someone help me out and guide me through getting my internet connection back please as I'm a newb and need all the help I can get.

---

### Post by Carlbc18 on 2010-10-12
if you do an ```
ifconfig
``` from a terminal window what does it say for eth0?

also, you could try bringing the interface down, ```
 ifconfig down 
``` then back up again ```
 ifconfig up 
```

---

### Post by StreetWise on 2010-10-14
Hi, sorry it's taken me a while to reply, I have been working away.

For ifconfig I get:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```


For ifconfig down I get:

```
down: error fetching interface information: Device not found
```

For ifconfig up I get:

```
up: error fetching interface information: Device not found
```


The ethernet driver is installed as it was working before I installed the Nvidia driver.

---

### Post by StreetWise on 2010-10-15
Anyone?

---

### Post by coffeecat on 2010-10-15
ifconfig is not showing your eth0 device. Post the output of these two commands:

```
lspci | grep -i ethernet
sudo lshw -C network
```> **StreetWise said:**
> I then downloaded the latest Nvidia driver from the official site and installed it.


Why did you go to the nvidia website instead of using the Hardware Drivers utility? Which version of the driver? Was it a beta? Did you try the nvidia driver you can install from System > Administration > Hardware Drivers?

---

### Post by StreetWise on 2010-10-15
Thanks for the reply and your help.

For "lspci | grep -i ethernet" I get:

```
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

For "sudo lshw -C network" I get:

  ```
*-network DISABLED      
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:1a:ee:01:9d:0a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:e700(size=256) memory:ee023000-ee0230ff memory:28000000-2801ffff(prefetchable)
```

> Why did you go to the nvidia website instead of using the Hardware Drivers utility? Which version of the driver? Was it a beta? Did you try the nvidia driver you can install from System > Administration > Hardware Drivers?

The one in the repo had a bug that would hang my computer on start up. the version I am using is 173.14.27 ([http://www.nvidia.co.uk/object/linux-display-ia32-173.14.27-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-173.14.27-driver-uk.html))

---

### Post by coffeecat on 2010-10-15
> **StreetWise said:**
> The one in the repo had a bug that would hang my computer on start up. 

That's unusual. There must be some sort of conflict between the driver and your particular hardware. Clearly the 173 driver must be interfering with your ethernet because you got this twice, and lshw clearly shows your eth0 device and the correct driver, although showing it as disabled.

I'm not sure what to suggest. Except...

Were you wanting to use the proprietary driver for gaming, or just to enable compiz? If the latter, you can enable 3d acceleration with the open-source nouveau driver in Maverick/10.10. It doesn't work out of the box, but you can get it to work by installing the libgl1-mesa-dri-experimental package.

---

### Post by StreetWise on 2010-10-15
Do you thing another ethernet card might do the trick?

---

### Post by coffeecat on 2010-10-15
> **StreetWise said:**
> Do you thing another ethernet card might do the trick?

Good idea, but I don't know. I can only guess this is an obscure conflict between your BIOS and the nvidia driver which is somehow interfering with the ethernet device. Just a guess, though. If you have a PCI ethernet card of another chipset it would be worth giving it a try, but whether it's worth going to the expense of buying   something that might or might not work with your setup I can't answer.

---

### Post by StreetWise on 2010-10-15
> **coffeecat said:**
> Good idea, but I don't know. I can only guess this is an obscure conflict between your BIOS and the nvidia driver which is somehow interfering with the ethernet device. Just a guess, though. If you have a PCI ethernet card of another chipset it would be worth giving it a try, but whether it's worth going to the expense of buying   something that might or might not work with your setup I can't answer.

I have two, the one I am using now is a PCI giga ethernet card but the mobo I'm using also has a standard 100/100 ethernet built into it, so I can test that now.

Thanks for your help buddy and I will post the results back here soon.

---

### Post by coffeecat on 2010-10-15
> **StreetWise said:**
> I have two, the one I am using now is a PCI giga ethernet card but the mobo I'm using also has a standard 100/100 ethernet built into it, so I can test that now.

That's interesting because the onboard ethernet didn't show up with your lspci and lshw outputs, or did you edit those? Or can you disable the onboard ethernet in BIOS?

Whatever, if the system is seeing the onboard ethernet, it might be worth blacklisting the driver for that to see if that can enable  the PCI ethernet.

---

### Post by StreetWise on 2010-10-15
> **coffeecat said:**
> That's interesting because the onboard ethernet didn't show up with your lspci and lshw outputs, or did you edit those? Or can you disable the onboard ethernet in BIOS?

Whatever, if the system is seeing the onboard ethernet, it might be worth blacklisting the driver for that to see if that can enable  the PCI ethernet.

Yeah the onboard one is disabled in the bios

---

### Post by StreetWise on 2010-10-15
Was on another forum and this guy gave me this command to put in:

```
dmesg | grep -i ethernet 
```

the result I got was:

```
[    1.437680] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
```

and my Ethernet decided to work, I have rebooted many times and it comes up every time.

Just thought I would post it here if you wanted to make sense of it because I can't, and to help others in case they come across this thread.

---

### Post by coffeecat on 2010-10-15
> **StreetWise said:**
> if you wanted to make sense of it because I can't

Nor can I, but I'm glad it's working. If it fails again, the only other thing I can suggest is:

```
sudo modprobe -r r8169
sudo modprobe r8169
```

---

### Post by StreetWise on 2010-10-15
> **coffeecat said:**
> Nor can I, but I'm glad it's working. If it fails again, the only other thing I can suggest is:

```
sudo modprobe -r r8169
sudo modprobe r8169
```


Cool, thanks I will keep that in mind.

---

