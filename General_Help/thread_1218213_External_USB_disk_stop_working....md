---
title: "External USB disk stop working..."
date: 2009-07-20
forum: General Help
---

### Post by dvanzo on 2009-07-20
Hi all!

Ubuntu 9.04
Dell Vostro 1500
USB Disk 160 Gb

I´m having a serious problem with an external USB disk... In this USB disk, I have a 20Gb file (virtualbox .vdi file) than I need to copy to another PC running Ubuntu too. The copy starts normaly but suddenly it stops, the disk is unmmounted and the red led in the diskcase it's turned off. The error shows up with the disk formatted as ext3 and the same error shows with the disk formatted as ntfs.  Copying the file in a XP machine works ok.

Dmesg output:
[ 7364.828072] usb 2-1: new high speed USB device using ehci_hcd and address 8
[ 7364.964202] usb 2-1: configuration #1 chosen from 1 choice
[ 7364.965264] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7364.969731] usb-storage: device found at 8
[ 7364.969734] usb-storage: waiting for device to settle before scanning
[ 7369.968447] usb-storage: device scan complete
[ 7369.972110] scsi 8:0:0:0: Direct-Access     TOSHIBA  MK1637GSX             PQ: 0
 ANSI: 2
[ 7369.974575] sd 8:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 G
iB)
[ 7369.985002] sd 8:0:0:0: [sdb] Write Protect is off
[ 7369.985007] sd 8:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 7369.985011] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 7369.986518] sd 8:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 G
iB)
[ 7369.989637] sd 8:0:0:0: [sdb] Write Protect is off
[ 7369.989641] sd 8:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 7369.989644] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 7369.989649]  sdb: sdb1
[ 7369.997727] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 7369.997804] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 8520.100088] usb 2-1: reset high speed USB device using ehci_hcd and address 8
[ 8945.112207] usb 2-1: reset high speed USB device using ehci_hcd and address 8
[ 8960.224076] usb 2-1: device descriptor read/64, error -110
[ 8975.440080] usb 2-1: device descriptor read/64, error -110
[ 8975.656080] usb 2-1: reset high speed USB device using ehci_hcd and address 8
[ 8981.068271] usb 2-1: USB disconnect, address 8
[ 8981.077067] sd 8:0:0:0: Device offlined - not ready after error recovery
[ 8981.077097] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_
OK,SUGGEST_OK
[ 8981.077102] end_request: I/O error, dev sdb, sector 60086511
[ 8981.077107] __ratelimit: 110 callbacks suppressed
[ 8981.077111] Buffer I/O error on device sdb1, logical block 7510806
[ 8981.077118] Buffer I/O error on device sdb1, logical block 7510807
[ 8981.077122] Buffer I/O error on device sdb1, logical block 7510808
[ 8981.077126] Buffer I/O error on device sdb1, logical block 7510809
[ 8981.077129] Buffer I/O error on device sdb1, logical block 7510810
[ 8981.077133] Buffer I/O error on device sdb1, logical block 7510811
[ 8981.077136] Buffer I/O error on device sdb1, logical block 7510812
[ 8981.077139] Buffer I/O error on device sdb1, logical block 7510813
[ 8981.077143] Buffer I/O error on device sdb1, logical block 7510814
[ 8981.077146] Buffer I/O error on device sdb1, logical block 7510815
[ 8981.077173] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_
OK,SUGGEST_OK
[ 8981.077177] end_request: I/O error, dev sdb, sector 60086751

Anyone can help me??


TIA!!!


Daniel Vanzo
G. Baigorria - Argentina

---

### Post by dvanzo on 2009-07-20
Well, now I can't even mount it... Very weird... Still working Ok with XP...

Regards,

---

