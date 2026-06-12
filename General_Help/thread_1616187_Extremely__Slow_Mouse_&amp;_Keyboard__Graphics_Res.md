---
title: "Extremely  Slow Mouse &amp; Keyboard / Graphics Response"
date: 2010-11-07
forum: General Help
---

### Post by aepheme on 2010-11-07
I am beyond aggravated with Ubuntu... cannot seem to get it to a usable state.  I had a similar issue with Mint (and thought it might help to move to a more up-to-date version of Ubuntu).  No successes in spite of fresh installs of both the 64-bit and 32-bit versions.

Here's the deal: everything is *incredibly* slow.  As I'm typing this post, it can capture about three keystrokes before queuing the rest of them up -- can't seem to keep up with even moderately paced typing.  Moving the mouse is a jerky process and dragging windows around is also a jerky process.

So, thinking it must be some issue with Xserver/Xorg or whatever display driver I'm using.  It's a fast Intel i7 920 processor + an ATI Radeon HD 5800 + 6 gb of RAM.  I have the exact same problem with the live CD and the full install.  It's unusable due to the lag / slowness.

I've tried installing the ATI fglrx drivers as well -- on both the 64-bit and 32-bit versions -- using Ubuntu's built-in installer.  It doesn't help solve the problem; but it does introduce new ones.  It pops up "Disabling IRQ #23 early in the boot process":

```
[    3.191638] irq 23: nobody cared (try booting with the "irqpoll" option)
[    3.191641] Pid: 0, comm: swapper Not tainted 2.6.35-22-generic-pae #35-Ubuntu
[    3.191643] Call Trace:
[    3.191648]  [<c05ed4b2>] ? printk+0x2d/0x33
[    3.191652]  [<c01b1c5c>] __report_bad_irq+0x2c/0x90
[    3.191655]  [<c01b0174>] ? handle_IRQ_event+0x44/0x150
[    3.191657]  [<c01b1e1d>] note_interrupt+0x15d/0x1a0
[    3.191660]  [<c017456d>] ? sched_clock_idle_wakeup_event+0x1d/0x30
[    3.191662]  [<c01b24fc>] handle_fasteoi_irq+0xac/0xe0
[    3.191665]  [<c017e434>] ? tick_check_idle+0xb4/0xc0
[    3.191668]  [<c010b45d>] handle_irq+0x1d/0x30
[    3.191670]  [<c05f67ec>] do_IRQ+0x4c/0xc0
[    3.191673]  [<c015909a>] ? irq_exit+0x5a/0x70
[    3.191675]  [<c05f68bb>] ? smp_apic_timer_interrupt+0x5b/0x8a
[    3.191677]  [<c0109930>] common_interrupt+0x30/0x38
[    3.191681]  [<c04f79f2>] ? poll_idle+0x32/0x80
[    3.191683]  [<c04f7d5a>] cpuidle_idle_call+0x7a/0x100
[    3.191686]  [<c01082cc>] cpu_idle+0x8c/0xd0
[    3.191689]  [<c05d7a61>] rest_init+0x71/0x80
[    3.191692]  [<c085882b>] start_kernel+0x36e/0x374
[    3.191695]  [<c08589ee>] ? pass_all_bootoptions+0x0/0xa
[    3.191697]  [<c08580e8>] i386_start_kernel+0xd7/0xdf
[    3.191698] handlers:
[    3.191699] [<c0494670>] (usb_hcd_irq+0x0/0x80)
[    3.191702] [<c0494670>] (usb_hcd_irq+0x0/0x80)
[    3.191704] Disabling IRQ #23
```

Then we continue for a little bit longer and this message pops up for a brief instant before X starts:

```
[   12.482089] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[   12.482625] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[   12.483129] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[   12.504146] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

I don't think that's related to my lag / display issues (that message refers to my wireless network card), but since it pops up, thought it might be worth mentioning.

There's also a few "WARNING: Unable to load file '/etc/gdm/custom.conf': No Such file or directory" errors.  Is that related?  Any help please?  Thanks!

---

### Post by aepheme on 2010-11-08
Bump!  Any ideas?

---

### Post by aepheme on 2010-11-09
One more bump?

---

