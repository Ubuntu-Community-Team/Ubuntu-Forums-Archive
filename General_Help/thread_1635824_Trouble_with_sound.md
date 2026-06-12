---
title: "Trouble with sound"
date: 2010-12-02
forum: General Help
---

### Post by Denton Larson on 2010-12-02
Hi Everybody

I have a problem with sound. I don't have any. It started yesterday. I have 2 boards that I can select from 1 internal 1 external for Ham radio. I was on a program that I was trying to get updated Fldigi. And now I lost the sound. My bad I now know.

Here is a picture of what I see when I go into the System/Preferences/Sound

Any got a clue as what to do?

Denton Larson
WB0ZUR

---

### Post by k50aker on 2010-12-02
> **Denton Larson said:**
> Hi Everybody

I have a problem with sound. I don't have any. It started yesterday. I have 2 boards that I can select from 1 internal 1 external for Ham radio. I was on a program that I was trying to get updated Fldigi. And now I lost the sound. My bad I now know.

Here is a picture of what I see when I go into the System/Preferences/Sound

Any got a clue as what to do?

Denton Larson
WB0ZUR

please post output of 
```
lspci
```

Also see if there are missing drivers in System > Administration > Additional Drivers.

---

### Post by Denton Larson on 2010-12-02
Hi

Here is what you said to post lspci

dlarson@dlarson-deskDell:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:00.0 USB Controller: NEC Corporation USB (rev 41)
03:00.1 USB Controller: NEC Corporation USB (rev 41)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
dlarson@dlarson-deskDell:~$

---

### Post by Denton Larson on 2010-12-02
> **k50aker said:**
> please post output of 
```
lspci
```

Also see if there are missing drivers in System > Administration > Additional Drivers.

And I don't have Additional Drivers but I have Hardware Drivers and it came up with nothing.

---

### Post by k50aker on 2010-12-02
> **Denton Larson said:**
> And I don't have Additional Drivers but I have Hardware Drivers and it came up with nothing.

now, whats the output of ```
lspci -v -s 00:1e.2
```

---

### Post by Denton Larson on 2010-12-02
> **k50aker said:**
> now, whats the output of ```
lspci -v -s 00:1e.2
```

dlarson@dlarson-deskDell:~$ lspci -v -s 00:1e.2
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Device 0181
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ec00 [size=256]
	I/O ports at e8c0 [size=64]
	Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
	Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

dlarson@dlarson-deskDell:~$ 


Denton Larson

---

### Post by k50aker on 2010-12-02
do you have alsa mixer? if not then:

```
apt-get install gnome-alsamixer
```


```
sudo gnome-alsamixer
```

and see if there are devices available there, if there is then unmute it or whatever you see there that could make the volume work.

---

### Post by Denton Larson on 2010-12-02
> **k50aker said:**
> do you have alsa mixer? if not then:

```
apt-get install gnome-alsamixer
```


```
sudo gnome-alsamixer
```

and see if there are devices available there, if there is then unmute it or whatever you see there that could make the volume work.

It worked WOO HOO THANK YOU!

Denton Larson

---

