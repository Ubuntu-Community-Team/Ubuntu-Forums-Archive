---
title: "Need Help On New Install 10.10"
date: 2011-04-05
forum: General Help
---

### Post by 3DGE on 2011-04-05
I just installed Ubuntu 10.10 on my older computer that had XP, and I can't get the sound or wireless internet working.

I am not too sure what sound card is in it, however I know the wireless adaptor is this one.

[http://www.airlink101.com/products/awlh6075.php](http://www.airlink101.com/products/awlh6075.php)

AWLH6075 Wireless N PCI Adapter

So I guess I need help with installing the drivers for these. 

Thanks

---

### Post by mikewhatever on 2011-04-05
Can you post the output of the following:
```
lspci | grep Net
```

---

### Post by 3DGE on 2011-04-27
Sorry for the late reply, I just finished my exam week. So I can now get back to fixing this computer.

here is the output from the lspci.


```
ar@ar-P4M266A-8235:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:0a.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
ar@ar-P4M266A-8235:~$ 

```

And here is from the lspci | grep Net

```
ar@ar-P4M266A-8235:~$ lspci | grep Net
00:0a.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R cardbus
ar@ar-P4M266A-8235:~$


```

---

### Post by lidex on 2011-04-27
For audio...Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by SkyNet2029 on 2011-04-27
His audio is a CS4281 PCI setup, as per lspci...
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
which can be setup using the following help page:

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

snd-cs4281= Cirrus Logic CS4281 for your card, which is listed under alsa-pci cards

load the module:

```
sudo modprobe snd-cs4281
```

For the wireless:

There is already a how-to on this forum for that card, located here:

[http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)


Hope that helps.

---

### Post by 3DGE on 2011-04-28
still could not get the wireless to work.

I tried following the link you gave however that must be for a older linux build because I received multiple errors and also the file no longer exists on that website so I had to get it from somewhere else and still no luck.

Any other method to get this to work ?

EDIT: Got it working now thanks guys.

I finally found a proper link to the package here [http://web.ralinktech.com/ralink/Home/Support/Linux.html]("http://web.ralinktech.com/ralink/Home/Support/Linux.html")

then just followed the steps from the link SkyNet gave me and instead of using the old 2008 package name use the 2010 one from that link above.

Thanks again

---

