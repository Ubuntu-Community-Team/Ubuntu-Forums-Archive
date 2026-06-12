---
title: "Wireless BCM4322 Slow Connection"
date: 2010-10-13
forum: General Help
---

### Post by gearshifter on 2010-10-13
I am having problems with the wl driver for the BCM4322 on 10.10.

It seems with two different routers the connection is really slow and jumpy and web pages barely want to load.  I have tried a usb wireless device, and it seems to work much quicker.

Is anyone else having problems with their broadcom cards with the new update?

10.10 64 bit.  Using Broadcom restricted drivers (wl)

ifconfig :
```
eth1      Link encap:Ethernet  HWaddr 0c:60:76:0e:35:07  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe0e:3507/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60312 errors:0 dropped:0 overruns:0 frame:26219
          TX packets:48748 errors:47 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76269022 (76.2 MB)  TX bytes:12990311 (12.9 MB)
          Interrupt:21 

```


iwconfig
```
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:238  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

---

### Post by nemarasu on 2010-10-14
I'm getting the same thing in the 32-bit version of 10.10. Slow wireless network but fast ether. Ping response times are horrible with packet loss on wireless but flawless on Ethernet.

I tried the b43 driver and reinstalling the sta bcm4322 driver, but same difference, its still slow. Any ideas anyone?

---

### Post by gearshifter on 2010-10-14
I will mess around with it again tonight, but I have tried both drivers, and still have the same problem..


I just bought an intel 5300 half card that I will attempt to put in this computer (xps 1340).  We'll see how that works....

---

### Post by ersiner on 2010-10-14
Same here for 4312. It was working fine in 10.04.

---

### Post by krims0n32 on 2010-10-14
Same here. There was an issue with power management in the previous version (10.04) that could be worked around by doing:

sudo iwconfig eth1 power off

this seems to help a little with 10.10, but it is still slow as hell.

---

### Post by krims0n32 on 2010-10-14
> **krims0n32 said:**
> Same here. There was an issue with power management in the previous version (10.04) that could be worked around by doing:

sudo iwconfig eth1 power off

this seems to help a little with 10.10, but it is still slow as hell.

Actually after giving this a second try, it still seems to be a valid workaround. 
Stick this script in /etc/network/if-up.d (I call the script powermode), and set its mode to 755. Make sure that DEVICE matches your broadcom device.
```

#!/bin/sh

DEVICE="eth1"

if [ "$IFACE" = "$DEVICE" -a "$PHASE" = "up" ]; then
  /sbin/iwconfig $DEVICE power off
fi

exit 0

```

Then disable and re-enable your wireless connection. iwconfig eth1 should tell you that "Power management" is set to Off. Now test your connection stability and speed. It is fine for me now :)

---

### Post by jlsm on 2010-10-14
This workaround works quite nicely. Thanks to krims0m32.

I'm using a lenovo g430 with broadcom 4312 wireless controller on Ubuntu 10.10 Maverick Meercat.

Again, thanks much.

---

### Post by nemarasu on 2010-10-15
The issue for me seems to be my home wireless access point. I tested connectivity from a couple of different locations (work, barnes & noble, etc...) ( I made no changes to 10.10 in any way shape or form ) and it works just fine. It's my home router/fw/wap that is the problem.

---

### Post by gearshifter on 2010-10-15
I've tried your script, and I have tried manually shutting of power managment, but I do not see anything that says power management is off in iwconfig..

If you look at the first post, you can see it even thinks I am not associated to an access point..

Anyone else have this problem?

I've tried this on three routers now.. I think all of the routers are broadcom chipsets too.

---

### Post by nemarasu on 2010-10-15
gearshifter,

have you tried changing the settings on the wireless router? (wep, wpa, wpa2) And then the various settings under each?

---

### Post by gearshifter on 2010-10-15
I believe I tried no security with just a mac addy filter and still had problems...

Hopefully this intel chip works out hah.. I hate broadcom.

---

### Post by bademeister on 2010-10-19
Hey,

I am experiencing the same issue on a 13.3" macbook pro (5,5) (Maverick 64bit). The ```
sudo iwconfig eth1 power off
``` workaround seems to help a little, but I would say it's still slower than with 10.04.

---

### Post by gearshifter on 2010-10-19
I swapped my wireless out for the intel 5300 which now will kernel panic my machine if powermode is on.  I wonder if swapping wireless cards is causing some sort of improper driver load.

---

### Post by superubufan on 2010-10-21
Has somebody files a bug report on this already? Turning powermanagement off for the wifi driver worked for me (Macbook Pro 6,2, Ubuntu 10.10/64bit)

---

### Post by Lemo85 on 2010-10-22
> **krims0n32 said:**
> Actually after giving this a second try, it still seems to be a valid workaround. 
Stick this script in /etc/network/if-up.d (I call the script powermode), and set its mode to 755. Make sure that DEVICE matches your broadcom device.
```

#!/bin/sh

DEVICE="eth1"

if [ "$IFACE" = "$DEVICE" -a "$PHASE" = "up" ]; then
  /sbin/iwconfig $DEVICE power off
fi

exit 0

