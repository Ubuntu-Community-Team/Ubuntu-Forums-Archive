---
title: "Wireless playing up on 10.10"
date: 2010-10-26
forum: General Help
---

### Post by DirtyPC on 2010-10-26
Hi all, I know theres quite a few of these threads anway, but ohwell.
I have a Belkin Wireless USB adapter, connected to the identical Belking G+ Mimo Router. On Windows, my internet is flawless, but for some reason on Ubuntu, after a while i'll just loose connection, when it still says i'm connected. On the bottom corner of firefox for example if i typed in [www.google.co.uk](www.google.co.uk), it would just say looking up google. The only way to solve this problem is to reconnect my router and modem, and I don't enjoy doing this every 20 minutes..
Any ideas?

---

### Post by Hippytaff on 2010-10-26
Possible a driver conflict - might be worth reading this - [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Any more questions post back :-)

You might want to include the results of
```

lspci | grep Network

```
Will show what driver it uses. (capital N on Network :-))

---

### Post by DirtyPC on 2010-10-27
Hi, thanks for the reply, Did you want me to type that into terminal? If so.. nothing comes up apart from Network in Red.

I added a WEP Key to my internet and it seems a little better, but will still fail under heavy load (if you call Skype,Transmission And Firefox heavy load) :(

---

### Post by Hippytaff on 2010-10-27
try just lspci, I can't remember how to get it to print the whole line containing the word network :-s

---

### Post by KaiO on 2010-10-27
There are a load of issues around networkmanager.
In my experience, installing wicd and removing networkmanager gives a much more stable wireless connection.

---

### Post by DirtyPC on 2010-10-27
> **Hippytaff said:**
> try just lspci, I can't remember how to get it to print the whole line containing the word network :-s
Hello This is what I got00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

@KaiO I remember a long time ago when in 2008 when I had ubuntu I remember something similar like that, I will try it now, thanks :)

---

### Post by Hippytaff on 2010-10-27
I just realised your using a usb wireless dongle...so it should be lsusb not lspci...I've heard wicd sometimes works better, but I'm guessing the usb dongle, either needs switching or there are driver issues.
[http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html)

---

### Post by DirtyPC on 2010-10-27
> **Hippytaff said:**
> I just realised your using a usb wireless dongle...so it should be lsusb not lspci...I've heard wicd sometimes works better, but I'm guessing the usb dongle, either needs switching or there are driver issues.
[http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html)
hi, i have installed usb-modeswitch but I am confused as how to use it... and i installed wicd and its still acts the same :(

---

### Post by Hippytaff on 2010-10-27
What do you get with lsusb?

You need to use the information returned about the usb dongle to edit [COLOR=#0000CD][COLOR=Black]/etc/usb_modeswitch.conf.

Theres info here, but it is probably for a different usb dongle, but the process should be the same, replacing the relevant info with your dongles info :-)

Let me know how it goes :-)
[/COLOR][/COLOR]

---

### Post by DirtyPC on 2010-10-28
> **Hippytaff said:**
> What do you get with lsusb?

You need to use the information returned about the usb dongle to edit [COLOR=#0000CD][COLOR=Black]/etc/usb_modeswitch.conf.

Theres info here, but it is probably for a different usb dongle, but the process should be the same, replacing the relevant info with your dongles info :-)

Let me know how it goes :-)
[/COLOR][/COLOR]
I would just like to add, I am a total idiot. Turns out the wubi installer is only currently setup to 10.04 D:. So ive just run 10.10 64 bit now as my main OS, and my internet seems to be fine :D Just like to ask, is there any good software compatible with 64 bit? And i really have noticed a big increase in speed! + 64 bit skype?!?!? :P

---

### Post by Hippytaff on 2010-10-28
As long as it's sorted :-) I have no idea about 64bit really, so probably best start a new thread :-)

---

### Post by DirtyPC on 2010-10-28
dont worry, i found plenty.. and i kinda got skype to work! :-)

---

### Post by DirtyPC on 2010-10-30
Happened again, but I fixed it, turns out the problem is FireFox, so i got Google Chrome instead and its working like a charm :)

---

### Post by DirtyPC on 2010-10-31
***_[COLOR="Red"]UPDATE.[/COLOR]_***

Turns out my ISP had a fault at their end, after sending 3 modems. So much for my flawless Virgin 50mbp/s

---

