---
title: "Resume from Suspend/Hibernate == Nautilus/Gnome-Panel messed up"
date: 2009-12-10
forum: General Help
---

### Post by drewsus on 2009-12-10
Hello! 
So, Im using 9.10 on my Acer Aspire One but have noticed this on the Dell Mini 10v. 
I have noticed that if I resume from suspend/hibernate, sometimes Nautilus and/or gnome-panel seems to be messed up.
How? Well let me try to best describe it. 
Essentially, the icon and gtk/metacity theme is not applied and is the ultra generic one (usually seen if using gksu nautilus?). Furthermore, there seem to be more audio notifications. Clicking on an item in panel makes a click sound. 

Doing 
$ killall nautilus && killall gnome-panel 
and then 
$ nautilus
Seems to fix it. 

I need to know how to fix this! 
Thanks in advance!
Drew


[edit]
I should say that I am on a fresh install atm. 
On my previous install (same OS, same system) I had used this PPA:
sudo add-apt-repository ppa:ubuntu-boot/ppa
And can't say I ever noticed this problem with that ppa.. But, I havent been able to reproduce this issue reliably either.

---

### Post by drewsus on 2009-12-10
Attached are my auth.log, kern.log and user.log. 
Maybe this will shine some light on the subject?


AUTH.LOG

```
Dec 10 10:22:40 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/pacmd
Dec 10 10:22:44 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/pacmd
Dec 10 10:22:45 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/pacmd
Dec 10 10:22:45 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/pacmd
Dec 10 10:22:45 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/pacmd
Dec 10 10:22:56 drewsus-lite gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.
Dec 10 10:22:56 drewsus-lite gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
Dec 10 10:27:32 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Dec 10 10:27:32 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Dec 10 10:27:33 drewsus-lite sudo:     root : TTY=unknown ; PWD=/ ; USER=drewsus ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Dec 10 11:17:02 drewsus-lite CRON[10911]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 10 11:17:02 drewsus-lite CRON[10911]: pam_unix(cron:session): session closed for user root
```

KERN.LOG

