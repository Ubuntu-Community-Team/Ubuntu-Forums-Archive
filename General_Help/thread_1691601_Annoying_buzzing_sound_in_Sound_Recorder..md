---
title: "Annoying buzzing sound in Sound Recorder."
date: 2011-02-20
forum: General Help
---

### Post by t0p on 2011-02-20
When I record my voice, using the gnome-sound-recorder, I get an awful buzzing sound in the background.  Altering the input volume or the output volume the recorder makes no difference: it makes the buzzing sound louder or quieter - but also makes my recorded voice louder or quieter.

Can anyone offer me a solution that gets rid of the buzz whilst keeping the voice volume as it should be?

---

### Post by topet2k12001 on 2011-06-06
Friends,

I have the same problem too. I am dual-booting with Windows 7 and I have never encountered the problem there.

**Problem Summary**

All other audio features (i.e. playback) are working fine both in Ubuntu 10.10 and Windows 7 without any problems. As an interim solution I boot into Windows 7 everytime I want to create a clean recording.

Recording is working fine with no other problem; it's just the buzzing background static noise that is annoying me. It's like the background static sound you hear when you plug in an electric guitar to an amplifier.

Problem is being encountered in any recording application in Ubuntu.

**My motherboard details**

[http://www.msi.com/product/mb/G41M4-F.html#?div=Detail](http://www.msi.com/product/mb/G41M4-F.html#?div=Detail)

**My audio card details (this is integrated into the motherboard by the way)**

[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141)

> **[IMG]http://www.msi.com/pic/image/little_icon/Bult_ar_org.gif[/IMG][FONT=Arial][COLOR=#000000]Audio[/COLOR][/FONT]**             [LEFT]• Chipset integrated by Realtek® ALC888S
- Flexible 8-channel audio with jack sensing
- Compliant with Azalia 1.0 Spec
- Meet Microsoft Vista Premium spec
[/LEFT]
[LEFT]**lspci output**
[/LEFT]
 
```
administrator@29-G:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
administrator@29-G:~$ 

```**My playback devices**

```
administrator@29-G:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```**My capture devices**

```
administrator@29-G:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```[B]My kernel details

[/B]```
administrator@29-G:~$ uname -a
Linux 29-G 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux
administrator@29-G:~$
``` Any help would be much appreciated. :)

[B]EDIT: other steps tried include editing

[/B]```
/etc/modprobe.d/alsa-base.conf
```to add "options-hda-intel position_fix=2" such as the one depicted in this URL: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/572146](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/572146). But I figured that this fix may not apply to the problem I'm trying to solve. It seems to be a solution for either fixing the microphone not working (or audio capture not working, which is not the case for me) or a solution for fixing crackling sound (mine is a buzzing static sound).

---

### Post by icarus74 on 2011-06-06
Very similar (same) problem, or noisy (but not untolerable buzz) faced on Compaq CQ42-450TU laptop (intel Pentium Dual-Core P6200 running at 2.13GHz, with 1GB RAM). Playback of prerecorded audio is clean as expected, but it is only the recording which is an issue. Running Ubuntu 64-bit 11.04 desktop on this laptop.

---

### Post by stinkeye on 2011-06-07
No problems here using a usb headset.

---

