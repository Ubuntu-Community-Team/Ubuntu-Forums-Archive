---
title: "newbie with non-newbie problem"
date: 2006-04-25
forum: General Help
---

### Post by jsnipe on 2006-04-25
[c]
After many false starts (and attempts with different distros) I was able to get Kubuntu up and running. I was having major problems, all centered around my SATA drive (maxtor 6Y250MO 251 GB).  So I installed an old 8 GB drive, and ran the install with complete out of box success!  
Now for the hard issue:  How do I go about getting linux to access my SATA drive?  The drive is easily accessed in windows (after a lengthy education in partition restoration), so I know it is possible, yet an install attempt with FC5 yielded similar results to Kubuntu.  Can someone help me figure out what I am missing?  Here are the facts:

1.  On first attempt to install kubuntu it properly recognized my drive and its (one 50 GB) partition.  However, it locked up while creating new partitions (35 min) and required a hard reset (CTRL-ALT-DEL did not work, nor did console switching (?? whatever it is when you switch between Fx keys)
2. Partition Table Doctor was able to locate and reinstall the old partition, but found no linux info whatsoever.
3.  Windows 98se runs fine on this drive, with no hang ups (other than I can only have 4 SATA/PATA devices at once).
4.  I consistently receive this error whenever anything tries to access this drive:

04/24/2006 09:48:44 PM	localhost	kernel	[4305115.378000] 

SCSI error : <0 0 0 0> return code = 0x8000002
sda: Current: sense key: Hardware Error
Additional sense: No additional sense information
ata1: status=0x25 { DeviceFault CorrectedError Error }
ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0


This is my (relevant) hardware:
Host scsi0  Channel: 00 Ld: 00 Lun: 00
Vendor:ATA   Model: Maxtor 6Y250M0   Rev:YAR5
Type Direct-Access      ANSI SCSI revision: 05

0000:00:1f.2 IDE interface: Intel Corp. 802801eb (ich5) Serial ATA 150 Storage Controller (rev 02) (prog -if 8f [Master SecP SecO PriP PriO])
Subsystem: Micro-Star International Co., Ltd: Unknown device 0080
Flags: Bus master 66MHz, Medium devdel, latency 0, IRQ 18
I/O ports at ec00 [size=8]
I/O ports at e800 [size=4]
I/O ports at e400 [size=8]
I/O ports at e000 [size=4]
I/O ports at dc00 [size=16]

and the motherboard is a:
Micro-Star International Co., Ltd: 865PE Neo2 (ms-6728)
(with the latest bios)

One final thought:  I noticed something odd when I was rebuilding my partition tables and restoring my MBR.  Cylinder 0 head 1 sector 4 through cylinder 0 head 1 sector 7 are always come back with access errors.  It appears that they are damaged or otherwise unreadable.  I know the MBR has to lie on CHS 0|1|1, is it possible that a linux MBR would be bigger, or differently located?  I have never had a problem with any other sectors, I assumed that CHS 0|1|4 through CHS 0|1|7 were either unused or possible an are for the head to park.  Could these three lousy sectors prevent linux from accessing this drive? Seems hard to believe.

Well I think that's everything, please let me know if I can provide any other information,  I am desperate to solve this.

---

### Post by ltmon on 2006-04-25
I checked the wiki, but unfortunately there's only a German language version of the SATA howto.

In case you can understand German, or have someone to translate it's at: [https://wiki.kubuntu.org/GermanSATAHowto](https://wiki.kubuntu.org/GermanSATAHowto)

---

### Post by oolunchbox on 2006-04-25
I had a [similar problem]("http://ubuntuforums.org/showthread.php?t=154352").  I basically had to completely format my drives to get them mounted.  As far as installing to the SATA drive, Kubuntu worked out of the box so you may have a compatibility issue with your SATA controller.  For some reason the first time I tried installing Kubuntu onto my SATA drive it didn't want to work.  I downloaded a copy of Dapper (flight 5) and it worked flawlessly but [Automatix]("http://ubuntuforums.org/showthread.php?t=138405") did not.  I went back to Breezy and it worked without a hitch.  I don't know if Dapper [flight 6]("http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/") is more stable or not, as I haven't tried it, but you may want to give it a whirl.

---

### Post by oolunchbox on 2006-04-25
oops, double post. Sorry.

---

### Post by jsnipe on 2006-04-25
not quite a similar problem.  fdisk (and sudo fdisk) return no information for /dev/sda.  However I just found out hdparm can read the geometry, and offers a sector count and starting point.  I'm going to man more about this and see what I can find.

---

### Post by jsnipe on 2006-04-25
I'm afraid google murders this in translation, unfortunately. Although the bit that read "the same you cant drive the car the driving school" was classic.  Would love some help on a translation, or just the gist of it?

---

