---
title: "Mic is working, but recording isn't working (AD1988 on ASUS P5B-VM)"
date: 2009-08-05
forum: General Help
---

### Post by vak on 2009-08-05
**UPD.**: Solved by upgrade to Karmic beta. (However now Skype is crashing :lolflag: )

Hi,

my mic is definitely working, because if I pronounce anything next to the mic then the sound is immediately transmitted to the speakers. Works fine to call my children from other rooms :)

But when I try to record -- no success. (Mic in Skype is also not working, etc)

I guess I am just failing to define the capture sources. However ALSA mixer looks Greek to me:

1. For some reason i have "Front Mic" and "Mic" in it -- why 2? Anyway all mics are unmuted, volume is set to max, the boost has been also tried -- it makes my family crazy when instantly transmitted to loudspeakers ;)

2. there are "Capture", "Capture 1" and "Capture 2" in Preferences -- why 3? is it for mixture purpose? (and why Sound Recorder sees only one "Capture" of those three?)

3. "Option" tab lets to define 3 input sources. If I put "Mic" and "Front Mic" there -- no success.

I tried [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but with no progress.

**Details:**
Motherboard: ASUS P5B-VM

```
$ cat /etc/issue
Ubuntu 9.04 \n \l

```

My ubuntu is AMD-64bit

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1988
```

Both model value "auto" and "6stack" in /etc/modprobe.d/alsa-base work as described above (i.e, sound from the mic is transmitted to loudspeakers, but recording isn't working)


```
$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```

---

### Post by vak on 2009-08-12
updated.

---

