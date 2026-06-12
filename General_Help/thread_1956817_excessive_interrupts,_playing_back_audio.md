---
title: "excessive interrupts, playing back audio?"
date: 2012-04-11
forum: General Help
---

### Post by d3rr1 on 2012-04-11
Hello there,

i've been using powertop to try and optimize my computer performance and I noticed while playing back audio I get interrupts above 1500. My question is. Is this normal? I'm also looking for some helpt to decrease [i915] interrupts.

Here are my stats while playing back music in chromium:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (21.7%)       Turbo Mode    13.8%
polling           0.0ms ( 0.0%)         2.00 Ghz     0.2%
C1 mwait          0.6ms ( 3.8%)         1400 Mhz     0.2%
C2 mwait          1.1ms ( 2.9%)         1000 Mhz     0.2%
C3 mwait          1.3ms ( 0.4%)          800 Mhz    85.0%
C4 mwait          2.2ms (71.3%)


Wakeups-from-idle per second : 420.1    interval: 10.0s
Power usage (5 minute ACPI estimate) :   0.1 W (918.0 hours left)

Top causes for wakeups:
  67.3% (1598.6)   [Rescheduling interrupts] <kernel IPI>
   9.5% (224.8)   chromium-browse
   3.8% ( 89.6)   kworker/0:1
   2.9% ( 68.8)   [kernel scheduler] Load balancing tick
   2.9% ( 68.3)   [iwlagn] <interrupt>
   2.7% ( 64.3)   kworker/0:0
   2.6% ( 62.0)   alsa-sink
   2.6% ( 61.8)   USB device 2-1.2 : USB-PS/2 Optical Mouse (Logitech)
   2.3% ( 55.2)   [ehci_hcd:usb2] <interrupt>
   0.0% (  0.1)D  Chrome_HistoryT
   0.7% ( 15.7)   [i915] <interrupt>
   0.6% ( 13.2)   [TLB shootdowns] <kernel IPI>
   0.5% ( 12.0)   SignalSender
   0.4% (  9.5)   [ahci] <interrupt>
```

And how are my idle stats?

```
Wakeups-from-idle per second :  9.8     interval: 30.0s
Power usage (5 minute ACPI estimate) :   0.0 W (1620.0 hours left)

Top causes for wakeups:
  23.3% ( 11.4)   [Rescheduling interrupts] <kernel IPI>
  17.1% (  8.3)   [i915] <interrupt>
  13.5% (  6.6)   kworker/0:0
  12.7% (  6.2)   kworker/0:1
   9.4% (  4.6)   [kernel scheduler] Load balancing tick
   5.1% (  2.5)   [ahci] <interrupt>
   2.2% (  1.1)   [kernel core] hrtimer_start (tick_sched_timer)
   2.1% (  1.0)   Xorg
   2.1% (  1.0)   gvfs-afc-volume
   2.1% (  1.0)   gnome-terminal
   1.6% (  0.8)   [Function call interrupts] <kernel IPI>
   1.4% (  0.7)   indicator-cpufr
   1.1% (  0.5)   udisks-daemon
   1.0% (  0.5)   kworker/3:1
```

I wonder if I could make anything better? Tnx for your help

---

### Post by kiirokurisu on 2012-04-11
Those stats all look pretty normal to me (apart from the power consumption, what the?). In your tables, i915 is not the chief source of interrupts. Incidentally i915 is the graphics subsystem so it's expected to generate a substantial number of interrupts.

---

### Post by d3rr1 on 2012-04-12
> **kiirokurisu said:**
> Those stats all look pretty normal to me (apart from the power consumption, what the?).

Allright thanks for that. About my ACPI stats:

If I'm on battery it gives normal estimates. This time I was plugged in and then it gives those weird stats. I have no clue what's that all about.

---

### Post by sentistawlben on 2012-04-12
Oui en effet, une activité "3d" me parait plus séduisante mais peut être que cela est plus difficile et plus couteux pour commencer... Je dispose d'un budget de 300€/mois tt compris..

---

