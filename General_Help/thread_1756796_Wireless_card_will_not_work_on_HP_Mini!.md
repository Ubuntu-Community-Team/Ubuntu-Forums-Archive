---
title: "Wireless card will not work on HP Mini!"
date: 2011-05-12
forum: General Help
---

### Post by linuxuser12345 on 2011-05-12
Hi, I am trying to fix someone's computer, and the wireless card will not work!
Two proprietary drivers show up on the "Additional Drivers" program, but every time I go to download and install them, I get an error message right before it finishes, and I still cannot use the card. ugh

Please help me on this!

I am using Ubuntu 10.10 Desktop

Thanks! :)
~Jeb

---

### Post by TeoBigusGeekus on 2011-05-12
What's the error message you get?

---

### Post by linuxuser12345 on 2011-05-12
Well now, whenever I go back to the Additional Drivers program, it tells me that one driver is installed and in use. Whenever I go to the network button on the top bar, though, it doesn't even have a wireless network option.

What should I do?

---

### Post by TeoBigusGeekus on 2011-05-12
Can you post us the output of
```
ifconfig
```
```
iwconfig
```
and
```
lshw -C network
```
?

---

### Post by linuxuser12345 on 2011-05-12
ifconfig:

amy@HP-Mini:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:55:cd:63:c8  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fecd:63c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123532 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:372490264 (372.4 MB)  TX bytes:9105361 (9.1 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11376 (11.3 KB)  TX bytes:11376 (11.3 KB)

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

amy@HP-Mini:~$

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> amy@HP-Mini:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)

Wait for it...

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:55:cd:63:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.10 latency=0 multicast=yes
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)
amy@HP-Mini:~$

---

### Post by TeoBigusGeekus on 2011-05-12
Broadcom. The usual suspect...
See [this]("http://ubuntuforums.org/showthread.php?t=1737996") thread.

---

### Post by linuxuser12345 on 2011-05-12
So, what should I do, simply?

---

### Post by linuxuser12345 on 2011-05-12
Do I type the stuff in the boxes in a terminal?

---

### Post by TeoBigusGeekus on 2011-05-12
Do what vaun suggested:
Uninstall through synaptic all the b43 packages (do a search for that string), reinstall the broadcom kernel source,
```
sudo apt-get --reinstall bcmwl-kernel-source
```
uninstall completely every proprietary wifi drivers from additional drivers and then try
```
sudo rmmod wl brcm4312
sudo modprobe brcm4312

sudo depmod -a
```

---

### Post by linuxuser12345 on 2011-05-12
So I type exactly what you just said in a terminal?

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ sudo apt-get --reinstall bcmwl-kernel-source
[sudo] password for amy: 
E: Invalid operation bcmwl-kernel-source
amy@HP-Mini:~$

---

### Post by TeoBigusGeekus on 2011-05-12
First open synaptic, search for b43, uninstall the related packages and then, yes, type the commands in a terminal.

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ sudo rmmod wl brcm4312
ERROR: Module wl does not exist in /proc/modules
ERROR: Module brcm4312 does not exist in /proc/modules
amy@HP-Mini:~$ sudo modprobe brcm4312
FATAL: Module brcm4312 not found.
amy@HP-Mini:~$ 
amy@HP-Mini:~$ sudo depmod -a

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> amy@HP-Mini:~$ sudo apt-get --reinstall bcmwl-kernel-source
[sudo] password for amy: 
E: Invalid operation bcmwl-kernel-source
amy@HP-Mini:~$

Oh ****, sorry, the correct command is
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by linuxuser12345 on 2011-05-12
How do I completely uninstall the proprietary drivers? The Additional Drivers app wont let me, for some reason.
Also, when do I know the stuff is done installing in the terminal?

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> How do I completely uninstall the proprietary drivers? The Additional Drivers app wont let me, for some reason.
Also, when do I know the stuff is done installing in the terminal?

Isn't there a remove option when you select your wifi's restricted driver?
Can you post a screenshot?

