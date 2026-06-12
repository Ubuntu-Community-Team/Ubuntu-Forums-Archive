---
title: "IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj."
date: 2011-07-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-07-11
here is part of dmesg
```
[    6.269184] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    6.269186] vboxdrv: Successfully done.
[    6.269187] vboxdrv: Found 4 processor cores.
[    6.269234] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e8ab00
[    6.269307] vboxdrv: fAsync=0 offMin=0x64b offMax=0xa100
[    6.269341] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    6.269342] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[    6.561387] ppdev: user-space parallel port driver
[   10.469604] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```i believe the last thing is adding 4 seconds to my boot time and percentage wise that is quite a bit that is what dmesg is telling me right?
i never saw it there before today
i updated the kernel so i could have trim support i also switched to the nvidia-current in the xswap ppa instead of the one on nvidia's site
```
lchad@lucid-desktop:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
chad@lucid-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chad@lucid-desktop:~$ uname -a
Linux lucid-desktop 2.6.35-25-generic #44~lucid1-Ubuntu SMP Tue Jan 25 19:17:25 UTC 2011 x86_64 GNU/Linux
chad@lucid-desktop:~$ 

```edit:
looks like card 1 is hdmi i don't have a hdmi monitor so i am using the dvi can i disable the hdmi?

edit:
found out how to disable the nvidia hdmi audio
this was useful [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)
added:
# disable Nvidia hdmi audio
 blacklist snd_hda_codec_nvhdmi
to:
/etc/modprobe.d/blacklist.conf

---

