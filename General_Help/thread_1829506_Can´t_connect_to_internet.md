---
title: "Can´t connect to internet"
date: 2011-08-20
forum: General Help
---

### Post by moustii on 2011-08-20
Hey

I´m having problems connecting to the internet with my computer running ubunutu. When I try to connect with to the internet with a wired connection it works fine. But when I try do it wirelessly with a usb doggle it seems I can´t connect. I´m  abble to see my WIFI butt it doesn´t connect. It just keeps trying to connect.

---

### Post by Old_Grey_Wolf on 2011-08-20
What is the manufacturer and model number of the wireless usb dongle?

What release of Ubuntu are you using; such as, 10.04, 10.10, 11.04?

---

### Post by moustii on 2011-08-20
I´m using ubunutu 11.04.I can´t seem to find the serial number. I came in the same box as my router. There both from belkin and from the N-standard

---

### Post by asomad on 2011-08-20
If you have a connection when wired on LAN, then its definitely a "driver" issue (unless your usb wifi stick is shot, and I doubt it). 
Your Ubuntu may be missing the correct driver or module, or may be using the wrong driver or module. 
best wishes

edit: I should have added, can you verify your wireless access point works? maybe with another pc, or something else with a wifi.

---

### Post by TimmyK. on 2011-08-20
Can you please type in (in the terminal) 'lspci -nn' and tell us what it says?

---

### Post by Bryan1234 on 2011-08-20
g

---

### Post by moustii on 2011-08-20
When I type in "lspci -nn' it returns :


00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 741/741GX/M741 Host [1039:0741] (rev 03)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:00f1] (rev a2)

---

### Post by hasardeur on 2011-08-20
could you please do the following: 1. disconnect the dongle and wait a few seconds 2. reconnect the dongle - wait again (15 sec or so).
then post the output of ```
lsusb
``` and ```
dmesg | tail
```

---

### Post by moustii on 2011-08-20
Do you mean that I should type it in the terminal?

---

### Post by hasardeur on 2011-08-20
Oh sorry, I forgot to mention that. Please open a Terminal and then type:

```
sudo su
lsusb
dmesg | tail
exit
exit
```

After the first command you will be prompted for your password. It is important that you enter exit twice.

---

### Post by moustii on 2011-08-20
root@Moustapha--desktop:/home/moustapha# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Moustapha--desktop:/home/moustapha# dmesg | tail
[ 1683.008226]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
[ 1683.008233]  [<c1038dde>] ? complete+0x4e/0x60
[ 1683.008243]  [<c14f127d>] ? rest_init+0x5d/0x70
[ 1683.008252]  [<c178d7e1>] ? start_kernel+0x35f/0x366
[ 1683.008256]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
[ 1683.008260]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
[ 1683.008264] ---[ end trace 2dc5668a05eae639 ]---
[ 1683.008269] eth0: Transmit timeout, status 00000004 00000000
[ 1683.569002] eth0: Media Link On 100mbps full-duplex
[ 1688.584019] eth0: no IPv6 routers present

this is the return

---

### Post by asomad on 2011-08-20
(anyone else have issues with ubuntu and laptop touchpads while typing, blah)

---

### Post by asomad on 2011-08-21
Now, that tells us... Your wifi dongle itself is probably working ok, and your pc recognizes it's plugged in.

I'm not sure which one, (i'm a linux NOOB) but it also tells us that either: A)theres no connection to a access point, or B) There's not a proper module installed for it. The gentleman that gave you the commands will know which.


I'm curious to know that your wireless access point is properly setup and functioning?

---

### Post by Actonix on 2011-08-21
> **moustii said:**
> root@Moustapha--desktop:/home/moustapha# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Moustapha--desktop:/home/moustapha# dmesg | tail
[ 1683.008226]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
[ 1683.008233]  [<c1038dde>] ? complete+0x4e/0x60
[ 1683.008243]  [<c14f127d>] ? rest_init+0x5d/0x70
[ 1683.008252]  [<c178d7e1>] ? start_kernel+0x35f/0x366
[ 1683.008256]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
[ 1683.008260]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
[ 1683.008264] ---[ end trace 2dc5668a05eae639 ]---
[ 1683.008269] eth0: Transmit timeout, status 00000004 00000000
[ 1683.569002] eth0: Media Link On 100mbps full-duplex
[ 1688.584019] eth0: no IPv6 routers present

this is the return

Hi, just checked out your RT2870 and it appears it does not work straight out of the box but lets try see if that has changed

Open up a terminal window and type "sudo lshw  -C network" - this should provide you with a bit more detail on all your nics. Your RT2870 should show a  driver bound to the device (driver=...) which you should see towards the bottom of the output provided against the RT2870, alternatively post it here and I will try assist further.

If unclaimed  you would need to download and install the driver, this might involve you having to compile the source you download but details should be provided with the download which you can get from  [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) 

... get it, follow the instructions to compile and run the resulting executable, probably called "install" but that you will find out from the info provided

