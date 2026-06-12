---
title: "Ubuntu 8.04.3 fails on boot-up"
date: 2009-11-28
forum: General Help
---

### Post by JCRWombat on 2009-11-28
Hello,

I have been running Ubuntu 8.04.03 for over a year.  Recently it fails on boot.  I am running on an IBM Thinkpad T42 and have kept relatively up to date on updates.

When I boot the machine the logo and scrolling bar appear and seem to work.  After a couple of minutes I get the following on a black screen in tty mode:
-------------------------------

Loading, please wait...
kinit: name_t-_dev_t(/dev/disk/by-uuid/5f3260e9-413f-4c4f-b16d-00ad57391099) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/5f3260e9-413f-4c4f-b16d-00ad57391099
kinit: No resume image, doing normal boot...

Ubuntu 8.04.3 LTS dadslaptop tty1

dadslaptop login:


--------------------------------
OK, a couple of additional pieces of information.

1) I can log in at the prompt in tty mode.  How can I get it back into the normal graphical mode and keep it there on future boots?

2) I tried to install 9.10 in another partition.  It worked until I tried to apply the updates when it failed with a bunch of other errors. (another problem for another time)

3) For the past 4 months my kids have been using the laptop for school work and internet and I've been away most of the time on business, so I don't know what they might have or not have done to it.

4) If I boot off of a CD in trial mode everything works fine.

I don't really need to upgrade to 9.10 at this time and would be happy if I could just get my trusty old 8.04.3 installation working correctly.

Any help would be greatly appreciated.

---

### Post by spcwingo on 2009-11-28
Log in on the terminal and try this command:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Let us know if that fixes it.

---

### Post by JCRWombat on 2009-11-28
Hi spcwingo,

I ran the command but got a couple of screens full of "Failed to fetch ....." errors.

Each of the lines ends with "Could not resolve 'xxx.ubuntu.com'" where xxx is **us.archives **or **security**.

I appreciate the help and any other ideas you may have.

Thanks
JC

---

### Post by spcwingo on 2009-11-28
What release are you using?  To find out enter this command:

```
lsb_release -a
```

Also, are you connected to the internet?  To find out run this command:

```
ifconfig
```

If you have an IP address listed by the interface that you are trying to use then try pinging Google or something.  To do that run this command:

```
ping -c 4 www.google.com
```

Please post the output of these commands and we'll try to go from there.

---

### Post by JCRWombat on 2009-11-28
$: lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:         8.04
Codename:     hardy

$: ifconfig
lo          Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0 B)   TX bytes:(0.0 B)

$: ping -c 4 [www.google.com](www.google.com)
ping unknown host [www.google.com](www.google.com)
---------------------------------------
From this I assume that, although my internet cable is connected and working (It was working a bit ago when I applied the updates to 9.10) that the internet service wasn't started for some reason.

---

### Post by JCRWombat on 2009-11-28
Sorry about that I must have fat fingered the last line and it interpreted it as a smiley.  It should be:

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by spcwingo on 2009-11-28
It's not even recognizing your interface at all.  Please post the output of these commands:

```
lspci
```

followed by:

```
lsusb
```

---

### Post by JCRWombat on 2009-11-28
$:lspci

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

$: lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

------------

I am able to get to the USB port (I redirected the output of the two commands, mounted a USB drive and copied the results to a thumb drive so I could include in this email.)

Thanks,
JC

---

### Post by spcwingo on 2009-11-28
You can try to manually install the modules.  Just download them from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/hardy/allpackages") and transfer them to the affected machine with a flash drive.  The first one to install is the linux-restricted-modules that corresponds with your kernel.  To find out what kernel you're running just run this command in a terminal:

```
uname -a
```

The next one to install is linux-ubuntu-modules.  Give those a whirl and let me know how it turns out.

---

