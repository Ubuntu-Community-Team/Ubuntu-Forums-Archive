---
title: "The Hardes Sound Issuse EVER On Ubuntu"
date: 2010-06-10
forum: General Help
---

### Post by hxcfelony on 2010-06-10
OK! I have had this problem for far too long, my onboard sound will not work, i went from Xubuntu, to Vista now to here! NO the mute is not on, it says i have sound but I dont! I did the lspci command and got this:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
ALSO I have a custom built computer that came with a Rocket Fish sound card model RF-51SDCD that I rip out (no known drivers for that sound card). I have a Compaq Presario 061. Model number is DT076A-ABA S6200CL NA410. My motherboard is an ASUSTek Kamet2. The firmeware is Phoenix Technologies version 3.05 (cant find an update for that either).
Well I hope the Ubuntu community can help because this is the last straw for me, I never had any trouble like this and this is very frustrating.
Good Luck!

---

### Post by SlidingHorn on 2010-06-10
what does this return

```
sudo aplay -l
```

---

### Post by hxcfelony on 2010-06-10
> **SlidingHorn said:**
> what does this return

```
sudo aplay -l
```
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Thats what I got

---

### Post by clhsharky on 2010-06-10
hxcfelony

Have a look here

Sticky: Comprehensive Sound Problem Solutions Guide 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Sharky

---

### Post by hxcfelony on 2010-06-10
Sharky i have tdone this one before, I thank you and I recently rip out the sound card. I actually went in my bios and turned the onboard auto to enabled. NO SOUND STILL. If you have further info plz help me, i dont want to lose my computer :(

---

### Post by SlidingHorn on 2010-06-10
what kernel are you running?

```
uname -a
```

---

### Post by hxcfelony on 2010-06-10
Linux evanpwn-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
Thats what i got, i hope this helps!

---