If it does show a driver attached from output of the lshw command then in a terminal window run the command  "sudo lsusb" and post the output back here and I will try to assist from there

---

### Post by asomad on 2011-08-21
> **Actonix said:**
> Hi, just checked out your RT2870 and it appears it does not work straight out of the box but lets try see if that has changed

Open up a terminal window and type "sudo lshw  -C network" - this should provide you with a bit more detail on all your nics. Your RT2870 should show a  driver bound to the device (driver=...) which you should see towards the bottom of the output provided against the RT2870, alternatively post it here and I will try assist further.

If unclaimed  you would need to download and install the driver, this might involve you having to compile the source you download but details should be provided with the download which you can get from  [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) 

... get it, follow the instructions to compile and run the resulting executable, probably called "install" but that you will find out from the info provided

If it does show a driver attached from output of the lshw command then in a terminal window run the command  "sudo lsusb" and post the output back here and I will try to assist from there

The message you replied to, was the output of lsusb.... (Mr. Acto, my nemesis) =P

however, if the user could post the output of your reccomended "lshw" command, that would be helpful.

And compiling code from source is often not preferred, Ubuntu allows access to "non-free" vendor made drivers, that would be the preferrable option if one is available.

---

### Post by moustii on 2011-08-21
when I run the command 'sudo lshw  -C network' it returns " ....... driver=rt2800usb driverversion=2.6.38-10-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn

what´s next?

I might add that the router is sett up properly beceause it works fine on my windows computer

---

### Post by asomad on 2011-08-21
wish I could be of more help here. to ME it seems like your driver is working, BUT I could be totally wrong...




I would compare the wireless connection settings on the windows computer that is connecting, to the connection settings being used by Ubuntu. In windows those settings are in different locations depending on which windows you run. Are you able to find out....

The encryption: WPA, WPA2, WEP, etc. (If any)
Name of Access point: I.e. Belkin***
Passkey: (if any)

alternatively.... There is often a "one touch button" on the router, and on the usb wifi stick. It will look something like a recycle symbol. if you have these buttons on your devices, you can push the one on the router, then push the button on the wifi stick (while it is plugged it to the pc). This would automatically "pair" the wifi stick to your router...

---

### Post by asomad on 2011-08-21
Also, since I can't be sure if its a driver issue, or a connection issue, ill add the following.

(start by plugging in your wifi stick to your pc)
in Ubuntu, go to System menu/administration menu/hardware drivers. See if anything is available AND uninstalled, if so, install the proprietary driver(s) that may be listed.


If it's not a driver issue, you can check, and edit, the wireless connection settings in ubuntu by going to system menu/preferences/network connections...


hope this helps. best wishes

---

### Post by asomad on 2011-08-21
I just re-read your first post. Now I feel STUPID. If you can see your wireless network, then your drivers are most likely FINE. This means your issue is your wifi settings. See my other post for the 3 important settings you need to find from you windows pc, and make sure they match in Ubuntu.... (or if you are familiar with your router, you can find it's wifi settings by accessing the router config through your browser (usually 192.168.0.1 or 192.168.1.1) (youll need to be plugged in to ur LAN seeing as how you dont have wireless access to it as of yet))

---

### Post by medusa569 on 2011-08-21
I had a heck of a time connectin gmy wireless......it turned out after months and months of trying it turned out to be "soft blocked" whatever that it.  

try 
rfkill unblock all


if this doesn't work google about blocked items in ubuntu. Once i ran the 
command the green light came on and I could see the nearby networks. 


good luck to you.

---

### Post by ClientAlive on 2011-08-21
> **medusa569 said:**
> I had a heck of a time connectin gmy wireless......it turned out after months and months of trying it turned out to be "soft blocked" whatever that it.  

try 
rfkill unblock all


if this doesn't work google about blocked items in ubuntu. Once i ran the 
command the green light came on and I could see the nearby networks. 


good luck to you.


Other pervayors of useful information might be:

```

ifconfig

```

And

```

rfkill list

```

```

man ifconfig

```

HTH

:D

---

### Post by asomad on 2011-08-21
> **medusa569 said:**
> I had a heck of a time connectin gmy wireless......it turned out after months and months of trying it turned out to be "soft blocked" whatever that it.  

try 
rfkill unblock all


if this doesn't work google about blocked items in ubuntu. Once i ran the 
command the green light came on and I could see the nearby networks. 


good luck to you.


He can see the wireless network(s) already, I believe the problem lies elsewhere.

---

### Post by asomad on 2011-08-22
> **moustii said:**
> when I run the command 'sudo lshw  -C network' it returns " ....... driver=rt2800usb driverversion=2.6.38-10-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn

what´s next?

I might add that the router is sett up properly beceause it works fine on my windows computer

I'm curious. The windows computer that works fine on your router... That's connected wirelessly right? Because if it's wired on LAN, that does not verify anything about your wireless access point being set-up...

---

