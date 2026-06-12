---
title: "X screen crashes randomly on resume"
date: 2009-11-21
forum: General Help
---

### Post by nerdy_kid on 2009-11-21
LD_BIND_NOW=1 error in X log -- which (says the log) means that the dlloader doesnt work which means that my NVIDIA drivers wont load which means that no screens are found which means that the X server crashes which means that all my apps die!!!!!

is there at least a workaround (i.e. force LD_BIND_NOW=0) ??

---

### Post by Johnny B on 2009-11-21
i've never heard of such an error, but if i were in your position, i would check that your using the correct nvidia drivers, then reinstall them.

---

### Post by nerdy_kid on 2009-11-22
ok thanks, i upgraded to the drivers of NVIDIA site - 190.42.  hope that helps

---

### Post by nerdy_kid on 2009-11-23
no fix.

note:

i have been messing with LD_PRELOAD if that somehow effects anything. I dont think it would, as i didnt export it.


this is really irratating!

there might be a pattern when i change the power status before resuming (like plugin the laptop in before resuming, or unpluging it)

????


[edit] is there some way to force LD_BIND_NOW=0 on X resume?

---

### Post by nerdy_kid on 2009-11-30
need help people!!!! please!!!

---

### Post by nerdy_kid on 2009-11-30
heres syslog: something really wierd is happening:


