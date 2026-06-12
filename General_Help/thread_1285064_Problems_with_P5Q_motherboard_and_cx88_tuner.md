---
title: "Problems with P5Q motherboard and cx88 tuner"
date: 2009-10-07
forum: General Help
---

### Post by bwobbones on 2009-10-07
Hi all,

  I recently had to swap out a dead motherboard and I replaced it with an Asus P5Q.  Now I have an intermittent fault with *one* of my tuners, more specifically one of the PCI slots that my tuner sits in.

  I have 2 Leadtek DTV1000s that have sered me very well for a few years now.  The one in PCI slot 1 works, the one in the other slot doesn't and I get a "Tuner is asleep" message from myth.  If I swap them around, or only have one, PCI slot 1 always works.  Does anyone have any ideas how to resolve this?  It doesn't happen all of the time, about 2 reboots in 3 will present the problem and on the third it will perform as normal.

  Here is a lspci (you can see that the card is detected but there is no MPEG port):

  05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

and I get this message in my dmesg:

cx88[1]: Your board has no valid PCI Subsystem ID and thus can't
[   13.057526] cx88[1]: be autodetected.  Please pass card=<n> insmod option to
[   13.057526] cx88[1]: workaround that.  Redirect complaints to the vendor of
[   13.057527] cx88[1]: the TV card.  Best regards,
[   13.057528] cx88[1]:         -- tux
[   13.057698] cx88[1]: Here is a list of valid choices for the card=<n> insmod option:
[   13.057735] cx88[1]:    card=0 -> UNKNOWN/GENERIC
[   13.057769] cx88[1]:    card=1 -> Hauppauge WinTV 34xxx models
<snip>
[   13.061191] cx88[1]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   13.061192] cx88[1]: TV tuner type -1, Radio tuner type -1
[   13.329931]   alloc irq_desc for 22 on node -1
[   13.329934]   alloc kstat_irqs on node -1
[   13.329939] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.329974] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.519055] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.521209] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   13.521212] cx88/2: registering cx8802 driver, type: dvb access: shared
[   13.521214] cx88[0]/2: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35]
[   13.521216] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.521218] cx8802_alloc_frontends() allocating 1 frontend(s)
[   13.654743] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   13.658123] All bytes are equal. It is not a TEA5767
[   13.658175] tuner 1-0060: chip found @ 0xc0 (cx88[1])
[   13.659531] SGI XFS Quota Management subsystem
[   13.681733] XFS mounting filesystem sda1
[   13.708013] tuner 1-0043: chip found @ 0x86 (cx88[1])
[   13.764657] tda9887 1-0043: creating new instance
[   13.764659] tda9887 1-0043: tda988[5/6/7] found
[   13.800710] Starting XFS recovery on filesystem: sda1 (logdev: internal)
[   13.805725] cx88[1]/0: found at 0000:05:00.0, rev: 5, irq: 16, latency: 64, mmio: 0xfd000000
[   13.805734] IRQ 16/cx88[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.805795] cx88[1]/0: registered device video0 [v4l2]
[   13.805811] cx88[1]/0: registered device vbi0
[   13.805826] tuner 1-0060: tuner type not set
[   13.806189] cx8800 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.806197] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 18, latency: 64, mmio: 0xfb000000
[   13.806203] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.806229] cx88[0]/0: registered device video1 [v4l2]
[   13.806245] cx88[0]/0: registered device vbi1
[   13.839205] DVB: registering new adapter (cx88[0])
[   13.839208] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...


I've tried the insmod option with no luck.  Running 0.22 on Mythbuntu 9.10 at the moment, but had the same problem with 0.21-fixes on 9.04. 

Thanks,

Greg

---

