---
title: "building raid array causing an IRQ error, logs included"
date: 2010-12-04
forum: General Help
---

### Post by byb3 on 2010-12-04
Hi All,

I've been trying to create a RAID5 array with 4x1TB disks.

I'm using Ubuntu 10.10, uname output:

> Linux dynamips 2.6.35-22-server #33-Ubuntu SMP Sun Sep 19 20:48:58 UTC 2010 x86_64 GNU/Linux

I have two of them connected to the on board ICH7 SATA controller (sdb and sdc), and two of them connected to an external Silicon Image SiI 3132 controller (sdd and sde).  sda is my boot disk split into several partitions and is also connected to the onboard SATA.

Everything is working fine before I create the array, here are my hdparm outputs:

> 
/dev/sdb:
 Timing cached reads:   2958 MB in  2.00 seconds = 1478.89 MB/sec
 Timing buffered disk reads:  360 MB in  3.02 seconds = 119.35 MB/sec

/dev/sdc:
 Timing cached reads:   2940 MB in  2.00 seconds = 1469.77 MB/sec
 Timing buffered disk reads:  408 MB in  3.00 seconds = 135.99 MB/sec

/dev/sdd:
 Timing cached reads:   2922 MB in  2.00 seconds = 1460.66 MB/sec
 Timing buffered disk reads:  340 MB in  3.00 seconds = 113.31 MB/sec

/dev/sde:
 Timing cached reads:   2898 MB in  2.00 seconds = 1448.43 MB/sec
 Timing buffered disk reads:  396 MB in  3.01 seconds = 131.53 MB/sec

/dev/sda:
 Timing cached reads:   2868 MB in  2.00 seconds = 1433.99 MB/sec
 Timing buffered disk reads:  166 MB in  3.02 seconds =  54.96 MB/sec
I create the raid5 array, and everything is ticking along nicely:

> 
root@dynamips:/home/adam# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde[4] sdd[2] sdc[1] sdb[0]
      2930287488 blocks level 5, 128k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.8% (8386048/976762496) finish=251.6min speed=64140K/sec

unused devices: <none>
However, roughly four minutes later, I get the following error in my syslog:

