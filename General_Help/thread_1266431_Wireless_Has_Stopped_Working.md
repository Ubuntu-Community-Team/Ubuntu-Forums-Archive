---
title: "Wireless Has Stopped Working"
date: 2009-09-14
forum: General Help
---

### Post by LeonBlade on 2009-09-14
Hey everyone,

Just this morning before I went to bed I was connected on my laptop on the Wireless Router like I always have been. 
I shut it off to go to bed, when I wake up and turn my laptop on, it can no longer connect to the Wireless in my house.

My iPod Touch connected to it, and when I switched my Operating System to Windows Vista on this very same laptop the Wireless worked fine, so I know it's something to do with my settings or something with Ubuntu.

I'm running the latest 9.04 of Ubuntu and like I said it has worked in the past but now it isn't.

Can someone assist me in getting it to connect again?
Oh, and I'm posting this from my laptop which is hooked up wired right now to my router.

Thanks,
Leon Blade

---

### Post by LeonBlade on 2009-09-14
Bumping this so people can see.

---

### Post by wieman01 on 2009-09-14
Please don't bump before 24 hours have passed, that's the rule.

When you type this in a shell (= command line window), what's the output?
> sudo iwlist scan

---

### Post by scrooge_74 on 2009-09-14
The few times I had that kind of problem I had to reboot the router and the PC just to be safe. I guess either one of them just dont want to release or give the IP again

---

### Post by LeonBlade on 2009-09-14
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

That's what I got... 
And I've reset the router and my computer several times already.

---

### Post by scrooge_74 on 2009-09-14
still it dosent pick up an ip from router?

This is a dumb question but, do you have your wifi card enable?

Also check the Network applet on the top bar, are you using some kind of security on your network? Try desabling it and then try to connect

---

### Post by LeonBlade on 2009-09-15
Apparently my device isn't found at all... it can't find my wireless card.
What confuses me is... it was just working the other day.
I shut it down, turn it on, and now this!

I'm not sure *how* to enable it exactly...
I have the HP G50 laptop and there is a WiFi button, but the light indicator doesn't work with this OS so it just stays red/orange indicating it's off, when it's actually on.  However, it does turn the WiFi on and off, I just don't know when it's on or off.

---

### Post by danwood76 on 2009-09-15
Could you please post the output of the following 2 commands:
```

sudo lspci -nnn
dmesg

```

The second command will post a lot so it might be worth piping it into a text file and uploading it with "dmesg > dmesg.txt"

---

### Post by LeonBlade on 2009-09-15
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```

[http://tinypaste.com/74a20](http://tinypaste.com/74a20)
Here is the dmesg

---

### Post by danwood76 on 2009-09-15
Odd, your wifi card isnt in your lspci.
Is it internal or USB?

It is mentioned in the dmesg:
> 
[   13.601856] ath_hal: module license 'Proprietary' taints kernel.
[   13.602840] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.611506] wlan: 0.9.4
[   13.616878] ath_pci: 0.9.4
[   13.616923] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.616936] ath_pci 0000:02:00.0: setting latency timer to 64
[   13.665685] pciehp 0000:00:1c.1:pcie02: Card not present on Slot(1)
[   13.665709] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   13.665734] ath_pci 0000:02:00.0: PCI INT A disabled
[   13.677956] pciehp 0000:00:1c.1:pcie02: Card present on Slot(1)

And this kind of points towards the fact you have an AR5007EG which isnt supported by madwifi of that version (0.9.4).

Can you post the output of the following to se if the kernel modules are loaded:
```

sudo lsmod | grep 'ath'

```

If you dont get any output from that command try the following and post the output:
```

sudo modprobe ath5k
dmesg | tail

```

---

### Post by LeonBlade on 2009-09-15
My wireless is inside the laptop, I don't know what happened.
It's possible a setting may have changed and disabled/removed it from viewing, I don't know.

```

ath_pci                99224  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci

