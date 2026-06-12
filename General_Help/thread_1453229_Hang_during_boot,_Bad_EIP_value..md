---
title: "Hang during boot, Bad EIP value."
date: 2010-04-13
forum: General Help
---

### Post by vyszard on 2010-04-13
I am using Gigabyte M912M Netbook with Ubuntu Netbook Edition 10.04.
I was doing upgrade earlier, and after I restarted, my netbook always hangs during boot.
The screen shows this:

```

[FONT=Courier New][   0.857044]   [<c0402a26>] ? scsi_probe_and_add_lun+0x196/0x470
[   0.857044]   [<c034bba2>] ? kobject_get+0x12/0x20
[   0.857044]   [<c0403bc9>] ? __scsi_add_device+0xd9/0xe0
[   0.857044]   [<c041d957>] ? ata_scsi_scan_host+0xa7/0x190
[   0.857044]   [<c041ba3d>] ? async_port_probe+0x9d/0xd0
[   0.857044]   [<c016e59a>] ? run_one_entry+0x6a/0x190
[   0.857044]   [<c016e715>] ? async_thread+0x55/0xd0
[   0.857044]   [<c0142b80>] ? default_wake_function+0x0/0x20
[   0.857044]   [<c016e6c0>] ? async_thread+0x0/0xd0
[   0.857044]   [<c01674b4>] ? kthread+0x74/0x80
[   0.857044]   [<c0167440>] ? kthread+0x0/0x80
[   0.857044]   [<c0104087>] ? kernel_thread_helper+0x7/0x10
[   0.857044] Code: Bad EIP value.
[   0.857044] EIP: [<00000fc0>] 0xfc0 SS:ESP 0068:f70bfc80
[   0.857044] CR2: 0000000000000fc0
[   0.857044] ---[ end trace 387a52e8c45056c5 ]---
[   0.864896] sd 2:0:0:0: [sda] Attached SCSI disk
[   0.992197] usb 1-4: new high speed USB device using ehci_hcd and address 2
[   1.125152] usb 1-4: configuration #1 chosen from 1 choice
[   1.125467] hub 1-4:1.0: USB hub found
[   1.125710] hub 1-4:1.0: 4 ports detected
[   1.236125] usb 1-5: new high speed USB device using ehci_hcd and address 3
[   1.380096] usb 1-5: configuration #1 chosen from 1 choice
[   1.496137] usb 1-8: new high speed USB device using ehci_hcd and address 4
_[/FONT] 

```It doesn't respond to anything I do. So I tried to boot with Ubuntu 10.04 Live USB, the only one I have, and it shows this:

```

[FONT=Courier New]Boot error
_
[/FONT]
```And if I press anything on the keyboard it then shows similar screen like above or sometimes this:

```

[FONT=Courier New][   0.647791]  [<c057f3fc>] piix_init_one|0x352/0x365
[   0.647858]  [<c025f049>] ? sysfs_find_dirent+0x29/0x40
[   0.647925]  [<c025fcf4>] ? __sysfs_add_one+0x24/0xc0
[   0.647994]  [<c0363723>] local_pci_probe+0x13/0x20
[   0.648079]  [<c0364528>] pci_device_probe+0x68/0x90
[   0.648147]  [<c03e66dd>] really_probe+0x4d/0x140
[   0.648214]  [<c03ecfee>] ? pm_runtime_barrier+0x4e/0xc0
[   0.648282]  [<c03e680c>] driver_probe_device+0x3c/0x60
[   0.648350]  [<c03e68b1>] __driver_attach+0x81/0x90
[   0.648416]  [<c03e5cf3>] bus_for_each_dev+0x53/0x80
[   0.648483]  [<c03e65ae>] driver_attach+0x1e/0x20
[   0.648549]  [<c03e6830>] ? __driver_attach+0x0/0x90
[   0.648616]  [<c03e5f75>] bus_add_driver+0xd5/0x280
[   0.648682]  [<c0364460>] ? pci_device_remove+0x0/0x40
[   0.648749]  [<c03e6baa>] driver_register+0x6a/0x130
[   0.648817]  [<c0251c15>] ? proc_create_data+0x65/0xb0
[   0.648883]  [<c0364765>] __pci_register_driver+0x45/0xb0
[   0.648952]  [<c07cf58f>] piix_init+0x14/0x24
[   0.649021]  [<c0101131>] do_one_initcall+0x31/0x190
[   0.649089]  [<c07cf57b>] ? piix_init+0x0/0x24
[   0.649154]  [<c07a32f8>] do_basic_setup+0x47/0x57
[   0.649220]  [<c07a3376>] kernel_init+0x6e/0xbf
[   0.649285]  [<c07a3308>] ? kernel_init+0x0/0xbf
[   0.649350]  [<c0104087>] kernel_thread_helper+0x7/0x10
_
[/FONT]
```What should I do? :(

---

### Post by Kanedagr on 2010-06-27
The same problem here on an HP 2133. It displays that: [<C0104087>]kernel_thread_helper+0x7/0x10
and then it freezes. Any suggestions?

---

