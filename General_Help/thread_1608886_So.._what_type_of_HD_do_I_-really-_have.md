---
title: "So.. what type of HD do I -really- have??"
date: 2010-10-29
forum: General Help
---

### Post by oxf on 2010-10-29
Well the Hard drive in my laptop is failing. Everything backed up and about to order a new one. Ha ha I can't even find a 40GB any more either.

Anyway I always thought it was SATA. My Linux partition is /dev/sda2. But when I take the drive out the lable on it says "Enhanced IDE Drive"  So what do I really have????? 

 fdisk -l

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1645    13213431    7  HPFS/NTFS
/dev/sda2            1646        3599    15687680   83  Linux
/dev/sda3            4816        4864      393592+  82  Linux swap / Solaris

```lshw -C disk

 ```
*-disk                  
       description: ATA Disk
       product: WDC WD400UE-22HC
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 09.0
       serial: WD-WXE905127915
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=94e494e4

```

---

### Post by Barajqial on 2010-10-29
What type of connection is it.  A l bar with lots of pins/ or a smallish cable with pins on the bottom similar to a USB cable(well kinda anyways).  If all else fails kindly provide the make and model of your laptop.

---

### Post by endotherm on 2010-10-29
if it helps, laptop sata connectors look just like desktop ones. just make sure your drive doesn;t have an adapter stuck to it. the first laptop hdd I looked at had this funny bus that I could never match up to a picture. it turns out that what I was seeing was one side of a removable adapter, and once I had taken it off, it was just standard sata underneath.

ps: according to this, you have an EIDE hdd: [http://www.superwarehouse.com/Western_Digital_40GB_Hard_Drive/WD400UE/ps/459790](http://www.superwarehouse.com/Western_Digital_40GB_Hard_Drive/WD400UE/ps/459790)

btw, ubuntu started calling all internal hdds "sdX" regardless of bus type, somewhere around feisty faun. I recall that it was a bit of a controversy when I first started ubuntuing.

---

### Post by uRock on 2010-10-29
Does it have a SAT cable ? [http://www.sierra-cables.com/Cables/Copper/SATA.aspx](http://www.sierra-cables.com/Cables/Copper/SATA.aspx)

Does it have a PATA cable? [http://www.tomshardware.com/reviews/pc-interfaces-101,1177-15.html](http://www.tomshardware.com/reviews/pc-interfaces-101,1177-15.html)

**IDE ** Also known as integrated drive electronics. A PC
specification for small- to medium-sized hard drives in which the controlling
electronics for the drive are part of the drive itself, speeding up transfer rates and
leaving only a simple adapter (or “paddle”). IDE only supported two drives per
system of no more than 504 megabytes each, and has been completely supplanted
by Enhanced IDE. EIDE supports four drives of over 8 gigabytes each and more
than doubles the transfer rate. The more common name for PATA drives. (See
PATA.)

---

### Post by oxf on 2010-10-29
> **Barajqial said:**
> What type of connection is it.  A l bar with lots of pins/ or a smallish cable with pins on the bottom similar to a USB cable(well kinda anyways).  If all else fails kindly provide the make and model of your laptop.

Thanks all...

Uhm it has the bar with lots of pins. two levels of them one above the other. The whole drive just slots right into the bank. It does not have a cable.

The drive itself is a WD400 Scorpio which seems to be SATA. I googled the "drive parameters #" which is printed on the drive sticker (LBA 78140160) and found a photo of a WD 40 GB drive with that number on it which clearly said SATA. But my sticker says E IDE   

The laptop is a Compaq Presario M2000 series. Specifically M2350EA. However, I've been unable to locate it on the Compaq UK site presumably as it's discontinued.

So all in all I was confused..

---

### Post by sisco311 on 2010-10-29
The [libATA]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce") subsystem uses the sd* naming convention for both PATA and SATA disks. Ubuntu uses libATA since 7.04 (linux kernel 2.6.20). ;)

---