```


2009-11-30 18:20:28    nerdy_kid-pc    anacron[12516]    Anacron 2.3 started on 2009-11-30
2009-11-30 18:20:28    nerdy_kid-pc    anacron[12516]    Normal exit (0 jobs run)
2009-11-30 18:20:28    nerdy_kid-pc    NetworkManager    <info>  Sleeping...
2009-11-30 18:20:28    nerdy_kid-pc    NetworkManager    <info>  (eth2): now unmanaged
2009-11-30 18:20:28    nerdy_kid-pc    NetworkManager    <info>  (eth2): device state change: 8 -> 1 (reason 37)
2009-11-30 18:20:28    nerdy_kid-pc    NetworkManager    <info>  (eth2): deactivating device (reason: 37).
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth2): canceled DHCP transaction, dhcp client pid 12123
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <WARN>  check_one_route(): (eth2) error -34 returned from rtnl_route_del(): Sucess#012
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    Withdrawing address record for 192.168.1.2 on eth2.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.1.2.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    Interface eth2.IPv4 no longer relevant for mDNS.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth2): cleaning up...
2009-11-30 18:20:29    nerdy_kid-pc    wpa_supplicant[1298]    CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth2): taking down device.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    querier.c: querier_remove() called but no querier to remove.
2009-11-30 18:20:29    nerdy_kid-pc    avahi-daemon[1072]    Withdrawing address record for fe80::216:44ff:fee3:8eff on eth2.
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth0): now unmanaged
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth0): device state change: 2 -> 1 (reason 37)
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth0): cleaning up...
2009-11-30 18:20:29    nerdy_kid-pc    NetworkManager    <info>  (eth0): taking down device.
2009-11-30 18:20:29    nerdy_kid-pc    kernel    [12772.759009] b44: eth0: powering down PHY
2009-11-30 18:20:31    nerdy_kid-pc    acpid    client 2178[0:0] has disconnected
2009-11-30 18:20:31    nerdy_kid-pc    kdm[1044]    X server for display :0 terminated unexpectedly
2009-11-30 18:20:32    nerdy_kid-pc    acpid    client 2178[0:0] has disconnected
2009-11-30 18:20:32    nerdy_kid-pc    acpid    client connected from 12616[0:0]
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Stopping security manager 0
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12776.881840] PM: Syncing filesystems ... done.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12776.889882] PM: Preparing system for mem sleep
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    HCI dev 0 down
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12776.889888] Freezing user space processes ... (elapsed 0.75 seconds) done.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.643914] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.643992] PM: Entering mem sleep
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Adapter /org/bluez/1857/hci0 has been disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.644017] Suspending console(s) (use no_console_suspend to debug)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.685308] btusb_bulk_complete: hci0 urb f1a0b680 failed to resubmit (1)
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    HCI dev 0 unregistered
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.686310] btusb_bulk_complete: hci0 urb f1a0b500 failed to resubmit (1)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.687311] btusb_intr_complete: hci0 urb f1a0bc00 failed to resubmit (1)
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Unregister path: /org/bluez/1857/hci0
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.704241] sd 2:0:0:0: [sda] Synchronizing SCSI cache
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    HCI dev 0 registered
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12777.704500] sd 2:0:0:0: [sda] Stopping disk
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.509551] ACPI handle has no context!
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.509558] sdhci-pci 0000:03:01.1: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    HCI dev 0 up
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.509565] sdhci-pci 0000:03:01.1: PCI INT B disabled
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Starting security manager 0
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.509573] ACPI handle has no context!
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.544288] b44 0000:03:00.0: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.544296] ACPI handle has no context!
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.560485] wl 0000:0c:00.0: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.605754] ata_piix 0000:00:1f.2: PCI INT B disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620298] ata2: port disabled. ignoring.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620369] ata_piix 0000:00:1f.1: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620383] ehci_hcd 0000:00:1d.7: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620393] uhci_hcd 0000:00:1d.2: PCI INT C disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620402] uhci_hcd 0000:00:1d.1: PCI INT B disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620412] uhci_hcd 0000:00:1d.0: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.620448] HDA Intel 0000:00:1b.0: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636235] ehci_hcd 0000:00:1a.7: PCI INT C disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636246] uhci_hcd 0000:00:1a.1: PCI INT B disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636256] uhci_hcd 0000:00:1a.0: PCI INT A disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636346] PM: suspend devices took 0.996 seconds
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636497] ricoh-mmc: Suspending.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636507] ricoh-mmc: Controller is now re-enabled.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.636801] ehci_hcd 0000:00:1d.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.652348] ehci_hcd 0000:00:1a.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.673015] ACPI: Preparing to enter system sleep state S3
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.674953] Disabling non-boot CPUs ...
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.677163] CPU 1 is now offline
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.677166] SMP alternatives: switching to UP code
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685973] CPU0 attaching NULL sched-domain.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685978] CPU1 attaching NULL sched-domain.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685985] CPU0 attaching NULL sched-domain.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686228] CPU1 is down
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] Extended CMOS year: 2000
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] Back to C!
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] CPU0: Thermal LVT vector (0xfa) already installed
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] Extended CMOS year: 2000
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] Enabling non-boot CPUs ...
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.686278] SMP alternatives: switching to SMP code
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.694017] Booting processor 1 APIC 0x1 ip 0x6000
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] Initializing CPU#1
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] Calibrating delay using timer specific routine.. 2792.25 BogoMIPS (lpj=5584515)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] CPU: L1 I cache: 32K, L1 D cache: 32K
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] CPU: L2 cache: 2048K
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] CPU: Physical Processor ID: 0
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] CPU: Processor Core ID: 1
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] mce: CPU supports 6 MCE banks
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] CPU1: Thermal monitoring enabled (TM2)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.685807] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.785706] CPU1: Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz stepping 0d
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.785792] CPU0 attaching NULL sched-domain.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.789016] Switched to high resolution mode on CPU 1
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800022] CPU0 attaching sched-domain:
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800026]  domain 0: span 0-1 level MC
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800029]   groups: 0 1
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800035] CPU1 attaching sched-domain:
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800038]  domain 0: span 0-1 level MC
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.800041]   groups: 1 0
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.801021] CPU1 is up
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.801024] ACPI: Waking up from system sleep state S3
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809591] pcieport-driver 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809602] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809608] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809636] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809666] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809681] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809710] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809735] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x309)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809765] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900102)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809787] ehci_hcd 0000:00:1a.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809811] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809837] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809846] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809885] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809901] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809908] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809915] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809922] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809932] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.809941] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810000] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810016] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810023] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f9f0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810030] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810037] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810048] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810056] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810115] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810131] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810138] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf9e0f9c0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810145] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xc0c0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810152] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810162] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810171] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810241] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810255] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810284] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810298] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810328] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810377] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810400] ehci_hcd 0000:00:1d.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810423] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810430] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xb0, writing 0xf9b0f9b0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810437] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810452] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810510] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810531] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x107)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810576] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810605] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80007, writing 0x2b00007)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810624] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810648] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xfebfbf00)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810659] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810693] nvidia 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810705] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfea00000, writing 0x0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810716] nvidia 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xdf01)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810725] nvidia 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xfa000004)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810886] wl 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810951] wl 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf9ffc004)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810964] wl 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.810983] wl 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811060] b44 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811084] b44 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfe000)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811091] b44 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811100] b44 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811127] ohci1394 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020105)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811156] ohci1394 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811165] ohci1394 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811191] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811218] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd400)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811225] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811234] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811261] ricoh-mmc 0000:03:01.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811286] ricoh-mmc 0000:03:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd500)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811293] ricoh-mmc 0000:03:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811302] ricoh-mmc 0000:03:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811316] ricoh-mmc: Resuming.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811327] ricoh-mmc: Controller is now disabled.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811342] pci 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811369] pci 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd700)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811376] pci 0000:03:01.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.811385] pci 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878834] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878845] uhci_hcd 0000:00:1a.0: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878875] usb usb3: root hub lost power or was reset
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878898] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878932] uhci_hcd 0000:00:1a.1: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878960] usb usb4: root hub lost power or was reset
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878984] ehci_hcd 0000:00:1a.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.878990] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879000] ehci_hcd 0000:00:1a.7: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879027] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879036] HDA Intel 0000:00:1b.0: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879068] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879078] uhci_hcd 0000:00:1d.0: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879107] usb usb5: root hub lost power or was reset
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879129] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879138] uhci_hcd 0000:00:1d.1: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879166] usb usb6: root hub lost power or was reset
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879188] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879197] uhci_hcd 0000:00:1d.2: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879226] usb usb7: root hub lost power or was reset
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879249] ehci_hcd 0000:00:1d.7: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879255] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879286] ehci_hcd 0000:00:1d.7: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879302] pci 0000:00:1e.0: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879313] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879321] ata_piix 0000:00:1f.1: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.879386] ata2: port disabled. ignoring.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.880095] ata1.00: _GTF evaluation failed (AE 0x1001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.880252] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.880260] ata_piix 0000:00:1f.2: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12778.891079] ata3.00: _GTF evaluation failed (AE 0x1001)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.531149] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.531164] wl 0000:0c:00.0: setting latency timer to 64
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.548598] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.572536] ata1.00: configured for UDMA/33
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.626248] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.632268] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.633288] pci 0000:03:01.3: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.633295] pci 0000:03:01.4: PME# disabled
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.860286] ata4.00: SATA link down (SStatus 4 SControl 300)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12779.860312] ata4.01: SATA link down (SStatus 0 SControl 0)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.016315] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.016337] ata3.01: SATA link down (SStatus 4 SControl 300)
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.069929] ata3.00: configured for UDMA/133
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.328230] usb 3-2: reset full speed USB device using uhci_hcd and address 2
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.688230] sd 2:0:0:0: [sda] Starting disk
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.801309] usb 3-2.1: reset full speed USB device using uhci_hcd and address 3
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.910312] btusb 3-2.1:1.0: no reset_resume for driver btusb?
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12780.910316] btusb 3-2.1:1.1: no reset_resume for driver btusb?
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12781.233322] usb 3-2.2: reset full speed USB device using uhci_hcd and address 4
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12781.421329] usb 3-2.3: reset full speed USB device using uhci_hcd and address 5
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12781.556600] PM: resume devices took 2.732 seconds
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12781.556649] PM: Finishing wakeup.
2009-11-30 18:33:29    nerdy_kid-pc    kernel    [12781.556651] Restarting tasks ... done.
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Parsing /etc/bluetooth/serial.conf failed: No such file or directory
2009-11-30 18:33:29    nerdy_kid-pc    bluetoothd[1861]    Adapter /org/bluez/1857/hci0 has been enabled
2009-11-30 18:33:30    nerdy_kid-pc    anacron[12680]    Anacron 2.3 started on 2009-11-30
2009-11-30 18:33:30    nerdy_kid-pc    anacron[12680]    Normal exit (0 jobs run)
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  Waking up...
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): now managed
2009-11-30 18:33:30    nerdy_kid-pc    kernel    [12781.852290] ADDRCONF(NETDEV_UP): eth0: link is not ready
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): device state change: 1 -> 2 (reason 2)
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): bringing up device.
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): preparing device.
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): deactivating device (reason: 2).
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth0): now managed
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth0): device state change: 1 -> 2 (reason 2)
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth0): bringing up device.
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth0): preparing device.
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth0): deactivating device (reason: 2).
2009-11-30 18:33:30    nerdy_kid-pc    bluetoothd[1861]    Inquiry Failed with status 0x12
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): supplicant interface state:  starting -> ready
2009-11-30 18:33:30    nerdy_kid-pc    NetworkManager    <info>  (eth2): device state change: 2 -> 3 (reason 42)
2009-11-30 18:33:30    nerdy_kid-pc    wpa_supplicant[1298]    CTRL-EVENT-SCAN-RESULTS
2009-11-30 18:33:30    nerdy_kid-pc    acpid    client connected from 12616[0:0]
2009-11-30 18:33:31    nerdy_kid-pc    avahi-daemon[1072]    Registering new address record for fe80::216:44ff:fee3:8eff on eth2.*.
2009-11-30 18:33:31    nerdy_kid-pc    kdm[1044]    X server startup timeout, terminating
2009-11-30 18:33:34    nerdy_kid-pc    kdm[1044]    X server died during startup
2009-11-30 18:33:34    nerdy_kid-pc    kdm[1044]    Failed to start X server. Starting failsafe X server.
2009-11-30 18:33:40    nerdy_kid-pc    wpa_supplicant[1298]    CTRL-EVENT-SCAN-RESULTS




```

