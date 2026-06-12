---
title: "external HDD not load (NTFS Filesystem) - HELP"
date: 2010-11-23
forum: General Help
---

### Post by alz3abi on 2010-11-23
Hello evey body.. 


i have an one terabyte HDD as NTFS File system, my life on it .. now not shown  :( 

```
alz3abi@Hz:~$ lsusb
Bus 002 Device 004: ID 1d57:000d  
[COLOR="Blue"]Bus 002 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
[/COLOR]Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

any help please,i gonna kill myself if not working 

PLEASEEEEEEEEEEEEEE

---

### Post by alz3abi on 2010-11-23
```
root@Hz:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe56e3d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13068   104857600    7  HPFS/NTFS
/dev/sda3           13068       26122   104856577    5  Extended
/dev/sda4           26122       60802   278566912    7  HPFS/NTFS
/dev/sda5           13068       26122   104856576   83  Linux

```

```
root@Hz:~# ls /dev/sdb
/dev/sdb

```

```
root@Hz:~# mkdir /media/sdb
root@Hz:~# mount -t ntfs-3g /dev/sdb /media/sdb
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

---

### Post by Verbeck on 2010-11-23
edited out

doesn't look like its detected. have you tried with another cable?

---

### Post by alz3abi on 2010-11-23
> **Verbeck said:**
> edited out


```
root@Hz:~# sudo blkid -c /dev/null
/dev/sda1: LABEL="System Reserved" UUID="10026B33026B1D4A" TYPE="ntfs" 
/dev/sda2: UUID="1AF68F4DF68F27D9" TYPE="ntfs" 
/dev/sda4: LABEL="Storage" UUID="32DE1B56DE1B1229" TYPE="ntfs" 
/dev/sda5: UUID="60353bd3-32ec-4a06-8a84-d47b25a8fce2" TYPE="ext4"
```

---

### Post by alz3abi on 2010-11-23
yes,but still same :(

---

### Post by alz3abi on 2010-11-23
Heeeeeeeeeeeeelllllllllllllllllllllppppppppppp

---