> 
Dec  5 00:51:53 dynamips kernel: [ 1175.556134] irq 19: nobody cared (try booting with the "irqpoll" option)
Dec  5 00:51:53 dynamips kernel: [ 1175.556144] Pid: 0, comm: swapper Not tainted 2.6.35-22-server #33-Ubuntu
Dec  5 00:51:53 dynamips kernel: [ 1175.556148] Call Trace:
Dec  5 00:51:53 dynamips kernel: [ 1175.556150]  <IRQ>  [<ffffffff810cb11b>] __report_bad_irq+0x2b/0xa0
Dec  5 00:51:53 dynamips kernel: [ 1175.556163]  [<ffffffff810cb31c>] note_interrupt+0x18c/0x1d0
Dec  5 00:51:53 dynamips kernel: [ 1175.556169]  [<ffffffff810856d0>] ? sched_clock_tick+0x60/0x90
Dec  5 00:51:53 dynamips kernel: [ 1175.556174]  [<ffffffff810cbb1d>] handle_fasteoi_irq+0xdd/0x110
Dec  5 00:51:53 dynamips kernel: [ 1175.556178]  [<ffffffff8100cb12>] handle_irq+0x22/0x30
Dec  5 00:51:53 dynamips kernel: [ 1175.556183]  [<ffffffff815a616c>] do_IRQ+0x6c/0xf0
Dec  5 00:51:53 dynamips kernel: [ 1175.556189]  [<ffffffff8159ed53>] ret_from_intr+0x0/0x11
Dec  5 00:51:53 dynamips kernel: [ 1175.556191]  <EOI>  [<ffffffff81012c2f>] ? mwait_idle+0x6f/0xd0
Dec  5 00:51:53 dynamips kernel: [ 1175.556199]  [<ffffffff815a279a>] ? atomic_notifier_call_chain+0x1a/0x20
Dec  5 00:51:53 dynamips kernel: [ 1175.556204]  [<ffffffff81008d93>] cpu_idle+0xb3/0x110
Dec  5 00:51:53 dynamips kernel: [ 1175.556209]  [<ffffffff815816ba>] rest_init+0x8a/0x90
Dec  5 00:51:53 dynamips kernel: [ 1175.556215]  [<ffffffff81b04c9d>] start_kernel+0x387/0x390
Dec  5 00:51:53 dynamips kernel: [ 1175.556219]  [<ffffffff81b04341>] x86_64_start_reservations+0x12c/0x130
Dec  5 00:51:53 dynamips kernel: [ 1175.556223]  [<ffffffff81b0443f>] x86_64_start_kernel+0xfa/0x109
Dec  5 00:51:53 dynamips kernel: [ 1175.556226] handlers:
Dec  5 00:51:53 dynamips kernel: [ 1175.556229] [<ffffffff813f3140>] (ata_bmdma_interrupt+0x0/0x240)
Dec  5 00:51:53 dynamips kernel: [ 1175.556238] [<ffffffff81417cc0>] (usb_hcd_irq+0x0/0x90)
Dec  5 00:51:53 dynamips kernel: [ 1175.556246] Disabling IRQ #19
Dec  5 00:52:23 dynamips kernel: [ 1205.021266] ata4: lost interrupt (Status 0x51)
Dec  5 00:52:23 dynamips kernel: [ 1205.021285] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  5 00:52:23 dynamips kernel: [ 1205.021292] ata4.01: BMDMA stat 0x66, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
Dec  5 00:52:23 dynamips kernel: [ 1205.021300] ata4.01: failed command: READ DMA EXT
Dec  5 00:52:23 dynamips kernel: [ 1205.021309] ata4.01: cmd 25/00:00:00:96:fb/00:04:01:00:00/f0 tag 0 dma 524288 in
Dec  5 00:52:23 dynamips kernel: [ 1205.021311]          res 40/00:00:00:00:00/00:00:00:00:00/10 Emask 0x24 (host bus error)
Dec  5 00:52:23 dynamips kernel: [ 1205.021319] ata4.01: status: { DRDY }
Dec  5 00:52:23 dynamips kernel: [ 1205.021330] ata4: soft resetting link
Dec  5 00:52:23 dynamips kernel: [ 1205.451294] ata4.00: configured for UDMA/133
Dec  5 00:52:23 dynamips kernel: [ 1205.551294] ata4.01: configured for UDMA/133
Dec  5 00:52:23 dynamips kernel: [ 1205.551299] ata4.01: device reported invalid CHS sector 0
Dec  5 00:52:23 dynamips kernel: [ 1205.551307] ata4: EH complete
The raid array is still being recovered, but now at a painstakingly slow speed:

> 
root@dynamips:/home/adam# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde[4] sdd[2] sdc[1] sdb[0]
      2930287488 blocks level 5, 128k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  1.8% (18040064/976762496) finish=7680.2min speed=2080K/sec

unused devices: <none>
If I repeat my hdparm tests from before I now get:

> 
/dev/sdb:
 Timing cached reads:     2 MB in  3.10 seconds = 660.92 kB/sec
 Timing buffered disk reads:    2 MB in  3.10 seconds = 661.05 kB/sec

/dev/sdc:
 Timing cached reads:     2 MB in  3.10 seconds = 660.89 kB/sec
 Timing buffered disk reads:    2 MB in  3.20 seconds = 640.01 kB/sec

/dev/sdd:
 Timing cached reads:   2932 MB in  2.00 seconds = 1465.99 MB/sec
 Timing buffered disk reads:  344 MB in  3.02 seconds = 114.09 MB/sec

/dev/sde:
 Timing cached reads:   2944 MB in  2.00 seconds = 1471.30 MB/sec
 Timing buffered disk reads:  390 MB in  3.01 seconds = 129.60 MB/sec

/dev/sda:
 Timing cached reads:   594 MB in  2.00 seconds = 296.91 MB/sec
 Timing buffered disk reads:    4 MB in  3.20 seconds =   1.25 MB/sec
As you can see, all of the drives connected to the onboard SATA are showing extremely slow disk reads.  However, the two drives connected to the external SATA card are still absolutely fine.

What is causing this bizarre error and how can I track it down to a root cause?

FYI, I have tried the smartctl on all drives and none are showing errors.

Here are my hdparm -i outputs:

> 
/dev/sdb:

 Model=SAMSUNG HD103UJ, FwRev=1AA01113, SerialNo=S13PJ9AQC07183
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