```Then disable and re-enable your wireless connection. iwconfig eth1 should tell you that "Power management" is set to Off. Now test your connection stability and speed. It is fine for me now :)

I'm a little new to creating scripts for Ubuntu, can you explain what you mean by "set it's mode to 755"?

Thanks.

---

### Post by Espen11 on 2010-10-23
> **Lemo85 said:**
> I'm a little new to creating scripts for Ubuntu, can you explain what you mean by "set it's mode to 755"?

Thanks.

It means to change the file permissions. Use this:
'sudo chmod 755 /etc/network/if-up.d/powermode'
(and you can see the changes with 'ls -l')

---

### Post by padlefot on 2010-10-24
> I am experiencing the same issue on a 13.3" macbook pro (5,5) (Maverick 64bit). The
Code:
sudo iwconfig eth1 power off
workaround seems to help a little, but I would say it's still slower than with 10.04.

I`m having the same issues on my MacBook Pro 5-5 13.3" (Maverick 32bit)
Tried the script fix, that seemed to fix it for like 3 seconds after reconnect, got into 53mb/s mode then popped back to 2mb/s and stayed there. 
The power off command itself doesnt seem to do anything at all.
Anyone filed a bug report or found a fix for this yet?

All Help Appriciated!:popcorn:

---

### Post by Jales on 2010-10-28
It's the same with me.

Using MacBookPro 55 13" - Ubuntu Maverick 32bit. Ping-ing to the router results in > 600ms reply.

I found that after I turn of security setting (WEP, WPA, WPA2) in the wireless router, and only use MAC Address allow-association, the connection gets A LOT better. Ping-ing to router results in ~100ms. Still makes me worried, since usually in my MacOSX the results is ~1ms. I try the power off option, resulting to 1ms - 6ms, but sometimes still get >100ms reply.

UPDATE : 

Another work-around without have to turn of security setting is to pass kernel parameter, intel_iommu=off .Still trying for about 10 minutes now. The ping results in ~1ms and sometimes jump to ~100ms. I'll report if this doesn't work.

---

### Post by itismike on 2010-11-14
I have a MBP 6,2 and powermode does not appear to make any difference at all:

```
$ sudo iwconfig eth1 power off
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 90:27:e4:e9:xx:xx  
          inet addr:192.168.1.x  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9227:e4ff:fee9:3478/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2149274 errors:0 dropped:0 overruns:0 frame:105593
          TX packets:3607849 errors:2909 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:583582414 (583.5 MB)  TX bytes:805004161 (805.0 MB)
          Interrupt:17 
$
```
Am I "holding it wrong?" :P

---

### Post by t4sseltine on 2010-11-19
Thanks krims0n32, that workaround worked just fine for me!

Running Broadcom Corporation BCM4322 which was fine on 10.04, but slow as on 10.10


[U]
[/U]

---

### Post by jrusi on 2010-12-07
> **Jales said:**
> It's the same with me.

I try the power off option, resulting to 1ms - 6ms, but sometimes still get >100ms reply.

UPDATE : 

Another work-around without have to turn of security setting is to pass kernel parameter, intel_iommu=off .Still trying for about 10 minutes now. The ping results in ~1ms and sometimes jump to ~100ms. I'll report if this doesn't work.

I have the same problem on the Mac BCM4322 :( power off option doesn't help
any update?

---

### Post by itismike on 2010-12-07
leaving the A/C power connector connected is the only solution I've found is reliable. Is there an open bug-report for this I can subscribe to?

---

### Post by jrusi on 2010-12-07
> **itismike said:**
> leaving the A/C power connector connected is the only solution I've found is reliable. Is there an open bug-report for this I can subscribe to?

I can confirm... leaving the A/C helps a little bit - at least I can connect to the AP but the ping is going from 45 to 500ms

I'm not sure if we can open bug-report in Ubutu since it is a proprietary driver...

---

### Post by bademeister on 2010-12-09
Hello,

i have filed a bug report in case anyone wants to subscribe:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/688146](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/688146)

cheers P

---

### Post by ahj on 2010-12-23
I have a Macbook Pro with the BCM4322 wireless chipset, and the power off option with iwconfig was not enough to get stable wireless, although it helped a bit.

However, the following solved the problem.

In nework manager, choose edit connections, choose your wireless network, and hit 'edit'. Now, enter the BSSID of your network. You can get the BSSID from iwconfig, look for Access Point: XX:XX:XX:XX:XX:XX . (you have to be connected for that information to appear).

Entering a specific BSSID disables wireless roaming, which solved the problem in my case.

Remember, you ALSO need the power off option described above.

Oh, and i also disabled wireless security, but I'm not sure that is actually necessary.

---

### Post by bademeister on 2010-12-25
Hey, the workaround posted by ahj works for me, thank you very much.

I have WPA enabled, doesn't seem to cause problems.

kind regards
Paul

---

### Post by darkvad0r on 2011-02-20
Well, what do you know ? I just applied the 2 workarounds suggested (powermode off and setting bssid) and my download speed went from ~3Mbps to ~11Mbps !

I'm on a MacbookPro6,2

---

