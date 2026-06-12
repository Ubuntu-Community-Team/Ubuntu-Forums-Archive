---
title: "Sound in Headphones only STAC92xx 11.10"
date: 2011-10-28
forum: General Help
---

### Post by mickiebims on 2011-10-28
Total linux noob here but loving the software and hope to get my feet under me.  I've installed ubuntu 11.10 on a number of computers around my house and one laptop is giving me trouble.  It's a couple of years old gateway laptop and the problem is sound plays through the headphone jack only.  I would also like to use the internal speakers.  I've dug through everything I could find here and on the net but couldn't pin anything down as to what I should do to get this working... if it's possible.  Thanks to all the experts out there and any help on my quest is greatly appreciated.  I've pasted below the results of the terminal aplay -l and lspci -v | grep -A7 -i "audio" if I need to gather any other info please let me know.

Thanks,
Mick


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)

---

### Post by mickiebims on 2011-10-30
Bump.  Anybody have a suggestion?

---

### Post by Regal953 on 2011-10-31
Get a Zalman usb 5.1 sound card and forget about the internal ATI, it worked on my gateway ml6721 STAC9200

---

