---
title: "Determine device (/dev/sd?) from SCSI Host number?"
date: 2011-06-03
forum: General Help
---

### Post by hbrednek on 2011-06-03
I need to be able to determine where a device exists in the /dev/sd? spectrum of things.  Since the device is loaded dynamically, and can change device name (/dev/sdc to /dev/sdd, for example) after a power cycle, I'm trying to find some way that I can programmatically determine this.  I can get the SCSI host by looking at /proc/scsi/scsi which contains (for example):

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Hitachi HDS72101 Rev: GKAO
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Hitachi HDS72101 Rev: GKAO
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW TS-H653N  Rev: HB02
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: CALCULEX Model: 6500 Bus A       Rev: 1.0d
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi7 Channel: 00 Id: 00 Lun: 01
  Vendor: CALCULEX Model: 6500 Bus A       Rev: 1.0d
  Type:   Direct-Access                    ANSI  SCSI revision: 02

The devices I care about are the ones marked Vendor: CALCULEX which I can programmatically detect have SCSI host 7.  So maybe the way to solve this is to find some way of determining the host property of any particular device, like /dev/sda maybe.  Any thoughts?

---

### Post by matt_symes on 2011-06-03
Hi

Can i ask what you are trying to do here ? You have given information about what you want to do but no context within which you wish to do it. I don't really understand what you mean when you say programatically. You are writing software ?

If you just need to ensure that a device always gets assigned the same device name by udev then you can just create a udev rule based on the characteristics of the device such as vendor ID and/or serial number (etc).

If your looking for something more advanced then you might get better luck with the /sys file system. That contains all the information about all the devices on all the buses the kernel and drivers have found.

As an example of the thing you can look for, you can check all the buses to see what devices are attached and the names they have been given along with a whole load of other information. There are a whole load of symlinks to cross reference the device information depending on whether you know its bus type/position or the device type (etc, etc).

As an example, this is the make of drive in my laptop for device name sda which is a block device.

```
matthew@matthew-laptop:~$ cat /sys/class/block/sda/device/model 
WDC WD3200BEVT-2
matthew@matthew-laptop:~$
```If you are writing software, i believe there are a number of libraries you can use to easy the process.

Kind regards

---