```

Here is the output of that first line.

---

### Post by P4man on 2009-09-15
FWIW, a few releases of ubuntu ago, my wireless worked, but the killswitch (to turn it on/off) didn't. It would only kill it. Only way I found to turn it on again after killing in ubuntu, annoyingly, was booting windows and turn it on, then reboot in ubuntu.

Not saying thats your issue, but thought id mention it.

---

### Post by danwood76 on 2009-09-15
I would try using the ath5k module.
I find its faster than madwifi anyway.

To load this module do the following:
```

sudo rmmod ath_pci ath_hal wlan
sudo modprobe ath5k

```

If your wifi doesnt come up please post the output of:
```

dmesg | tail

```

regards,
Danny

---

### Post by LeonBlade on 2009-09-15
Thanks P4Man, but that isn't my case.
My Wireless resets to on once you reboot.

---

### Post by LeonBlade on 2009-09-15
With Ethernet not plugged in:
```

[   36.579512] r8169: eth0: link down
[   36.579684] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.651504] CPU0 attaching NULL sched-domain.
[   58.651510] CPU1 attaching NULL sched-domain.
[   58.651654] CPU0 attaching sched-domain:
[   58.651656]  domain 0: span 0-1 level MC
[   58.651660]   groups: 0 1
[   58.651665] CPU1 attaching sched-domain:
[   58.651666]  domain 0: span 0-1 le

```

With Ethernet plugged in:
```

[   58.651504] CPU0 attaching NULL sched-domain.
[   58.651510] CPU1 attaching NULL sched-domain.
[   58.651654] CPU0 attaching sched-domain:
[   58.651656]  domain 0: span 0-1 level MC
[   58.651660]   groups: 0 1
[   58.651665] CPU1 attaching sched-domain:
[   58.651666]  domain 0: span 0-1 level MC
[   58.651668]   groups: 1 0
[  139.667638] r8169: eth0: link up
[  139.667996] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

I still can't seem to get it to work... :/

---

### Post by danwood76 on 2009-09-15
For some reason I dont think the hardware is being recognised and the previous output of lspci confirms this.

You can try disabling the madwifi driver from bootup by blacklisting it in modprobe.
First open the blacklist file:
```

sudo gedit /etc/modprobe.d/blacklist.conf

```
and add the following two lines to the bottom:
```

blacklist ath_pci
blacklist ath_hal

```
Then shutdown and bootup again, dont reboot as rebooting will leave stuff in the RAM of the Wifi card which may be blocking it.

When you bootup you probably wont have wifi working but enabling the ath5k driver by doing the following:
```

sudo modprobe ath5k

```
Can you post the ouput of the final command and the dmesg after you have run it please.

regards,
Danny

---

### Post by LeonBlade on 2009-09-15
```

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'pc'

```

Now I'm connected to my wireless! :D
Thank you very much for this!
Do you know how this might of happened?

---

### Post by wieman01 on 2009-09-16
> **LeonBlade said:**
> Thanks P4Man, but that isn't my case.
My Wireless resets to on once you reboot.
I would not be too sure here. This once happened to me as well, although the light turned on wireless was off. It is worth a shot.

---

### Post by danwood76 on 2009-09-16
It could be that in some update madwifi was decided to be working correctly or something odd happened with a race condition which allowed it to load instead of the ath5k module.

Glad its working for you though!

I believe that you can disable madwifi using the hardware drivers control panel which may be a better place to disable it.

Did ath5k load automatically or did you have to load it with modprobe? (the last command)

If you add "ath5k" on a new line to /etc/modules it will load on each boot without you needing to do anything.

Also it looks like you have a typo in the /etc/modprobe.d/blacklist file can you post the output of the following so we can sort this?
```

cat /etc/modprobe.d/blacklist

```

regards,
Danny

---

### Post by LeonBlade on 2009-09-16
```

#pc speaker beep
blacklist pcspkr

```

I commented it out, I think *pc speaker* isn't supposed to be there lol.

And I was just going to ask where to add a line for the *ath5k* to be loaded at startup because I had to do it again (luckily the line was still in the Terminal history).

Thanks again for your help.

---

### Post by danwood76 on 2009-09-16
That line should have been commented anyway, I wonder if maybe the madwifi drivers are supposed to be blacklisted but somehow your blacklist file got corrupted.

Anyway it doesn't matter, I'm glad you're now sorted.

---