EDIT:
When it returns to a command prompt it's done.

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ sudo rmmod wl brcm4312
ERROR: Module wl does not exist in /proc/modules
ERROR: Module brcm4312 does not exist in /proc/modules
amy@HP-Mini:~$ sudo modprobe brcm4312
FATAL: Module brcm4312 not found.
amy@HP-Mini:~$ 
amy@HP-Mini:~$ sudo depmod -a

---

### Post by linuxuser12345 on 2011-05-12
Okay, I got it all removed. Now what?

edit: The reason why I tried installing the drivers in the first place is because with Ubuntu's default settings, the firmware was missing.

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> Okay, I got it all removed. Now what?

See post #18.

---

### Post by linuxuser12345 on 2011-05-12
Done. Now what do I do? I still don't see anything on the "Wireless" section on the networking menu. All I see is "Wireless is disabled"

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> Done. Now what do I do? I still don't see anything on the "Wireless" section on the networking menu. All I see is "Wireless is disabled"

Reboot.

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ sudo rmmod wl brcm4312
ERROR: Module wl does not exist in /proc/modules
ERROR: Module brcm4312 does not exist in /proc/modules
amy@HP-Mini:~$ sudo modprobe brcm4312
FATAL: Module brcm4312 not found.
amy@HP-Mini:~$ 
amy@HP-Mini:~$ sudo depmod -a

---

### Post by linuxuser12345 on 2011-05-12
Lets hope this works!!!! Please pray for me! :)

---

### Post by linuxuser12345 on 2011-05-12
Nothing happened. Now the "wireless" section doesn't even appear on the menu! ugh

---

### Post by TeoBigusGeekus on 2011-05-12
Do this
```
sudo modprobe bcm4312
sudo depmod -a
```

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ sudo modprobe bcm4312
FATAL: Module bcm4312 not found.
amy@HP-Mini:~$ sudo depmod -a
amy@HP-Mini:~$

---

### Post by TeoBigusGeekus on 2011-05-12
I give up... Sorry for wasting your time.
One last thing, is to try your luck with the windows drivers via [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").
Sorry again... (and damn you broadcom)

---

### Post by linuxuser12345 on 2011-05-12
Do you know where I can find the windows driver? Maybe I can get this working on ndiswrapper

---

### Post by linuxuser12345 on 2011-05-12
Okay, I found the driver, but how do i get the .inf file from the .exe file?

---

### Post by TeoBigusGeekus on 2011-05-12
It's probably an archive; see [this]("http://blaise.ca/blog/2009/06/14/solution-extract-exe-archive-with-7z-in-ubunu-9-04-fix-unsupported-method-error/").

---

### Post by linuxuser12345 on 2011-05-12
amy@HP-Mini:~$ 7z e sp45515.exe

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)


Error:
there is no such archive
amy@HP-Mini:~$ 


Am I putting the right destination in? The file is in the downloads folder

---

### Post by TeoBigusGeekus on 2011-05-12
Then do
```
7z e ~/Downloads/sp45515.exe
```

---

### Post by linuxuser12345 on 2011-05-12
Okay, I installed the .inf file. Now what do I do? I still see "wireless is disabled"

---

### Post by TeoBigusGeekus on 2011-05-12
They should be in your downloads folder.

---

### Post by linuxuser12345 on 2011-05-12
Okay, I got the .inf file installed now, and ndiswrapper detects my hardware, but I still see the "wireless is disabled". Is there anything else I can do?

---

### Post by TeoBigusGeekus on 2011-05-12
> **linuxuser12345 said:**
> Okay, I got the .inf file installed now, and ndiswrapper detects my hardware, but I still see the "wireless is disabled". Is there anything else I can do?

Stupid question, sorry to ask, but isn't there a button on the netbook that enables/disables wifi? Is it correctly set?

---

### Post by linuxuser12345 on 2011-05-15
There is a button that enables/disables the wifi, but it is set to "on" mode

---

