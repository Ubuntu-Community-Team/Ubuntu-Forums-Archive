---
title: "Why don't my headphones work in 10.04 or 10.10?"
date: 2010-10-13
forum: General Help
---

### Post by josephellengar on 2010-10-13
So, I've had this problem since I clean-installed Ubuntu on this computer and have lived with it, but I was really hoping that upgrading (clean install) to 10.10 would fix it.  It didn't.

Anyway, my headphones don't work.  When I plug headphones into the computer, the sound still comes out of the main speakers, and this is with all of the headphone jacks on my computer.  Furthermore, the headphones work in all of my jacks when I am in windows.  I can't figure it out.  Does anybody know why this might be?

---

### Post by jiykauu on 2010-10-13
I didn't have that problem in 10.04, now my problem is i plug headphones they work but speakers work along with them, so its really annoying. In Audio setting i changed from analog output into headphones and only on maximum i hear really quiet sound from headphones which is useless.

---

### Post by josephellengar on 2010-10-13
> **jiykauu said:**
> I didn't have that problem in 10.04, now my problem is i plug headphones they work but speakers work along with them, so its really annoying. In Audio setting i changed from analog output into headphones and only on maximum i hear really quiet sound from headphones which is useless.

Well, at least that means I'm not the only one with this problem.  What type of computer do you have this problem on?  My headphones work on my netbook but fail on my HP dv7t quad edition notebook (Nvidia graphics, intel i7 processor, etc)

```


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci:
```


00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
05:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by josephellengar on 2010-10-15
Anybody else have any idea?

---

### Post by josephellengar on 2010-10-19
bump

---

### Post by josephellengar on 2010-10-20
bump

---

### Post by Frogs Hair on 2010-10-20
To view your mixer status in the terminal  type alsamixer into the terminal and press enter. To learn about the mixer type man alsamixer in a cleared terminal . you may find something that will point you in the right direction.

Edit: I found a bug report on this issue. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/650863](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/650863)

---

### Post by josephellengar on 2010-10-20
> **Frogs Hair said:**
> To view your mixer status in the terminal  type alsamixer into the terminal and press enter. To learn about the mixer type man alsamixer in a cleared terminal . you may find something that will point you in the right direction.

Edit: I found a bug report on this issue. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/650863](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/650863)

Oh, thanks, good to know that a fix has been committed.

---

### Post by ushio81 on 2011-03-02
> **josephellengar said:**
> Oh, thanks, good to know that a fix has been committed.

I have installed latest Alsa drivers but I still have the problem. Did it work for you?

---

### Post by David D. on 2011-03-02
I had this problem which turned out to be a failure to sense the headphones being plugged into the jack.  This was fixed with the following in terminal
```
gksudo gedit/etc/modprobe.d/alsa-base.conf
```

Insert the following at the end of the file that opens for editing

> options snd-hda-intel model=hp-dv5 enable_msi=1

Save the edited file, close, then reboot.

---

### Post by Subhajit on 2011-03-02
p { margin-bottom: 0.21cm; }a:link {  }  check out */proc/asound/card0/codec#**. you can find the device's make.

 	
 	go to [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) 	to check the model-name according to your system architecture/type. for me it was 'dell-vostro'


 	Update 	/etc/modprobe.d/alsa-base.conf by adding this line to its end: 	*options 	snd-hda-intel model=dell-vostro. *(change dell-vostro to what you find in the list).
[I]
[/I]
 	Restart 	the system*.* **

---

