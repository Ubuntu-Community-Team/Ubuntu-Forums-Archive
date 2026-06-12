---
title: "Prevent automount of USB external drive on boot"
date: 2012-09-26
forum: General Help
---

### Post by shreepads on 2012-09-26
The situation I have is that I have an external WD MyBook USB 3.0 drive which I want to use for creating backups using rsync.

So I don't want this to be mounted at boot or by any user, but only when my backup script runs: mount, do rsync and unmount (the script is [here]("http://ubuntuforums.org/showpost.php?p=12261308&postcount=18")).

So I have configured this in /etc/fstab as follows:

```
UUID=<insert UUID>	/media/WDMyBook	ext4	noauto,nodev,noatime,noexec,nosuid,rw,nouser	0	2
```

The issue seems to be that despite the 'noauto' option, just because it is a USB drive the boot process tries to mount it anyway and fails to do so (because of noauto & nouser presumably), generating several warnings (see further below).

The same thing happens if it is plugged in/ powered on AFTER the system has booted up: it tries to automount and fails with a 'only root can mount' error.

How can I disable this USB automount business, but ONLY for this drive and not for the other USB pendrives etc (for those I want std automount).

Not a major issue, after the system has started up, the USB drive is recognised and mounts properly either from command line or from the backup script and works fine.

Bootup warnings:

```

$ dmesg | grep -i xhci
[    9.445195] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.445242] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    9.445246] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    9.445310] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 9
[    9.450733] xhci_hcd 0000:06:00.0: irq 16, io mem 0xe3200000
[    9.454149] xHCI xhci_add_endpoint called for root hub
[    9.454151] xHCI xhci_check_bandwidth called for root hub
[    9.941406] usb 9-1: new SuperSpeed USB device using xhci_hcd and address 2
[    9.964364] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[    9.964735] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[    9.965100] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[    9.965476] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[    9.968224] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[    9.968599] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   10.130867] usb 9-2: new SuperSpeed USB device using xhci_hcd and address 3
[   10.142959] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   10.143332] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   10.143707] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   10.144082] xhci_hcd 0000:06:00.0: WARN: short transfer on control ep
[   15.394753] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.396517] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.819466] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.899038] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.900770] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.902453] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.904478] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.906142] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.907433] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
[   15.909052] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint

```

and 

```
$ dmesg | grep -i sde
[   15.394303] sd 8:0:0:0: [sde] 3906963456 512-byte logical blocks: (2.00 TB/1.81 TiB)
[   15.395895] sd 8:0:0:0: [sde] Write Protect is off
[   15.395898] sd 8:0:0:0: [sde] Mode Sense: 47 00 10 08
[   15.395899] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   15.398305] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   15.398490]  sde: sde1
[   15.820497] sd 8:0:0:0: [sde] Assuming drive cache: write through
[   15.820683] sd 8:0:0:0: [sde] Attached SCSI disk

```

---

### Post by shreepads on 2012-09-27
Anyone???
:(

---

