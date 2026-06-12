---
title: "Find optical drive hardware labels?"
date: 2009-08-14
forum: General Help
---

### Post by soapBAR2 on 2009-08-14
I'll ask in the general help section since this doesn't seem to fit anywhere else..

_**Preamble**_: I'm writing a script that needs to get the hardware label of the optical drive, as part of a larger project. I'm aware that there's any number of tools that could tell me what I need to know, but part of the project's goal is to have a very small footprint (and why bother with another tool when they're probably just getting the information from somewhere in /proc? It's linux, I can do it myself ;)). So, after a length of time poking around in /proc/ and on google, I've discovered that /proc/scsi/scsi seems to hold all of the information I need, but only on the few linux machines I've tested it on. I've also found the information in dmesg, but don't want to spend a lot of time writing a reliable data scraping function for potentially stale information. Now, the obvious problem here is that /proc/scsi/scsi will only contain scsi devices (or what the kernel THINKS are scsi devices), and I want to be assured that there's no chance of an ATA device existing but not being reported (because I asked about SCSI drives):

My question is - are there any CD/DVD/optical drives or connections that will NOT report themselves in /proc/scsi/scsi? Does the linux kernel treat every SATA/ATA drive as SCSI? *Or*, does anyone know where I can get the optical drives' label in such a way that I can be assured that it will work on any linux machine - ie, hardware + distro + WM + optical drive mount location + kernel + setup agnostic (within reason) ?

PS. I'm using python. If you know of any libraries that will handle this, I'd also appreciate - but I'm fairly sure they don't exist - at least as far as Google is concerned.

--------

**_EASY MODE_**: If you don't have an answer, but still want to help me out, please post the output of:

```
cat /proc/scsi/scsi
```

PLUS the number of CD/DVD drives you currently have on your computer, and I'd be grateful. Here's mine, so you know what to expect and what I mean:

> ```
$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD360ADFD-00 Rev: 20.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD360ADFD-00 Rev: 21.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4167B Rev: DL12
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```

**I have 1 DVD drive**


Thankyou

---

### Post by 3rdalbum on 2009-08-14
Why not use HAL?

```
hal-find-by-capability --capability storage.cdrom
```

Should list the UDI numbers of all your CD-ROM-capable drives. Then you can put each UDI into this command:

```
hal-get-property --udi <your_udi> --key storage.model
```

You can be sure that all reported devices are optical drives. You can also use the hal-get-property command to discover what capabilities the drive has.

I think HAL ships with every distribution nowadays.

---

### Post by soapBAR2 on 2009-08-14
> **3rdalbum said:**
> Why not use HAL?

```
hal-find-by-capability --capability storage.cdrom
```

Should list the UDI numbers of all your CD-ROM-capable drives. Then you can put each UDI into this command:

```
hal-get-property --udi <your_udi> --key storage.model
```

You can be sure that all reported devices are optical drives. You can also use the hal-get-property command to discover what capabilities the drive has.

I think HAL ships with every distribution nowadays.

Thanks for that!

---

### Post by neurophyre on 2010-01-09
Out of curiosity, is hal actually polling the hardware for this data or polling some monstrous database of potentially fallible information?  I'm trying to write a piece of software that needs to determine the DVD+R capabilities of optical drives and stumbled across this helpful thread in researching.  I'd feel best if hal were polling the hardware but I can't seem to find a lot of information on how it actually works.

---

