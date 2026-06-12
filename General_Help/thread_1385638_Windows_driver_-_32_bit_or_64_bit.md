---
title: "Windows driver - 32 bit or 64 bit?"
date: 2010-01-19
forum: General Help
---

### Post by Xog on 2010-01-19
I need to d/l the driver for my USB adapter. I'm running 64 bit ubuntu but I'm not sure if I should download the 32 bit or the 64 bit driver

(using NDISwrapper o_O!)



Windows 7 Driver

    *

      11/09/2009

      Ver.3.00.01(32-bit)

      Download 433 KB

      (Driver)

      Release Notes

Windows 7 Driver

    *

      09/11/2009

      Ver.3.00.01 (64-bit)

      Download 466 KB

      (Driver)

      Release Notes

---

### Post by spcwingo on 2010-01-19
I think ndiswrapper only supports x86 (32 bit) drivers up to XP...so the Win7 driver you have might not work.  I would suggest booting into Ubuntu (with the adapter plugged in) and running this command from a terminal to find out exactly what card you have:

```
lsusb
```

Please post the output of this command in your next post.

EDIT:

If you need the output in a file so you can post it using another machine run this command instead:

```
lsusb > ~/Desktop/output.txt
```

---

### Post by Xog on 2010-01-19
The adapter model I have is a WUSB54GC. However I'm in XP right now due to another issue which I hope to resolve shortly.

---

### Post by spcwingo on 2010-01-19
I actually need the chipset model (that's what lsusb will yield).

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> I actually need the chipset model (that's what lsusb will yield).

Bus 002 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**_Bus 001 Device 003: ID 1737:0077 Linksys _**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by spcwingo on 2010-01-19
After a little research I think I might have found the driver you need.  I have upped it here:

[http://www.mediafire.com/file/kmyy1mnwgdj/rt2870.zip]("http://www.mediafire.com/file/kmyy1mnwgdj/rt2870.zip")

If for some reason that one doesn't work, you can try this one:

[http://www.mediafire.com/file/jai12o5vyz1/netr28u.zip]("http://www.mediafire.com/file/jai12o5vyz1/netr28u.zip")

Just unzip "em and load 'em up in ndiswrapper.  :)

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> After a little research I think I might have found the driver you need.  I have upped it here:

[http://www.mediafire.com/file/kmyy1mnwgdj/rt2870.zip]("http://www.mediafire.com/file/kmyy1mnwgdj/rt2870.zip")

If for some reason that one doesn't work, you can try this one:

[http://www.mediafire.com/file/jai12o5vyz1/netr28u.zip]("http://www.mediafire.com/file/jai12o5vyz1/netr28u.zip")

Just unzip "em and load 'em up in ndiswrapper.  :)

Actually I just did this:
[http://ubuntuforums.org/showthread.php?t=1273401](http://ubuntuforums.org/showthread.php?t=1273401)

I followed all of those instructions and did everything to a T. I can see my wireless router now. But I can't connect.

The last part of his post, he said "edit your /etc/modules file" .. I just dont know what to edit it to.

contents:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

Also, where do I extract those two files to use the NDISwrapper?

---

### Post by spcwingo on 2010-01-19
You would have to add the name of the module.  Judging by the thread you linked to, I would have to say that the name of it is rt3070sta.  So you would just have to add that to your /etc/modules file so that it now looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3070sta
```

Just to be sure, with the adapter up and running, run this command in a terminal and post the output:

```
lsmod | grep 3070
```

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> You would have to add the name of the module.  Judging by the thread you linked to, I would have to say that the name of it is rt3070sta.  So you would just have to add that to your /etc/modules file so that it now looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3070sta
```

Just to be sure, with the adapter up and running, run this command in a terminal and post the output:

```
lsmod | grep 3070
```
yeah,


rt3070sta             565856  0

Gonna edit now. Will post result.

---

### Post by Xog on 2010-01-19
```

root@xog-desktop:~# lshw -C Network
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.1.2.0 multicast=yes wireless=RT2870 Wireless
root@xog-desktop:~# 
```

---

### Post by spcwingo on 2010-01-19
> **Xog said:**
> Eek. My router won't even show up now (after reboot).

```
xog@xog-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (1737:0077) present (alternate driver: rt2800usb)

```

Do I need to blacklist rt2800usb?

I would blacklist it and ndiswrapper just to play it safe.

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> I would blacklist it and ndiswrapper just to play it safe.

no go.
```

xog@xog-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.1.2.0 multicast=yes wireless=RT2870 Wireless
xog@xog-desktop:~$ ndiswrapper -l
xog@xog-desktop:~$ 

```
maybe I need to put "Wireless" after RT2870.. restarting

nope :( still can't see router... lol did i just really restart my entire CPU and come back to this page in under a minute? :x

anyways. advice?

```
xog@xog-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xog@xog-desktop:~$ 

```

Strange. I have RT2870 Wireless blacklisted.

Edit: ahhh its rt2870sta...

---

### Post by spcwingo on 2010-01-19
I have no idea...I'm sorry, but I've done all I know to do.  Hopefully someone else with a little more experience in these matters will chime in soon.  If for some reason you can't get it going you can always comment out ndiswrapper in your blacklist file, then add the newly compiled module (rt3070sta), and then go the ndiswrapper route.

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> I have no idea...I'm sorry, but I've done all I know to do.  Hopefully someone else with a little more experience in these matters will chime in soon.  If for some reason you can't get it going you can always comment out ndiswrapper in your blacklist file, then add the newly compiled module (rt3070sta), and then go the ndiswrapper route.

I never blacklisted ndiswrapper... is the name for it just "ndiswrapper" ?

---

### Post by spcwingo on 2010-01-19
Yes.

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> Yes.

ok..added it and restarted. didn't work.

Which ones should I add/remove from blacklist.conf to start trying out the ndiswrapper method

```
# rt2800usb default wireless driver
rt2800usb

# RT2870 the driver i installed for ndiswrapper
RT2870 Wireless

# RT2870 try2
RT2870

# RT2870 try3
RT2870STA

# ndiswrapper blacklisted to hopefully run normal wireless
ndiswrapper
```

---

### Post by spcwingo on 2010-01-19
You can try the ndiswrapper route that I described above...that's all I know to do.

---

### Post by Xog on 2010-01-19
> **spcwingo said:**
> You can try the ndiswrapper route that I described above...that's all I know to do.

I think I've discovered something. Back on page 1 you told me to put "rt3070sta" in the modules file.

I just tried RT3070USB and restarted. I no longer have an option for wireless then I click on the icon on the menu.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
RT3070USB
RT307x
RT3070USB(RT307x)
```
tried those combinations just to see.. and sure enough something changed.

---

