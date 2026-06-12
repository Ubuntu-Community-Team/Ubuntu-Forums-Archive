---
title: "[kernel module] hrtimer_start (cx88_ir_work) causes wakeups"
date: 2011-05-10
forum: General Help
---

### Post by umpirsky on 2011-05-10
Hi.

I hava a problem with this hrtimer.

output speaks for itself:

>sudo powertop

< Detailed C-state information is not P-states (frequencies)
                                        2.31 Ghz    21.4%
                                        2.21 Ghz     0.0%
                                        2.00 Ghz     0.0%
                                        1.80 Ghz     4.9%
                                        1000 Mhz    73.7%

Wakeups-from-idle per second : 555.1    interval: 5.0s                                                                                                                                  
no ACPI power usage estimate available

Top causes for wakeups:
  90.2% (1001.2)   [kernel module] hrtimer_start (cx88_ir_work)
   1.8% ( 20.0)   knotify4
   1.2% ( 13.0)   [kernel scheduler] Load balancing tick
   1.0% ( 11.6)   postgres
   1.0% ( 11.0)   [Rescheduling interrupts] <kernel IPI>



When I run

dmesg | grep cx88
[   15.248507] cx88_audio 0000:01:06.1: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   15.250028] cx88[0]: subsystem: 107d:6618, board: Leadtek TV2000 XP Global [card=61,autodetected], frontend(s): 0
[   15.250030] cx88[0]: TV tuner type 71, Radio tuner type 71
[   15.355162] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   15.545826] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   15.596753] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[   15.657154] input: cx88 IR (Leadtek TV2000 XP Glob as /devices/pci0000:00/0000:00:08.0/0000:01:06.1/rc/rc0/input4
[   15.657254] rc0: cx88 IR (Leadtek TV2000 XP Glob as /devices/pci0000:00/0000:00:08.0/0000:01:06.1/rc/rc0
[   15.657304] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   15.657627] cx8800 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   15.657636] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 16, latency: 32, mmio: 0xf4000000
[   15.657716] cx88[0]/0: registered device video0 [v4l2]
[   15.657753] cx88[0]/0: registered device vbi0
[   15.657796] cx88[0]/0: registered device radio0
[   54.835243] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835253] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835260] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835267] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835274] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835281] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835288] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835294] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835301] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835308] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835315] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835321] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835328] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835335] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835341] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835348] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835355] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835362] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835368] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835375] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835382] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835389] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835395] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835402] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835409] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835415] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835422] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835429] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835436] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835443] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835449] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835456] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835463] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835469] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835476] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835483] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835490] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835496] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835503] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835510] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835516] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835523] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835530] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835537] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835543] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835550] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835557] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835563] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835570] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835577] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   54.835581] cx88[0]/1: IRQ loop detected, disabling interrupts

How can I solve this, my computer is getting very slow?

---

### Post by demilord on 2011-05-10
what cpu do you have, what version of ubuntu do you run?  Did you file it at launchpad as bug report?

---

### Post by umpirsky on 2011-05-11
#rmmod -f cx88_alsa 

fixed it, thanks.

---

