---
title: "Can't Suspend or Hibernate - Some Devices failed to suspend"
date: 2009-10-19
forum: General Help
---

### Post by feizex on 2009-10-19
Hi Guys,

I can't get my PC to Suspend or Hibernate because some devices failed to suspend.

Below is an extract of the error... and a pic.

Is there something I can do to rectify this? Is there something I can do to make the device comply?

Thanks,
Feizex.
 
**Error Extract:**
ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
... Emask 0x1 (device error)
ata4.00: status: { DRDY ERR }
ata4.00: error: { ABRT }
suspend_device(): scsi_bus_suspend*0x0/0x70 returns 134217730
PM: Device 3:0:0:0 failed to suspend: error 134217730
PM: Some Devices failed to suspend

[IMG]http://home.exetel.com.au/feizex/some%20devices%20failed%20to%20suspend.jpg[/IMG]

---

### Post by P4man on 2009-10-19
run ```
lspci
``` and find out which device it is. On my machine 3:0:0:0  is my videocard. Assuming its the same on yours, which videocard and drivers are you using ?

**edit** scratch that. its your ata controller.
YOu could try what this guy did:
[http://bbs.archlinux.org/viewtopic.php?id=77718](http://bbs.archlinux.org/viewtopic.php?id=77718)

add "pci=msi" to your kernel options.

---

### Post by feizex on 2009-10-19
> add "pci=msi" to your kernel options. 

I don't know how to do that. I googled a bit and looks like I'd need to re-compile kernel. Is that right?

Thanks,
Feizex.

PS. yes it is my disk...

*-disk
                description: ATA Disk
                product: ST340810A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 3.39
                serial: 3FB32GGA
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a002a002

---

### Post by P4man on 2009-10-19
> **feizex said:**
> > add "pci=msi" to your kernel options. 

I don't know how to do that. I googled a bit and looks like I'd need to re-compile kernel. Is that right?

No, you just have to add it to you kernel parameters. Have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

first section explains how to test a kernel parameter for one boot. Should it work, read the next paragraph to make it permanent

---

### Post by feizex on 2009-10-20
Hi,

I tried pci=msi, but it appears that my kernel does not recognise this option. It gave me a warning message on bootup.

Does 2.6.15 have support for pci=msi?

Thanks,
Feizex.

---

### Post by P4man on 2009-10-21
hmm you're right. that boot option doesnt exist.
Not sure what to do next. Check for a new bios? See if in the bios there is anything useful to change about the (s)ata controller. Or try these boot options:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

(you can ignore the first three I think)

---