```
Dec 10 10:22:23 drewsus-lite kernel: [20802.275229] PM: Syncing filesystems ... done.
Dec 10 10:22:23 drewsus-lite kernel: [20802.447220] Freezing user space processes ... (elapsed 0.00 seconds) done.
Dec 10 10:22:23 drewsus-lite kernel: [20802.449247] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Dec 10 10:22:23 drewsus-lite kernel: [20802.449543] PM: Shrinking memory...  -\|/-\|/-\|done (107263 pages freed)
Dec 10 10:22:23 drewsus-lite kernel: [20812.746731] PM: Freed 429052 kbytes in 10.29 seconds (41.69 MB/s)
Dec 10 10:22:24 drewsus-lite kernel: [20812.746737] Suspending console(s) (use no_console_suspend to debug)
Dec 10 10:22:24 drewsus-lite kernel: [20812.976122] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 10 10:22:24 drewsus-lite kernel: [20812.976828] jmb38x_ms 0000:04:00.3: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20812.976843] jmb38x_ms 0000:04:00.3: PCI INT A disabled
Dec 10 10:22:24 drewsus-lite kernel: [20812.992300] sdhci-pci 0000:04:00.0: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20812.992320] sdhci-pci 0000:04:00.0: PCI INT A disabled
Dec 10 10:22:24 drewsus-lite kernel: [20813.008317] ath5k 0000:03:00.0: PCI INT A disabled
Dec 10 10:22:24 drewsus-lite kernel: [20813.024337] ata_piix 0000:00:1f.2: PCI INT B disabled
Dec 10 10:22:24 drewsus-lite kernel: [20813.024410] HDA Intel 0000:00:1b.0: PCI INT A disabled
Dec 10 10:22:24 drewsus-lite kernel: [20813.072536] ACPI: Preparing to enter system sleep state S4
Dec 10 10:22:24 drewsus-lite kernel: [20813.192136] PM: Saving platform NVS memory
Dec 10 10:22:24 drewsus-lite kernel: [20813.202717] Disabling non-boot CPUs ...
Dec 10 10:22:24 drewsus-lite kernel: [20813.205105] CPU 1 is now offline
Dec 10 10:22:24 drewsus-lite kernel: [20813.205111] SMP alternatives: switching to UP code
Dec 10 10:22:24 drewsus-lite kernel: [20813.211593] CPU0 attaching NULL sched-domain.
Dec 10 10:22:24 drewsus-lite kernel: [20813.211601] CPU1 attaching NULL sched-domain.
Dec 10 10:22:24 drewsus-lite kernel: [20813.211613] CPU0 attaching NULL sched-domain.
Dec 10 10:22:24 drewsus-lite kernel: [20813.212207] CPU1 is down
Dec 10 10:22:24 drewsus-lite kernel: [20813.212387] PM: Creating hibernation image: 
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] PM: Need to copy 125545 pages
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] PM: Normal pages needed: 113673 + 1024 + 24, available pages: 121639
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] PM: Restoring platform NVS memory
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] CPU0: Thermal LVT vector (0xfa) already installed
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] Enabling non-boot CPUs ...
Dec 10 10:22:24 drewsus-lite kernel: [20813.216017] SMP alternatives: switching to SMP code
Dec 10 10:22:24 drewsus-lite kernel: [20813.218761] Booting processor 1 APIC 0x1 ip 0x6000
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] Initializing CPU#1
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] Calibrating delay using timer specific routine.. 3191.96 BogoMIPS (lpj=6383935)
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] CPU: L2 cache: 512K
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] CPU: Physical Processor ID: 0
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] CPU: Processor Core ID: 0
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] mce: CPU supports 5 MCE banks
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] CPU1: Thermal monitoring enabled (TM1)
Dec 10 10:22:24 drewsus-lite kernel: [20813.211316] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Dec 10 10:22:24 drewsus-lite kernel: [20813.309049] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 10 10:22:24 drewsus-lite kernel: [20813.309208] CPU0 attaching NULL sched-domain.
Dec 10 10:22:24 drewsus-lite kernel: [20813.313021] Switched to high resolution mode on CPU 1
Dec 10 10:22:24 drewsus-lite kernel: [20813.324055] CPU0 attaching sched-domain:
Dec 10 10:22:24 drewsus-lite kernel: [20813.324064]  domain 0: span 0-1 level SIBLING
Dec 10 10:22:24 drewsus-lite kernel: [20813.324071]   groups: 0 1
Dec 10 10:22:24 drewsus-lite kernel: [20813.324083] CPU1 attaching sched-domain:
Dec 10 10:22:24 drewsus-lite kernel: [20813.324089]  domain 0: span 0-1 level SIBLING
Dec 10 10:22:24 drewsus-lite kernel: [20813.324095]   groups: 1 0
Dec 10 10:22:24 drewsus-lite kernel: [20813.328048] CPU1 is up
Dec 10 10:22:24 drewsus-lite kernel: [20813.328302] ACPI: Waking up from system sleep state S4
Dec 10 10:22:24 drewsus-lite kernel: [20813.946997] i915 0000:00:02.0: restoring config space at offset 0x7 (was 0x58400000, writing 0x58500000)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947011] i915 0000:00:02.0: restoring config space at offset 0x4 (was 0x58380000, writing 0x58480000)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947047] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x58300000, writing 0x58400000)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947105] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x58440004, writing 0x58540004)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947121] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947179] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x58205730, writing 0x58305730)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947646] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x58444400, writing 0x58544400)
Dec 10 10:22:24 drewsus-lite kernel: [20813.947679] ehci_hcd 0000:00:1d.7: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20813.947821] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
Dec 10 10:22:24 drewsus-lite kernel: [20813.948149] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Dec 10 10:22:24 drewsus-lite kernel: [20813.948269] sdhci-pci 0000:04:00.0: restoring config space at offset 0xc (was 0xffff8000, writing 0x0)
Dec 10 10:22:24 drewsus-lite kernel: [20813.948434] pci 0000:04:00.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
Dec 10 10:22:24 drewsus-lite kernel: [20814.620070] i915 0000:00:02.0: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20814.931992] [drm] LVDS-8: set mode  2e
Dec 10 10:22:24 drewsus-lite kernel: [20815.305525] pci 0000:00:02.1: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20815.305542] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 10 10:22:24 drewsus-lite kernel: [20815.305553] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305599] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305646] usb usb2: root hub lost power or was reset
Dec 10 10:22:24 drewsus-lite kernel: [20815.305672] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305717] usb usb3: root hub lost power or was reset
Dec 10 10:22:24 drewsus-lite kernel: [20815.305741] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305785] usb usb4: root hub lost power or was reset
Dec 10 10:22:24 drewsus-lite kernel: [20815.305810] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305854] usb usb5: root hub lost power or was reset
Dec 10 10:22:24 drewsus-lite kernel: [20815.305879] ehci_hcd 0000:00:1d.7: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20815.305887] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.305895] usb usb1: root hub lost power or was reset
Dec 10 10:22:24 drewsus-lite kernel: [20815.309804] ehci_hcd 0000:00:1d.7: debug port 1
Dec 10 10:22:24 drewsus-lite kernel: [20815.309814] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 10 10:22:24 drewsus-lite kernel: [20815.309830] pci 0000:00:1e.0: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.309849] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 10 10:22:24 drewsus-lite kernel: [20815.309858] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.309900] r8169 0000:02:00.0: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20815.309932] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 10:22:24 drewsus-lite kernel: [20815.309976] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 10 10:22:24 drewsus-lite kernel: [20815.310003] sdhci-pci 0000:04:00.0: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.310046] pci 0000:04:00.2: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20815.310065] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 10 10:22:24 drewsus-lite kernel: [20815.310080] jmb38x_ms 0000:04:00.3: setting latency timer to 64
Dec 10 10:22:24 drewsus-lite kernel: [20815.310112] pci 0000:04:00.4: PME# disabled
Dec 10 10:22:24 drewsus-lite kernel: [20815.476512] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Dec 10 10:22:24 drewsus-lite kernel: [20815.476521] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Dec 10 10:22:24 drewsus-lite kernel: [20815.492874] ata1.00: configured for UDMA/133
Dec 10 10:22:24 drewsus-lite kernel: [20815.555330] sd 0:0:0:0: [sda] Starting disk
Dec 10 10:22:24 drewsus-lite kernel: [20815.688106] usb 1-5: reset high speed USB device using ehci_hcd and address 2
Dec 10 10:22:24 drewsus-lite kernel: [20815.978159] PM: Image restored successfully.
Dec 10 10:22:24 drewsus-lite kernel: [20816.056434] Restarting tasks ... done.
Dec 10 10:22:24 drewsus-lite kernel: [20816.062138] PM: Basic memory bitmaps freed
Dec 10 10:22:34 drewsus-lite kernel: [20828.691149] r8169: eth0: link down
Dec 10 10:22:34 drewsus-lite kernel: [20828.691994] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 10 10:22:34 drewsus-lite kernel: [20828.738139] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 10 10:22:40 drewsus-lite kernel: [20834.747317] wlan0: authenticate with AP 00:21:7c:e9:99:21
Dec 10 10:22:40 drewsus-lite kernel: [20834.748993] wlan0: authenticated
Dec 10 10:22:40 drewsus-lite kernel: [20834.749050] wlan0: associate with AP 00:21:7c:e9:99:21
Dec 10 10:22:40 drewsus-lite kernel: [20834.750643] wlan0: RX AssocResp from 00:21:7c:e9:99:21 (capab=0x431 status=0 aid=2)
Dec 10 10:22:40 drewsus-lite kernel: [20834.750654] wlan0: associated
Dec 10 10:22:40 drewsus-lite kernel: [20834.752692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 10 10:22:47 drewsus-lite kernel: [20842.287876] CPU0 attaching NULL sched-domain.
Dec 10 10:22:47 drewsus-lite kernel: [20842.287893] CPU1 attaching NULL sched-domain.
Dec 10 10:22:48 drewsus-lite kernel: [20842.301186] CPU0 attaching sched-domain:
Dec 10 10:22:48 drewsus-lite kernel: [20842.301198]  domain 0: span 0-1 level SIBLING
Dec 10 10:22:48 drewsus-lite kernel: [20842.301206]   groups: 0 1
Dec 10 10:22:48 drewsus-lite kernel: [20842.301221] CPU1 attaching sched-domain:
Dec 10 10:22:48 drewsus-lite kernel: [20842.301228]  domain 0: span 0-1 level SIBLING
Dec 10 10:22:48 drewsus-lite kernel: [20842.301236]   groups: 1 0
Dec 10 10:22:50 drewsus-lite kernel: [20845.168196] wlan0: no IPv6 routers present
Dec 10 10:35:07 drewsus-lite kernel: [21581.672121] ACPI: EC: missing confirmations, switch off interrupt mode.
Dec 10 11:19:16 drewsus-lite kernel: [24230.884797] i2c-adapter i2c-0: unable to read EDID block.
Dec 10 11:19:16 drewsus-lite kernel: [24230.884818] i915 0000:00:02.0: VGA-1: no EDID data
Dec 10 11:19:17 drewsus-lite kernel: [24231.280863] i2c-adapter i2c-0: unable to read EDID block.
Dec 10 11:19:17 drewsus-lite kernel: [24231.280889] i915 0000:00:02.0: VGA-1: no EDID data
Dec 10 11:19:17 drewsus-lite kernel: [24231.721128] [drm] DAC-6: set mode  31
```

USER.LOG

```
Dec 10 10:22:50 drewsus-lite pulseaudio[1510]: ratelimit.c: 36 events suppressed
Dec 10 10:22:56 drewsus-lite gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec 10 10:22:56 drewsus-lite gnome-screensaver-dialog: pam_sm_authenticate: username = [drewsus]
```

---

### Post by drewsus on 2009-12-10
the above logs are on the resume.

---

### Post by drewsus on 2009-12-13
bump

Please, anyone?

---

