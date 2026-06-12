---
title: "troubleshooting ATA drive in USB external Xcraft enclosure"
date: 2011-04-02
forum: General Help
---

### Post by dragonfly41 on 2011-04-02
I'm trying to get Ubuntu to recognise an ATA disk in an external Xcraft USB enclosure connected to Dell Inspiron USB 2.0 port.

Other USB drives work fine but this particular setup is not recognised.

HITACHI Model: HTS541616J9AT00
160 GB  5400 rpm    ATA/IDE
Global Storage Technologies (Thailand) Ltd.

........................................

When I inspect the connected ATA drive on USB port using Disk Utility

I get this:

Device:        /dev/sdb
Model:       ITE TECH. INC.,? ]         .... but why isn't it named HITACHI as printed on the drve?
Capacity:    1.0 TB   (1,034,534,230,016 bytes)      .... why not 160 GB?
Connection:    USB at 480.0 MB/s
SMART Status:    Not Supported
Partitioning:    Not Partitioned


A screenshot of Disk Utility is attached.

Clearly Disk Utility is not recording the correct properties of the ATA drive.

..........................................

GParted only shows device /dev/sda (containing Vista and Ubuntu)

No external USB drive is seen in other devices.

..........................................

Reading some forum threads I ran this command
sudo lsusb

```

ubuntu@ubuntu:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 062: ID 048d:8903 Integrated Technology Express, Inc. 
Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 

```

and then this command
sudo dmesg | tail -n 20

```

ubuntu@ubuntu:~$ sudo dmesg | tail -n 20
[19449.044498] Buffer I/O error on device sdb, logical block 0
[19449.044503] Buffer I/O error on device sdb, logical block 1
[19449.044550] sd 14:0:0:0: rejecting I/O to offline device
[19449.044585] sd 14:0:0:0: rejecting I/O to offline device
[19449.044610] sd 14:0:0:0: rejecting I/O to offline device
[19449.044634] sd 14:0:0:0: rejecting I/O to offline device
[19449.044651] ldm_validate_partition_table(): Disk read failed.
[19449.044662] sd 14:0:0:0: rejecting I/O to offline device
[19449.044684] sd 14:0:0:0: rejecting I/O to offline device
[19449.044707] sd 14:0:0:0: rejecting I/O to offline device
[19449.044730] sd 14:0:0:0: rejecting I/O to offline device
[19449.044747] Dev sdb: unable to read RDB block 0
[19449.044757] sd 14:0:0:0: rejecting I/O to offline device
[19449.044779] sd 14:0:0:0: rejecting I/O to offline device
[19449.044809] sd 14:0:0:0: rejecting I/O to offline device
[19449.044830] sd 14:0:0:0: rejecting I/O to offline device
[19449.044853] sd 14:0:0:0: rejecting I/O to offline device
[19449.044876] sd 14:0:0:0: rejecting I/O to offline device
[19449.044892]  unable to read partition table
[19449.045066] sd 14:0:0:0: [sdb] Attached SCSI disk
ubuntu@ubuntu:~$

```

What else can I do to troubleshoot why this drive is not recognised .. although "attached SCSI disk" (sdb) seems to be detected.   Is this a job for testdisk?

---

