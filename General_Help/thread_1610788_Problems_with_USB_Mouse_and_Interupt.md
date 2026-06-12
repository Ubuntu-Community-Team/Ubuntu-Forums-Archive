---
title: "Problems with USB Mouse and Interupt"
date: 2010-11-01
forum: General Help
---

### Post by harpert on 2010-11-01
Hi there,
my Problem is that now and then my mouse suddenly slows down.
Working with a lazy mouse it quite annoying.
I looked into dmesg and got the following lines:
--------------------------------
[ 2248.747253] ssindex[10762]: segfault at 8 ip 011b0c30 sp bfb49840 error 4 in excel.so[118c000+8a000]
[ 2969.887881] irq 20: nobody cared (try booting with the "irqpoll" option)
[ 2969.887888] Pid: 0, comm: swapper Tainted: P           2.6.32-25-generic #45-Ubuntu
[ 2969.887892] Call Trace:
[ 2969.887901]  [<c058abfd>] ? printk+0x1d/0x20
[ 2969.887907]  [<c01a189c>] __report_bad_irq+0x2c/0x90
[ 2969.887913]  [<c019ffb4>] ? handle_IRQ_event+0x54/0x150
[ 2969.887917]  [<c01a1a50>] note_interrupt+0x150/0x190
[ 2969.887922]  [<c016dafe>] ? sched_clock_tick+0x5e/0xa0
[ 2969.887927]  [<c01a205c>] handle_fasteoi_irq+0xac/0xd0
[ 2969.887932]  [<c01059ed>] handle_irq+0x1d/0x30
[ 2969.887937]  [<c059170c>] do_IRQ+0x4c/0xc0
[ 2969.887941]  [<c0103a30>] common_interrupt+0x30/0x40
[ 2969.887946]  [<c010aaa5>] ? mwait_idle+0x55/0xa0
[ 2969.887950]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 2969.887955]  [<c05884f3>] start_secondary+0xc6/0xc8
[ 2969.887958] handlers:
[ 2969.887960] [<c0446120>] (usb_hcd_irq+0x0/0x80)
[ 2969.887967] [<c0446120>] (usb_hcd_irq+0x0/0x80)
[ 2969.887972] [<c0429970>] (ata_sff_interrupt+0x0/0xd0)
[ 2969.887978] Disabling IRQ #20
[ 2997.684531] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd upowerd rqt 192 rq 9 len 8 ret -110
[ 3000.156032] usb 1-8.1: reset high speed USB device using ehci_hcd and address 7
[ 3027.684583] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd upowerd rqt 192 rq 9 len 8 ret -110
[ 3057.684575] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd upowerd rqt 192 rq 9 len 8 ret -110
-----------------------------------------------------------
It seems that IRQ 20 is causing the trouble. 
However I have no idea why this happens and how to solve this problem
The only thing  I can do is to restart the system.


Info:
- Ubuntu 10.04 
-Two USB HDs
- Keyboard and mouse connected to the USB as well
- a scanner also connected to teh USB

Any ideas what may couse this and how to solve???

Harpert

---