---

### Post by nerdy_kid on 2009-12-01
bump

---

### Post by nerdy_kid on 2009-12-08
directly after an X crash i found this in /var/log/kdm.log:

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Nov 14 21:55:54 2009
(EE) LD_BIND_NOW is set, dlloader will NOT work!
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0407:1028:0228 nVidia Corporation G84 [GeForce 8600M GT] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default nv Device 0"
        Driver    "nv"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default nv Screen 0"
        Device    "Builtin Default nv Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default nv Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default nv Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default nv Device 0"
(==) No monitor specified for screen "Builtin Default nv Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: DRIDestroyContext
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
dlopen: /usr/lib/xorg/modules/drivers//nv_drv.so: undefined symbol: vbeFree
(EE) Failed to load /usr/lib/xorg/modules/drivers//nv_drv.so
(II) UnloadModule: "nv"
(EE) Failed to load module "nv" (loader failed, 7)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
dlopen: /usr/lib/xorg/modules/drivers//vesa_drv.so: undefined symbol: vbeFree
(EE) Failed to load /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "vesa"
(EE) Failed to load module "vesa" (loader failed, 7)
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
dlopen: /usr/lib/xorg/modules/drivers//fbdev_drv.so: undefined symbol: shadowSetup
(EE) Failed to load /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdev"
(EE) Failed to load module "fbdev" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```



this was in /var/log/Xorg.1.log

is there any possible way that kdm might be causing this to happen?

---

### Post by nerdy_kid on 2009-12-08
please someone help; is there at least a way to force LD_BIND_NOW to 0 on resume? so instead of starting X a script would start forcing LD_BIND_NOW to equal 0 then starting X?  if this is possible where would i place such a script?

---

