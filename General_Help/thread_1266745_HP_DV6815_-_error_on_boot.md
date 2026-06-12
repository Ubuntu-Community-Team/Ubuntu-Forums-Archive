---
title: "HP DV6815 - error on boot"
date: 2009-09-15
forum: General Help
---

### Post by izziere on 2009-09-15
This is not a big problem, but I get untidy boot due to an error message "pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02".  Seems to be common with the HP DV6*** laptops, but I cannot understand any of the solutions...

All devices seem to work OK, but I hate getting terminal-style error messages at boot time, plus it would be good education for me as to how to fix these things.

Any ideas, please?

Thanks.

Output from relevant dmesg section:

```
[   20.261484] ACPI: bus type pci registered
[   20.282389] PCI: PCI BIOS revision 3.00 entry at 0xfde1b, last bus=9
[   20.282391] PCI: Using configuration type 1
[   20.282398] Setting up standard PCI resources
[   20.284052] ACPI: EC: Look up EC in DSDT
[   20.285630] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   20.286168] ACPI: Interpreter enabled
[   20.286170] ACPI: (supports S0 S3 S4 S5)
[   20.286180] ACPI: Using IOAPIC for interrupt routing
[   20.283436] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   20.292723] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   20.292726] ACPI: EC: driver started in interrupt mode
[   20.292782] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.293589] PCI: Transparent bridge - 0000:00:08.0
[   20.293942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.294003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   20.294027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   20.294059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   20.294088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   20.294118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[   20.314421] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *15
[   20.314602] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *10
[   20.314785] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   20.314968] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   20.315150] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[   20.315332] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   20.315514] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   20.315697] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *15
[   20.315880] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   20.316063] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   20.316245] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7
[   20.316431] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[   20.316617] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *11
[   20.316803] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   20.316986] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[   20.317173] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *0, disabled.
[   20.317319] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.317348] pnp: PnP ACPI init
[   20.317354] ACPI: bus type pnp registered
[COLOR="Red"][   20.320004] ACPI Error (dsopcode-0548): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20070126]
[   20.320010] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f7c49900), AE_AML_BUFFER_LIMIT
[   20.320049] ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f7c49900), AE_AML_BUFFER_LIMIT
[   20.320055] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02[/COLOR]
[   20.321679] pnp: PnP ACPI: found 11 devices
[   20.321681] ACPI: ACPI bus type pnp unregistered
[   20.321683] PnPBIOS: Disabled by ACPI PNP
[   20.321894] PCI: Using ACPI for IRQ routing
[   20.321896] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

```

---

