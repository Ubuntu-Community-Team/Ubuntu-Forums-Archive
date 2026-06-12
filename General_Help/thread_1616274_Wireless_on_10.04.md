---
title: "Wireless on 10.04"
date: 2010-11-08
forum: General Help
---

### Post by markinmadison on 2010-11-08
I am having trouble with my wireless connection. I have a Dell wireless 1450 USB Adapter that I used to use with the 9.10 version of Ubuntu. Now that I have upgraded to 10.04 Ubuntu, I can not get the adapter to work. What am I doing wrong? To my knowledge, I just plug it into the USB port and I should see the wireless connections.

---

### Post by P4man on 2010-11-08
can you open at terminal and type

```
lsusb
```

and report the output for the wifi card, so we know exactly what chipset it uses?

---

### Post by markinmadison on 2010-11-08
Here is the info:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 012: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 001 Device 011: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 008: ID 1058:070a Western Digital Technologies, Inc. 
Bus 001 Device 006: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by P4man on 2010-11-08
Ok, this probably only requires some blacklisting. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

Yours is the 3070. That link is a bit dated, but the issue identical according to this thread:
[http://art.ubuntuforums.org/showthread.php?t=1589504](http://art.ubuntuforums.org/showthread.php?t=1589504)

report back if that doesnt help or you have problems.

---

### Post by markinmadison on 2010-11-08
I read through all of the material and did the blacklist codes. Neither of them worked.

---

### Post by Hippytaff on 2010-11-08
What does
```

rfkill list

```
return...if anything is blocked do
```

rfkill unblock all

```

If this doesn't work, what does
```

lshw -C network

```
return :-)

---

### Post by P4man on 2010-11-08
Thats odd.
I dont know how proficient you are with ubuntu, but are you sure you dont have wireless set to disabled in network manager or something?

Can you provide the output of
```

lsmod |grep rt
lshw -C network
iwconfig
```

WHile the adapter is plugged in.

---

### Post by markinmadison on 2010-11-08
Ok, I tried both of the codes in the previous posts. Here is the data:

  	 	 	 	p { margin-bottom: 0.08in; }  mark@mark-desktop:~$ rfkill list 
 mark@mark-desktop:~$ rfkill unblock all 
 mark@mark-desktop:~$ lshw -C network 
 WARNING: you should run this program as super-user. 
   *-network                
        description: Ethernet interface 
        product: 82562V-2 10/100 Network Connection 
        vendor: Intel Corporation 
        physical id: 19 
        bus info: pci@0000:00:19.0 
        logical name: eth0 
        version: 02 
        serial: 00:1d:09:9c:e7:d9 
        width: 32 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical 
        configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-2 ip=192.168.2.4 latency=0 multicast=yes 
        resources: irq:25 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32) 
 mark@mark-desktop:~$  
 

 mark@mark-desktop:~$ lsmod |grep rt 
 agpgart                31724  2 intel_agp,drm 
 parport                32635  2 ppdev,lp 
 mark@mark-desktop:~$ lshw -C network 
 WARNING: you should run this program as super-user. 
   *-network                
        description: Ethernet interface 
        product: 82562V-2 10/100 Network Connection 
        vendor: Intel Corporation 
        physical id: 19 
        bus info: pci@0000:00:19.0 
        logical name: eth0 
        version: 02 
        serial: 00:1d:09:9c:e7:d9 
        width: 32 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical 
        configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-2 ip=192.168.2.4 latency=0 multicast=yes 
        resources: irq:25 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32) 
 mark@mark-desktop:~$ iwconfig 
 
mark@mark-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mark@mark-desktop:~$

---

### Post by Hippytaff on 2010-11-08
Its not seeing you wireless at all.

I don't think the driver isinstalled - p4man?

---

### Post by P4man on 2010-11-08
Or he blacklisted a bit much.

Mark you are certain the usb stick was plugged in, right?

Can you try this

```
sudo modprobe rt2x00usb
```

And run those commands again? If they provide the same output, dont bother posting it, just let me know

Also lets see the contents of your /etc/modprobe.d/blacklist.conf

---

### Post by markinmadison on 2010-11-08
I have got another USB stick and I just pluged it in. It now comes up with wireless connections, but none are listed. I did put that command in and here is the output:

mark@mark-desktop:~$ sudo modprobe rt2x00usb
[sudo] password for mark: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist.conf line 58: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist.conf line 59: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist.conf line 60: ignoring bad line starting with 'rt2x00usb'
WARNING: /etc/modprobe.d/blacklist.conf line 61: ignoring bad line starting with 'rt2x00lib'
WARNING: /etc/modprobe.d/blacklist.conf line 62: ignoring bad line starting with 'rt2800usb'
WARNING: /etc/modprobe.d/blacklist.conf line 63: ignoring bad line starting with 'rt2870sta'
 
The other stick I found is:
[http://www.amazon.com/gp/product/B002XGDU9M/ref=oss_product](http://www.amazon.com/gp/product/B002XGDU9M/ref=oss_product)

---

### Post by P4man on 2010-11-08
Looks like you made a mistake blacklisting. There are errors in that file. Can we see it?

```
cat /etc/modprobe.d/blacklist.conf 
```

Id rather we try the dell one first before we completely mess up your config.

---

### Post by markinmadison on 2010-11-08
Ok, how do I correct this?.....

---

### Post by Hippytaff on 2010-11-08
post the output of
```
[FONT=monospace]
[/FONT]cat /etc/modprobe.d/blacklist.conf

```
:-D

---

### Post by markinmadison on 2010-11-08
Here is the output:

mark@mark-desktop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist
blacklist
blacklist
blacklist
rt2x00usb
rt2x00lib
rt2800usb
rt2870sta

mark@mark-desktop:~$

---

### Post by Hippytaff on 2010-11-08
rt2x00usb
rt2x00lib

These might need to be unblacklisted?

---

### Post by P4man on 2010-11-08
You could probably have guessed that this:

```
blacklist amd76x_edac
blacklist
blacklist
blacklist
blacklist
rt2x00usb
rt2x00lib
rt2800usb
rt2870sta

```

would be incorrect. If nothing else the syntax.
That should be either:
```

blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

OR

```

blacklist amd76x_edac
blacklist rt2870sta
```

---

### Post by markinmadison on 2010-11-08
Ok, I corrected the error. Here is the following output:

mark@mark-desktop:~$ 
mark@mark-desktop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2870sta

mark@mark-desktop:~$ 

There still is no light on the USB stick...

---

### Post by markinmadison on 2010-11-09
Can someone help? My 10.04 still isn't seeing the wireless.

---

### Post by uRock on 2010-11-09
This is going to sound too easy, but try **sudo apt-get install linux-firmware-nonfree** That is what I had to do to get my USB wireless working.

---

### Post by markinmadison on 2010-11-09
Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!! Thank you!!!!

It worked!!!!!!

---

### Post by uRock on 2010-11-10
I am guessing that worked then?:P

---

### Post by markinmadison on 2010-11-10
It sure did!!!

---

### Post by uRock on 2010-11-10
Awesome, congrats!

---

