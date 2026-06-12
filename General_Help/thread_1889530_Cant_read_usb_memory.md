---
title: "Cant read usb memory"
date: 2011-12-01
forum: General Help
---

### Post by hengis on 2011-12-01
I recently increased the size of my natty partitions.  Now I cannot red usb drives which I could read before the change.  These drives can be read using Windows on the same machine.  Here is some info which may help.  I do not understand any of it

hengis@hengis-ThinkPad-R61:~$ dmesg |tail -n15
[24187.662674] usb 1-3: USB disconnect, address 7
[26521.005413] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1d:e0:4e:31:9b:00:1f:9f:42:dc:3c:08:00 SRC=199.59.149.198 DST=192.168.1.66 LEN=52 TOS=0x10 PREC=0x00 TTL=44 ID=0 DF PROTO=TCP SPT=443 DPT=48273 WINDOW=54 RES=0x00 ACK URGP=0 
[29650.049957] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1d:e0:4e:31:9b:00:1f:9f:42:dc:3c:08:00 SRC=199.59.149.230 DST=192.168.1.66 LEN=52 TOS=0x18 PREC=0x00 TTL=44 ID=0 DF PROTO=TCP SPT=443 DPT=38377 WINDOW=99 RES=0x00 ACK URGP=0 
[29710.168096] usb 1-3: new high speed USB device using ehci_hcd and address 8
[29710.349186] scsi4 : usb-storage 1-3:2.0
[29713.319911] scsi 4:0:0:0: Direct-Access     ST650211 CF               3.04 PQ: 0 ANSI: 0 CCS
[29713.321688] sd 4:0:0:0: Attached scsi generic sg2 type 0
[29713.322558] sd 4:0:0:0: [sdb] 9767520 512-byte logical blocks: (5.00 GB/4.65 GiB)
[29713.323934] sd 4:0:0:0: [sdb] Write Protect is off
[29713.323943] sd 4:0:0:0: [sdb] Mode Sense: 00 4a 00 00
[29713.323951] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[29713.328304] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[29713.419885]  sdb: sdb1
[29713.421948] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[29713.421953] sd 4:0:0:0: [sdb] Attached SCSI disk
hengis@hengis-ThinkPad-R61:~$ 

Any help would be much appreciated

---

