---
title: "sound problem in kubuntu"
date: 2010-01-05
forum: General Help
---

### Post by felious_fadger on 2010-01-05
sometimes if one program is open and playing sound like amarok or kaffeine, and another program makes a noise like kopete playing the incoming message sound, the song in amarok will just stop dead, and i get a message saying "falling back to."

help?

---

### Post by felious_fadger on 2010-01-06
bump

---

### Post by Ms_Angel_D on 2010-01-06
I can't say what your sound issues might be but to help you get help I suggest you post some system specs

First what version of Kubuntu are you using, then open Konsole and run the command ```
lspci -v
``` Post that output here.

These two key pieces of information should help others be able to better assist you. Good Luck ;)

---

### Post by felious_fadger on 2010-01-06
sorry :)

im using kubuntu 9.10 32 bit. lspci gives me this.

```


00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

```

---

### Post by felious_fadger on 2010-01-06
bump

---

### Post by Chris Musampa on 2010-01-06
This may help:
[http://kubuntuguide.org/Karmic#PulseAudio](http://kubuntuguide.org/Karmic#PulseAudio)

---

### Post by felious_fadger on 2010-01-06
thanks, but i would rather extract all my teeth with rusty scissors than use pulseaudio again.

---

### Post by Chris Musampa on 2010-01-06
I agree TBH, I spent a couple of hours messing with it last weekend and decided I don't really need multiple sounds that badly.

---

### Post by felious_fadger on 2010-01-06
lol

---

