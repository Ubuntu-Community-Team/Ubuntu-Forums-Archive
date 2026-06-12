---
title: "HDMI sound with ALSA (Pulse Audio removed)?"
date: 2010-09-28
forum: General Help
---

### Post by bakinsoda on 2010-09-28
Hi everyone,

I'm currently using Ubuntu 10.04 (amd64) on my Toshiba Portege r705 laptop.  To get through the HDMI port, what I did was select the HDMI output in the Pulse Audio menu.  This worked fine.

However, I recently [removed]("http://ubuntuforums.org/showthread.php?t=1351369") Pulse Audio because it does not allow simultaneous sound from multiple programs; ALSA works for simultaneous sound.  I also followed [these]("http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/") instructions to get ALSA to work better with Ubuntu (menu and keyboard shortcuts).

I don't know how to get HDMI working with ALSA alone though.  I searched for it but couldn't find much help.  Is there a way to select HDMI as the output?

Some information that may be useful:
```

$ lspci | less
...
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 36
        Memory at d4620000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
...
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Slim Odds on 2010-09-28
Pulse Audio most definitely DOES allow for multiple programs to output audio at the same time. I do it all the time.

Like right now:
[INDENT]Pandora is playing music (Adobe AIR)
Pokerstars is making sounds when needed (WINE)
System sounds: Yes
Tried RhythmBox also: lots of audio overlap
[/INDENT]

---

### Post by bakinsoda on 2010-09-28
Can you try going to youtube to watch a video, and, while the tab is not closed, try playing something with rhythmbox?

---

### Post by Slim Odds on 2010-09-29
> **bakinsoda said:**
> Can you try going to youtube to watch a video, and, while the tab is not closed, try playing something with rhythmbox?

Same time, no problem. Other sounds mixed in too.....

---

### Post by bakinsoda on 2010-09-29
Are you still on Karmic?  Wonder if it's a Lucid thing.

Can you give as much information as possible?  What Pulse Audio version are you on?  What is your hardware?  Do you have ALSA installed at all?

I would expect it's just me, but the links I've posted up show that others have had the same issue.

---

### Post by Slim Odds on 2010-10-01
> **bakinsoda said:**
> Are you still on Karmic?  Wonder if it's a Lucid thing.

Can you give as much information as possible?  What Pulse Audio version are you on?  What is your hardware?  Do you have ALSA installed at all?

I would expect it's just me, but the links I've posted up show that others have had the same issue.

I'm on Lucid (like it shows over there under my avatar).

Latest versions of PulseAudio and ALSA from the Lucid repositories. Audo hardware is on my mobo.

```
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fe020000-fe023fff

```

---

### Post by bakinsoda on 2010-10-19
Both my netbook and laptop has simultaneous sound under Ubuntu 10.10.  Thanks.

---

