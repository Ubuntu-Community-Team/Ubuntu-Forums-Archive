---
title: "New user. Cant burn DVD`s. Need some help."
date: 2009-10-05
forum: General Help
---

### Post by kanagye on 2009-10-05
I`m on a Asus G1S laptop. I can burn CDR`s fine but when it came time for me to burn a DVDISO k3b spits the disk out and says write error. I`m using Maxwell DVR`s.  I`m using linux mint on the default kernel. Here is the output from my terminal. Any help would be greatly appreciated. I dont have a Windows Installation anymore but i know that my DVD burner works. My linux install is only three days old and i burnt my install disk with Nero on a DVD before installing mint. The end of the log has the errors. 

g1s-laptop g1s # k3b
Session management error: None of the authentication protocols specified are supported
g1s-laptop g1s # (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_T20L to device /dev/sr0
/dev/sr0 resolved to /dev/sr0
/dev/sr0 is block device (0)
/dev/sr0 seems to be cdrom
bus: 4, id: 0, lun: 0
(K3bDevice::Device) /dev/sr0: init()
(K3bDevice::Device) /dev/sr0 feature: CD Mastering
(K3bDevice::Device) /dev/sr0 feature: CD Track At Once
(K3bDevice::Device) /dev/sr0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/sr0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/sr0 feature: DVD+R
(K3bDevice::Device) /dev/sr0 feature: DVD+RW
(K3bDevice::Device) /dev/sr0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/sr0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/sr0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/sr0 unknown profile: 2
(K3bDevice::Device) /dev/sr0: dataLen: 60
(K3bDevice::Device) /dev/sr0: checking for TAO
(K3bDevice::Device) /dev/sr0: checking for SAO
(K3bDevice::Device) /dev/sr0: checking for SAO_R96P
(K3bDevice::Device) /dev/sr0: checking for SAO_R96R
(K3bDevice::Device) /dev/sr0: checking for RAW_R16
(K3bDevice::Device) /dev/sr0: checking for RAW_R96P
(K3bDevice::Device) /dev/sr0: checking for RAW_R96R
(K3bDevice::Device) /dev/sr0: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/sr0: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/sr0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/sr0 : 11080 KB/s
(K3bDevice::Device) /dev/sr0 : 5540 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/sr0 to 11080
/dev/sr0 resolved to /dev/sr0
(K3bDevice::DeviceManager) dev /dev/sr0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: HL-DT-ST DVDRAM GSA-T20L
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 554:28:03 (LBA 2495103) (5109970944 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 554:28:03 (LBA 2495103) (5109970944 Bytes)
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:46:46 (LBA 2298496) (4707319808 Bytes)
Remaining size:  510:46:46 (LBA 2298496) (4707319808 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/sr0: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/sr0: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/sr0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/sr0 : 11080 KB/s
(K3bDevice::Device) /dev/sr0 : 5540 KB/s
Devices:
------------------------------
Blockdevice:    /dev/sr0
Generic device: 
Vendor:         HL-DT-ST
Description:    DVDRAM GSA-T20L
Version:        NR02
Write speed:    0
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/sr0
------------------------------
Session management error: None of the authentication protocols specified are supported
QGDict::hashKeyString: Invalid null key
QGDict::hashKeyString: Invalid null key
(K3bDevice::Device) /dev/sr0: GET CONFIGURATION length det failed.
(K3bDevice::DeviceManager) request for empty device!
(K3bDevice::Device) /dev/sr0: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/sr0: GET CONFIGURATION length det failed.
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_T20L
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/g1s/.gvfs
      Output information may be incomplete.
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_T20L
removing udi /org/freedesktop/Hal/devices/volume_empty_dvd_r
Session management error: None of the authentication protocols specified are supported
ICE default IO error handler doing an exit(), pid = 5706, errno = 11
ICE default IO error handler doing an exit(), pid = 5722, errno = 11

---

### Post by kanagye on 2009-10-05
Tried a different ISO and wodim. Failed. Could it be the maxwell DVD`s?



g1s@g1s-laptop ~/usenet/WINDOWS_7_X64_OEM.rar/WINDOWS_7_X64_OEM $ sudo wodim -v dev=/dev/cdrw WINDOWS_7_X64_OEM.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-T20L '
Revision       : 'NR02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1114112 = 1088 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 14085 kB/s 80x CD 10x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data  4036 MB        
Total size:     4635 MB (459:13.92) = 2066544 sectors
Lout start:     4635 MB (459:15/69) = 2066544 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 231952
Speed set to 11080 KB/s
Starting to write CD/DVD at speed   8.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of 4036 MB written.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 32 4D 03 0C 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.941s timeout 40s

write track data: error after 0 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:   37.913s
Average write speed 111.0x.
Fixating...
Fixating time:    0.009s
wodim: fifo had 192 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
g1s@g1s-laptop ~/usenet/WINDOWS_7_X64_OEM.rar/WINDOWS_7_X64_OEM $

---

### Post by kanagye on 2009-10-05
Found a memorex DVDR laying around and burnt a DVDR no problem. Wonder whats wrong with the maxwells? I have 150 Maxwell DVD`s that i cant use.:popcorn:

---

### Post by fluffman86 on 2009-10-05
So Nero worked in Windows on the Maxwells?  The only time I've had trouble like that was when I bouth 16x DVDs and tried to use them in an old burner.  I fixed the problem by finding the manufacturer of the drive itself (Samsung, NEC, Sony...not Dell, HP, Gateway, etc.) and updating the firmware.

This shouldn't be a problem though for DVD drives made in the last 4 years.

---

### Post by scouser73 on 2009-10-05
If you're using Linux Mint then really this should be asked in the [[COLOR="Red"]**Linux Mint Forum**[/COLOR]]("http://forums.linuxmint.com/")

---

