---
title: "Suspend without user intervention"
date: 2010-08-01
forum: General Help
---

### Post by Jon Monreal on 2010-08-01
Hello everyone,

I have a machine that I leave on overnight, and noticed this morning that it had suspended.

Interestingly enough, the syslog makes it look like it's resumed during the same second that its suspended (or it might just be that it's very early here and I'm reading this wrong). I am certain that I didn't catch it that quickly. I've attached the relevant bits:

```
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: The canary thread is apparently starving. Taking action.
Aug  1 04:49:49 JonE6400 kernel: [73610.312707] PM: Syncing filesystems ... done.
Aug  1 04:49:49 JonE6400 kernel: [73610.422831] PM: Preparing system for mem sleep
Aug  1 04:49:49 JonE6400 kernel: [73610.422834] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: Demoting known real-time threads.
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: Successfully demoted thread 1922 of process 1912 (n/a).
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: Successfully demoted thread 1918 of process 1912 (n/a).
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: Successfully demoted thread 1912 of process 1912 (n/a).
Aug  1 04:49:49 JonE6400 rtkit-daemon[1697]: Demoted 3 threads.
Aug  1 04:49:49 JonE6400 acpid: client 1225[0:0] has disconnected
Aug  1 04:49:49 JonE6400 acpid: client 1225[0:0] has disconnected
Aug  1 04:49:49 JonE6400 bluetoothd[9598]: HCI dev 0 down
Aug  1 04:49:49 JonE6400 bluetoothd[9598]: Adapter /org/bluez/9597/hci0 has been disabled
Aug  1 04:49:49 JonE6400 bluetoothd[9598]: Stopping security manager 0
Aug  1 04:49:49 JonE6400 kernel: [73610.423716] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug  1 04:49:49 JonE6400 kernel: [73610.423757] PM: Entering mem sleep
Aug  1 04:49:49 JonE6400 kernel: [73610.423769] Suspending console(s) (use no_console_suspend to debug)
Aug  1 04:49:49 JonE6400 kernel: [73610.426244] btusb_intr_complete: hci0 urb ffff880082d740c0 failed to resubmit (1)
Aug  1 04:49:49 JonE6400 kernel: [73610.427240] btusb_bulk_complete: hci0 urb ffff8800b35fbe40 failed to resubmit (1)
Aug  1 04:49:49 JonE6400 kernel: [73610.428238] btusb_bulk_complete: hci0 urb ffff8800b62fec00 failed to resubmit (1)
Aug  1 04:49:49 JonE6400 kernel: [73610.620158] PM: suspend of drv:ieee80211 dev:phy0 complete after 119.917 msecs
Aug  1 04:49:49 JonE6400 kernel: [73610.640199] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Aug  1 04:49:49 JonE6400 kernel: [73610.640639] sd 0:0:0:0: [sda] Stopping disk
Aug  1 04:49:49 JonE6400 kernel: [73611.640654] PM: suspend of drv:sd dev:0:0:0:0 complete after 1000.457 msecs
Aug  1 04:49:49 JonE6400 kernel: [73612.033903] PM: suspend of drv:psmouse dev:serio1 complete after 373.619 msecs
Aug  1 04:49:49 JonE6400 kernel: [73612.133614] serial 00:09: disabled
Aug  1 04:49:49 JonE6400 kernel: [73612.134714] ACPI handle has no context!
Aug  1 04:49:49 JonE6400 kernel: [73612.134721] sdhci-pci 0000:03:01.1: PCI INT C disabled
Aug  1 04:49:49 JonE6400 kernel: [73612.134726] ACPI handle has no context!
Aug  1 04:49:49 JonE6400 kernel: [73612.480402] HDA Intel 0000:00:1b.0: PCI INT A disabled
Aug  1 04:49:49 JonE6400 kernel: [73612.500220] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 129.951 msecs
Aug  1 04:49:49 JonE6400 kernel: [73612.500439] e1000e 0000:00:19.0: PCI INT A disabled
Aug  1 04:49:49 JonE6400 kernel: [73612.500444] e1000e 0000:00:19.0: PME# enabled
Aug  1 04:49:49 JonE6400 kernel: [73612.500454]  pci0000:00: wake-up capability enabled by ACPI
Aug  1 04:49:49 JonE6400 kernel: [73612.520556] PM: suspend of devices complete after 2096.367 msecs
Aug  1 04:49:49 JonE6400 kernel: [73612.520558] PM: suspend devices took 2.100 seconds
Aug  1 04:49:49 JonE6400 kernel: [73612.520869] ricoh-mmc: Suspending.
Aug  1 04:49:49 JonE6400 kernel: [73612.520877] ricoh-mmc: Controller is now re-enabled.
Aug  1 04:49:49 JonE6400 kernel: [73612.560239] PM: late suspend of devices complete after 39.677 msecs
Aug  1 04:49:49 JonE6400 kernel: [73612.568115] ACPI: Preparing to enter system sleep state S3
Aug  1 04:49:49 JonE6400 kernel: [73612.640010] Disabling non-boot CPUs ...
Aug  1 04:49:49 JonE6400 kernel: [73612.640029] CPU0 attaching NULL sched-domain.
Aug  1 04:49:49 JonE6400 kernel: [73612.640031] CPU1 attaching NULL sched-domain.
Aug  1 04:49:49 JonE6400 kernel: [73612.800014] CPU0 attaching NULL sched-domain.
Aug  1 04:49:49 JonE6400 kernel: [73612.910017] CPU 1 is now offline
Aug  1 04:49:49 JonE6400 kernel: [73612.910019] SMP alternatives: switching to UP code
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] Extended CMOS year: 2000
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] Back to C!
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] CPU0: Thermal monitoring enabled (TM1)
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] Extended CMOS year: 2000
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] Enabling non-boot CPUs ...
Aug  1 04:49:49 JonE6400 kernel: [73612.916416] SMP alternatives: switching to SMP code
Aug  1 04:49:49 JonE6400 kernel: [73612.922270] Booting processor 1 APIC 0x1 ip 0x6000
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] Initializing CPU#1
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU: L2 cache: 6144K
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU 1/0x1 -> Node 0
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU: Physical Processor ID: 0
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU: Processor Core ID: 1
Aug  1 04:49:49 JonE6400 kernel: [73612.916044] CPU1: Thermal monitoring enabled (TM1)
Aug  1 04:49:49 JonE6400 kernel: [73613.080078] CPU1: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz stepping 0a
Aug  1 04:49:49 JonE6400 kernel: [73613.080140] CPU0 attaching NULL sched-domain.
Aug  1 04:49:49 JonE6400 kernel: [73613.150019] CPU0 attaching sched-domain:
Aug  1 04:49:49 JonE6400 kernel: [73613.150021]  domain 0: span 0-1 level MC
Aug  1 04:49:49 JonE6400 kernel: [73613.150022]   groups: 0 1
Aug  1 04:49:49 JonE6400 kernel: [73613.150026] CPU1 attaching sched-domain:
Aug  1 04:49:49 JonE6400 kernel: [73613.150027]  domain 0: span 0-1 level MC
Aug  1 04:49:49 JonE6400 kernel: [73613.150028]   groups: 1 0
Aug  1 04:49:49 JonE6400 kernel: [73613.150396] CPU1 is up
Aug  1 04:49:49 JonE6400 kernel: [73613.151176] ACPI: Waking up from system sleep state S3
Aug  1 04:49:49 JonE6400 kernel: [73613.300498] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x80100, writing 0x1a0100)
....

```

I'm not too worried about it, but appreciate any help.

---

### Post by Jon Monreal on 2010-08-01
Bump.

No other threads (forum threads, that is) dealing with the "canary thread" report standby problems, just performance problems.

If anyone is wondering what came before and after that in the syslog: the last message before was hours before, and messages after deal with the computer waking (in which there appears to be nothing out of the ordinary).

Again, thanks for any help.

---

