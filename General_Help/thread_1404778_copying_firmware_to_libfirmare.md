---
title: "copying firmware to lib/firmare"
date: 2010-02-11
forum: General Help
---

### Post by nickm57 on 2010-02-11
Hi 
very new around ubuntu, but i like what i am using so far.

I'm trying to setup a Mythtv HTPC.
So far I've installed mythtv and got it to see my tuner card (Leadtek dtv1800h). 
But I can't get it to scan the tuner as I don't and can't get the firmware for the tuner installed. (xc4000)
I've tried to "sudo cp"  the file to the lib/firmware folder but it will not show up I also tried.
 
nick@nick-desktop:/lib/firmware$ sudo wget [http://kernellabs.com/firmware/xc4000/dvb-fe-xc4000-1.4.1.fw](http://kernellabs.com/firmware/xc4000/dvb-fe-xc4000-1.4.1.fw)


Also even if i get it to do this I'm not sure if mythtv will then see the tuner.
I'm at the point of dumping the card and getting something more compatible.

what am i doing wrong?

my log file for the card looks like this
Feb  8 14:10:16 nick-desktop kernel: [    8.011367] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  8 14:10:16 nick-desktop kernel: [    8.035247] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
Feb  8 14:10:16 nick-desktop kernel: [    8.038650] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
Feb  8 14:10:16 nick-desktop kernel: [    8.040378] cx8800 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 14:10:16 nick-desktop kernel: [    8.040696] cx88[0]: subsystem: 107d:6f38, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
Feb  8 14:10:16 nick-desktop kernel: [    8.040698] cx88[0]: TV tuner type -1, Radio tuner type -1
Feb  8 14:10:16 nick-desktop kernel: [    8.092795] EXT4-fs (sda8): internal journal on sda8:8
Feb  8 14:10:16 nick-desktop kernel: [    8.260010] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb  8 14:10:16 nick-desktop kernel: [    8.260014] Disabling lock debugging due to kernel taint
Feb  8 14:10:16 nick-desktop kernel: [    8.275449] [fglrx] Maximum main memory to use for locked dma buffers: 1639 MBytes.
Feb  8 14:10:16 nick-desktop kernel: [    8.275471] [fglrx]   vendor: 1002 device: 9710 count: 1
Feb  8 14:10:16 nick-desktop kernel: [    8.275696] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
Feb  8 14:10:16 nick-desktop kernel: [    8.275707] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  8 14:10:16 nick-desktop kernel: [    8.275943] [fglrx] Kernel PAT support is enabled
Feb  8 14:10:16 nick-desktop kernel: [    8.275959] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
Feb  8 14:10:16 nick-desktop kernel: [    8.292414] tuner 0-0061: chip found @ 0xc2 (cx88[0])
Feb  8 14:10:16 nick-desktop kernel: [    8.337617] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 20, latency: 32, mmio: 0xfa000000
Feb  8 14:10:16 nick-desktop kernel: [    8.337627] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Feb  8 14:10:16 nick-desktop kernel: [    8.337683] cx88[0]/0: registered device video0 [v4l2]
Feb  8 14:10:16 nick-desktop kernel: [    8.337697] cx88[0]/0: registered device vbi0
Feb  8 14:10:16 nick-desktop kernel: [    8.337705] tuner 0-0061: tuner type not set
Feb  8 14:10:16 nick-desktop kernel: [    8.338953] cx88[0]/2: cx2388x 8802 Driver Manager
Feb  8 14:10:16 nick-desktop kernel: [    8.398687] cx2388x alsa driver version 0.0.7 loaded
Feb  8 14:10:16 nick-desktop kernel: [    8.403108] cx88_audio 0000:03:06.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 14:10:16 nick-desktop kernel: [    8.403118] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Feb  8 14:10:16 nick-desktop kernel: [    8.403136] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
Feb  8 14:10:16 nick-desktop kernel: [    8.466500] __ratelimit: 9 callbacks suppressed

thanks

---

### Post by gordintoronto on 2010-02-12
You might want to look at this thread:
[http://ubuntuforums.org/showthread.php?t=648028](http://ubuntuforums.org/showthread.php?t=648028) 

You say you tried to "sudo cp the file ... but it will not show up."  Could you be more exact, please?  Sudo cp works.

If you Google 
Leadtek dtv1800h linux
there are several other interesting results.

---

### Post by nickm57 on 2010-02-12
[LEFT]thanks
when I "sudo cp dvb-fe-xc4000-1.4.1.fwp /lib/firmware/ "
 the file does not show in the folder lib/firmware folder. How ever in terminal it lists in the Dir command?




The installs listed are for the older tuner chip [http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/) lists that the XC4000 chip is not yet supported. But there is a firmware now available for it.
So my next question is how can/do I implement this firmware so mythtv can scan the channels?

Nick
[/LEFT]

---

