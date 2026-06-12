---
title: "no sound from headphone jack"
date: 2010-10-02
forum: General Help
---

### Post by philipballew on 2010-10-02
on my dell studio laptop that has two headphone jacks and is running Ubuntu 10.10 r.c. and has been running 10.10 since beta is having one of the headphone jacks not send sound to my headphone. how can i find out if its Ubuntu and then fix it or if its a hardware problem?

---

### Post by philipballew on 2010-10-05
anyone?

---

### Post by coibyxqx on 2010-10-05
> **philipballew said:**
> on my dell studio laptop that has two headphone jacks and is running Ubuntu 10.10 r.c. and has been running 10.10 since beta is having one of the headphone jacks not send sound to my headphone. how can i find out if its Ubuntu and then fix it or if its a hardware problem?

I have the same problem, too.
acer4930G+10.10 rc 64amd

---

### Post by philipballew on 2010-10-06
mines a 64 to. perhaps it could be software.

---

### Post by philipballew on 2010-10-09
anyone know how or what to do?

---

### Post by eveld on 2010-10-12
Same here. Headphone output died on upgrade from 10.04 to 10.10 on a (64-bit) Thinkpad T400s.

---

### Post by philipballew on 2010-10-12
so is there a way to re engage it?

---

### Post by tpsvca on 2010-10-13
The same problem with asus k52f core i3

---

### Post by iluvatar85 on 2010-10-14
Same problem here, tried to google a bit but none of the proposed solution worked. I think this is a new bug for the 10.10. 64 bit.
A bit of information:
uname -a
```
Linux march-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```

lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by philipballew on 2010-10-14
does anyone know a way to re engage this?

---

### Post by WaroDaBeast on 2010-10-15
Spotted a similar thread earlier and here's what I posted: [http://art.ubuntuforums.org/showpost.php?p=9975824&postcount=3](http://art.ubuntuforums.org/showpost.php?p=9975824&postcount=3)

Hope this fixes you guys' problem. :)

---

### Post by iluvatar85 on 2010-10-15
Dunno if it helps, but I tried to get more accurate info about the device and spotted the driver that's been in use for the audio.

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 13f3
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d7400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    [B]Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel[/B]

``` It's the same for you?
Is it correct or should be audio_intel_hda??

BTW, I've already added (ad rebooted) this line in my /etc/modprobe.d```

```/alsa-base.conf:
```
options snd-hda-intel model=Asus
```
and still no &#8220;analog headphones&#8221; in the sound settings manager. :/

---

### Post by philipballew on 2010-10-15
it seemes simple because all mine is not doing is picking up the second headphone jack. meaning the sound is working but just not recognizing theres sound needing to go to that jack?

---

### Post by iluvatar85 on 2010-10-16
Ok, I'm tring to solve this problem following the solution proposed in this bug report
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/636291](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/636291)
Essentialy, is the same solution proposed before, only with the correct model name: "thinkpad"

In this other thread is proposed to download the new kernel and use the model "hp-laptop".
[http://ubuntuforums.org/showpost.php?p=9873430&postcount=128](http://ubuntuforums.org/showpost.php?p=9873430&postcount=128)

I'll try those solution right now.

Edit: none worked. :/

---

### Post by iluvatar85 on 2010-10-20
Ok, I found a working solution in this forum. Type this command,it will create a new file in /etc/modprobe.d/ called sound.conf and put options "snd-hda-intel model=hp-laptop" into it

```
sudo mkdir /etc/modprobe.d/ && sudo echo 'options snd-hda-intel model=hp-laptop' > /etc/modprobe.d/sound.conf 
```

then download this file -> [http://ubuntuforums.org/attachment.php?attachmentid=172614&d=1287301111](http://ubuntuforums.org/attachment.php?attachmentid=172614&d=1287301111) 
and copy snd-hda-codec-conexant.ko file to /lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko  
Reboot and plug in your now perfectly working headphone! :D

---

### Post by philipballew on 2010-10-21
this command is not working in the terminal

---

### Post by iluvatar85 on 2010-10-21
> **philipballew said:**
> this command is not working in the terminal
Now it work.

---

### Post by philipballew on 2010-10-23
this isnt creating a file. it says 

mkdir: cannot create directory `/etc/modprobe.d/': File exists

---

### Post by philipballew on 2010-10-25
anyone. would i divide this code in half or somrthing like a two step process?

---

### Post by philipballew on 2010-11-03
anyone?

---

### Post by mutex023 on 2010-11-03
> **philipballew said:**
> it seemes simple because all mine is not doing is picking up the second headphone jack. meaning the sound is working but just not recognizing theres sound needing to go to that jack?

Did you try fiddling around in the sound preferences menu , which you get when you right click the sound icon ? (I've not tried ubuntu 10.10 but in 10.04, u can access it by right clicking the sound icon in the taskbar).

---

### Post by philipballew on 2010-11-14
anyone have any idea because that code and file thng wont seem to work

---

### Post by phil0stine on 2010-12-24
Any success? Exact same problem, same version, with an XPS 1730.

---

### Post by phil0stine on 2010-12-24
Okay for anybody still wondering, this post had the solution (for my case at least!). 

[http://art.ubuntuforums.org/showpost.php?p=9975824&postcount=3]("http://art.ubuntuforums.org/showpost.php?p=9975824&postcount=3")

For a studioXPS 1730, the addition to the alsa-base.conf file was 

```
options snd-hda-intel model=dell-m6 
```

Now I can post online *and* listen to music while my gf sleeps!

---

### Post by philipballew on 2010-12-25
open termanal and type "alsamixer"   then change the headphone volume thats all the way down

---