/dev/sdc:

 Model=SAMSUNG HD103SJ, FwRev=1AJ10001, SerialNo=S2C8J90Z901913
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=80
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-0,1,2,3,4,5,6,7

 * signifies the current active mode


/dev/sdd:

 Model=Hitachi HDS721010CLA332, FwRev=JP4OA39C, SerialNo=JP2921HQ1WKPXA
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=56
 BuffType=DualPortCache, BuffSize=29999kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode


/dev/sde:

 Model=SAMSUNG HD103SJ, FwRev=1AJ10001, SerialNo=S2C8J90Z901915
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-0,1,2,3,4,5,6,7

 * signifies the current active mode


/dev/sda:

 Model=WDC WD1600JD-00FYB0, FwRev=02.05D02, SerialNo=WD-WMAEK1721610
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode
For completeness here is my mdadm --detail /dev/md0 output:

> 
root@dynamips:/home/adam# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Dec  5 00:47:30 2010
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec  5 00:55:38 2010
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 128K

 Rebuild Status : 1% complete

           UUID : 5eb69e9e:bacc5f3f:0b384156:215d925b (local to host dynamips)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       64        3      spare rebuilding   /dev/sde
What causes an IRQ issue and how do I resolve it?

Thanks,

---

### Post by byb3 on 2010-12-04
I've included the /proc/interrupts.  This shows that IRQ 19 is being shared with a USB device.

> 
root@dynamips:/proc/bus/pci# cat /proc/interrupts
           CPU0       CPU1
  0:         32          4   IO-APIC-edge      timer
  1:          1          3   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          2   IO-APIC-edge      i8042
 14:         45         45   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:     169092        151   IO-APIC-fasteoi   uhci_hcd:usb5, sata_sil24
 17:        107     111200   IO-APIC-fasteoi   sata_sil24
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:     296957       3044   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
 23:         44         40   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 43:         81       7253   PCI-MSI-edge      eth0
 44:         58         60   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:     149868     190609   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:        630        626   Rescheduling interrupts
CAL:        576        601   Function call interrupts
TLB:        358        466   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         10         10   Machine check polls
ERR:          1
MIS:          0


I'll admit I don't fully understand IRQ values and their function.  But why would my USB device and the hard disks be trying to compete?

I'm going to try and unplug my USB devices to see if this resolves my problem.  

The bigger question is, how do I get my USB device to work alongside my onboard SATA?

Thanks,

---

### Post by byb3 on 2010-12-04
Well I don't want to shout too soon, but it looks to have been resolved.

The culprit was in fact a faulty SATA cable.  Somehow it was causing everything else on the same controller to be affected, which is what had me perplexed.

I traced it down due to the following repeating events in my syslog:

> 
Dec  5 03:09:14 dynamips kernel: [  246.080162] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  5 03:09:14 dynamips kernel: [  246.081408] ata4.01: BMDMA stat 0x66, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
Dec  5 03:09:14 dynamips kernel: [  246.082689] ata4.01: failed command: READ DMA EXT
Dec  5 03:09:14 dynamips kernel: [  246.084001] ata4.01: cmd 25/00:00:00:22:3e/00:04:00:00:00/f0 tag 0 dma 524288 in
Dec  5 03:09:14 dynamips kernel: [  246.086690] ata4.01: status: { DRDY }
Dec  5 03:09:14 dynamips kernel: [  246.321472] ata4.01: configured for UDMA/133
Dec  5 03:09:14 dynamips kernel: [  246.321478] ata4.01: device reported invalid CHS sector 0


I jumped to the incorrect conclusion that the hard disk itself was faulty.  However after replacing the cable this error has miraculously disappeared.

I have also unplugged my USB devices, which may have cleared up the IRQ errors or it could have been related to the faulty cable.  When I plug back in the USB devices (USB to Serial cables) I'll be able to tell.

I'm sitting nicely and the mdstat is nearly 8% complete (i'd never got past 3% before)

> 
root@dynamips:/dev# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde[4] sdd[2] sdc[1] sdb[0]
      2930287488 blocks level 5, 128k chunk, algorithm 2 [4/3] [UUU_]
      [=>...................]  recovery =  7.6% (74819328/976762496) finish=228.4min speed=65783K/sec

unused devices: <none>
root@dynamips:/dev#


---

