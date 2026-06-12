---
title: "Why isn't my sound working?"
date: 2010-02-06
forum: General Help
---

### Post by JoeyF on 2010-02-06
I installed 9.10 on my Gateway MD2614U and the sound works. But when i plug the Headphones in and take them out the soun doesn't work. Even if i plug them back in. It goes back to normal once i reboot.

Any idea?

Thanks.

---

### Post by JoeyF on 2010-02-06
Ok, So i messed with the modes and then put it back on analog stereo duplex and it works when i have the headphones plugged it. But it skips every now and then.

Help?

Thanks.

---

### Post by samantha_ on 2010-02-06
> **JoeyF said:**
> Ok, So i messed with the modes and then put it back on analog stereo duplex and it works when i have the headphones plugged it. But it skips every now and then.

Help?

Thanks.

skipping likely = pulseaudio

---

### Post by JoeyF on 2010-02-06
I rebooted and it works except when i put the headphones in

---

### Post by JoeyF on 2010-02-06
I remember pulse audio(Or something else) causing problems on my Desktop. But still lost as to why i'm getting no sound. It's like it's trying to send the sound to the headphones when they're not in i guess.

---

### Post by JoeyF on 2010-02-07
Bump?

---

### Post by JoeyF on 2010-02-09
Earlier it was working but just not in Movie Player. Then it started not working on Youtube.(By not working i mean not working with the headphones). Not nothings working with the headphones. 

Could it be an issue with the phones? Or should i find some drivers?

Thanks.

---

### Post by JoeyF on 2010-02-09
I think it just does it on my Laptop.

EDIT:And now it's working again.

---

### Post by JoeyF on 2010-02-10
Right now it's only working when i have the headphones plugged in. But when i reboot it works.

```
0:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
03:00.0 Network controller: RaLink RT2860
06:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
06:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
```


What i am trying to get it to do is when i unplug the headphones go back to the built in speakers.

I heard something about upgrading ALSA. i think my card is Intel. How can i do that?


Thanks.

---

### Post by JoeyF on 2010-02-11
It doesn't do it on my Desktop and my headphones are the kind that goes in a Walkman.

How can i get it to switch back to the built in speakers when i unplug the headphones?

Thanks.

---

### Post by samantha_ on 2010-02-11
> **JoeyF said:**
> Right now it's only working when i have the headphones plugged in. But when i reboot it works.

```
0:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
03:00.0 Network controller: RaLink RT2860
06:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
06:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
```


What i am trying to get it to do is when i unplug the headphones go back to the built in speakers.

I heard something about upgrading ALSA. i think my card is Intel. How can i do that?


Thanks.
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by lidex on 2010-02-11
Can you post the output of this command please:
```
head -n 1 /proc/asound/card0/codec*
```

Download and run this script: 
[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
If you save the file locally please post it here. My browser displays this file so best to right-click on the link and select "save link as". Save to your home folder.
Run it with this command:
```
sudo bash utils_alsa-info.sh
```

---

### Post by JoeyF on 2010-03-13
Sorry for the late reply. I was waiting to try what that thread said.

```
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#1 <==
Codec: Conexant HSF
```



What's the script for?

Also, I tried downloading a driver from [http://www.linuxant.com/drivers/hsf/changes.php](http://www.linuxant.com/drivers/hsf/changes.php) but nothing.

Thanks.

---

### Post by lidex on 2010-03-13
The script tells us everything about your alsa/sound configuration. Makes it a lot easier to diagnose your problem. One thing before that, if you would, post the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by JoeyF on 2010-03-13
```
    USER        PID ACCESS COMMAND
/dev/snd/controlC0:  joey       2699 F.... pulseaudio
/dev/snd/pcmC0D0p:   joey       2699 F...m pulseaudio

```


I downloaded and ran the Script. What now?. It gave me a link. Should i PM it to you?

Thanks.

---

### Post by lidex on 2010-03-13
> **JoeyF said:**
> ```
    USER        PID ACCESS COMMAND
/dev/snd/controlC0:  joey       2699 F.... pulseaudio
/dev/snd/pcmC0D0p:   joey       2699 F...m pulseaudio

```
I downloaded and ran the Script. What now?. It gave me a link. Should i PM it to you?
Thanks.

You can post it here.

---

### Post by JoeyF on 2010-03-13
[http://www.alsa-project.org/db/?f=a8bc3cf7ee81c6657702f870c2b1863166ee714d](http://www.alsa-project.org/db/?f=a8bc3cf7ee81c6657702f870c2b1863166ee714d)


Thanks.

---

### Post by lidex on 2010-03-13
I think you should upgrade alsa. Best way is here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by JoeyF on 2010-03-14
I think that solved it! Thanks.

---

