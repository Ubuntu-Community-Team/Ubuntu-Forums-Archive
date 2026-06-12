---
title: "Sony Vaio VPCEA1S1E - lucid linx 10.04 slow boot"
date: 2010-06-23
forum: General Help
---

### Post by afro22 on 2010-06-23
I recently install LucidLinx to my new laptop Sony Vaio VPCEA1S1E and I was supprised that boot time is longer as my older desktop PC.
I checked the log files and here is my problem.

I extracted important lines from my dmessg (I hope that enough these lines):

1) 
[    0.977103] Freeing initrd memory: 8131k freed
[    2.924268] pci 0000:00:1a.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.923904] pci 0000:00:1d.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.924111] pci 0000:01:00.0: Boot video device

sleep aprox. 2x 2 seconds for detecting what?

Somewhere I read that this can be fixed if i switch in bios USB legacy support. But Vaio have in bios only 4 items for set. I don't know how I can unlock all bios features, or do you have any solution how I can fix that? (BIOS handoff failed (BIOS bug?))


2)
[    6.394516] usb 2-1.6: new low speed USB device using ehci_hcd and address 3
[    6.205849] usb 1-1.6: new full speed USB device using ehci_hcd and address 5
[    6.319359] usb 1-1.6: configuration #1 chosen from 1 choice
[    6.509913] usb 2-1.6: configuration #1 chosen from 1 choice
[   10.842917] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.843840] ata1.00: ACPI _SDD failed (AE 0x5)
[   10.843915] ata1.00: ACPI: failed the second time, disabled
[   10.898331] ata1.00: ATA-8: ST9500325AS, 0006SDM2, max UDMA/133
... and ...
[   10.949905] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.262842] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.264789] ata2.00: ACPI _SDD failed (AE 0x5)
[   16.611875] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.613821] ata2.00: ACPI _SDD failed (AE 0x5)

As you see: SATA link up take 2x 5seconds..

How I can speed up this 2 steps?

Together takes my problems 14seconds during boot and that is too much for lucid linx, which promise boot time up to 20sec.

Thank for help!

---

### Post by bspujari on 2010-06-25
Even my timings are very similar.. is there any solution for the delay and the BIOS bug? I did upgrade the BIOS.

---

### Post by gnamba on 2010-07-16
I have the same problem! someone have find the solution?

---

### Post by jayachandranm on 2010-07-16
I got very similar timings and errors in my boot. Followed the instructions from the link below to disable ATA ACPI Support.

[http://cateee.net/lkddb/web-lkddb/ATA_ACPI.html](http://cateee.net/lkddb/web-lkddb/ATA_ACPI.html)

Open,
> sudo vi /etc/default/grub

and edit the line as,
> GRUB_CMDLINE_LINUX_DEFAULT="libata.noacpi=1"

Then update grub,
> sudo update-grub2

That removed the 2x5secs delay for me. Left with a 9sec delay near udev start.

---

### Post by gnamba on 2010-07-17
thanks jayachandranm... your solution speed up my boot time about 10 sec.
however i hope we find with the new kernel a definitive solution

---

### Post by jayachandranm on 2010-07-17
Yes. Hope to find a solution for the udev delay as well.

---

### Post by afro22 on 2010-07-18
Work for me, too. Thanks!

---

