---
title: "Recover files from Compact Flash card? (File system might be corrupt)"
date: 2010-06-11
forum: General Help
---

### Post by lightbricko on 2010-06-11
I hope someone can help me restore the photos on my compact flash memory card. Even though the file system might be corrupt, the files are probably intact and can hopefully be restored.

Earlier, the card worked like it should both in the digital camera and in Ubuntu (using an 8-in-1 card reader). But all of a sudden after I had removed the card from the card reader it doesn't work in either the camera or Ubuntu. Maybe I removed the card from the card reader without "safely removing" it or even while a file operation was running, I don't know. I guess the file system is corrupt, but I'm not fully sure about that either.

I have another CF card too, and since that card works in the camera and in the card reader I'm quite sure the card reader etc. works fine. I've also tried the broken card in another card reader and in Windows without success.

The card reader is found but no media is detected when inserting the card. I've read about tools to recover files (such as "testdisk"), but since the media can't be detected, the tools I've found can't be used. "sudo fdisk -l" doesn't show the memory card.

In dmesg I get this when I insert the card:
```
usb 2-2.2: reset high speed USB device using ehci_hcd and address 110
usb 2-2.2: reset high speed USB device using ehci_hcd and address 110
usb 2-2.2: reset high speed USB device using ehci_hcd and address 110
usb 2-2.2: reset high speed USB device using ehci_hcd and address 110
usb 2-2.2: reset high speed USB device using ehci_hcd and address 110
sd 31:0:0:0: Device offlined - not ready after error recovery
```

In other threads I found the advice to disable USB2 in BIOS, and then I get the following in dmesg when inserting the card:
```
[  451.474713] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  467.716233] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  467.952153] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  478.188699] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  478.352645] sd 6:0:0:1: Device offlined - not ready after error recovery
[  481.136413] hald-addon-st D c08145c0     0  1290   1106 0x00000000
[  481.136418]  f406bbd8 00000086 f20f3796 c08145c0 f3a7da88 c08145c0 d39823aa 0000004f
[  481.136425]  c08145c0 c08145c0 f3a7da88 c08145c0 d398091a 0000004f c08145c0 f522aa00
[  481.136431]  f3a7d7f0 f406bc88 7fffffff f406bc8c f406bc34 c056f735 f6401358 f406bc08
[  481.136438] Call Trace:
[  481.136445]  [<c056f735>] schedule_timeout+0x185/0x200
[  481.136450]  [<c031210d>] ? kobject_put+0x1d/0x50
[  481.136455]  [<c0570e63>] ? _spin_lock_irq+0x13/0x20
[  481.136460]  [<c03b8bb3>] ? scsi_request_fn+0xc3/0x4b0
[  481.136463]  [<c056f452>] wait_for_common+0xa2/0x120
[  481.136468]  [<c013c5a0>] ? default_wake_function+0x0/0x10
[  481.136471]  [<c056f562>] wait_for_completion+0x12/0x20
[  481.136476]  [<c03066a5>] blk_execute_rq+0x75/0xd0
[  481.136479]  [<c0306560>] ? blk_end_sync_rq+0x0/0x30
[  481.136483]  [<c03031cd>] ? get_request_wait+0x1d/0x160
[  481.136487]  [<c03028bf>] ? __freed_request+0x9f/0x120
[  481.136491]  [<c030370b>] ? blk_get_request+0x5b/0x80
[  481.136494]  [<c03ba042>] scsi_execute+0xb2/0x140
[  481.136497]  [<c03ba275>] scsi_execute_req+0x85/0x140
[  481.136502]  [<c03c2670>] sd_spinup_disk+0x80/0x4f0
[  481.136506]  [<c03c4ef7>] ? sd_revalidate_disk+0x67/0x2b0
[  481.136510]  [<c03c4f22>] sd_revalidate_disk+0x92/0x2b0
[  481.136514]  [<c03c48ce>] ? sd_media_changed+0xbe/0x260
[  481.136518]  [<c0312272>] ? kobject_get+0x12/0x20
[  481.136523]  [<c020e9e0>] check_disk_change+0x50/0x60
[  481.136527]  [<c03c24bd>] sd_open+0x7d/0x1b0
[  481.136530]  [<c0312272>] ? kobject_get+0x12/0x20
[  481.136534]  [<c020faf6>] __blkdev_get+0x76/0x310
[  481.136538]  [<c0487860>] ? apparmor_file_alloc_security+0x20/0x90
[  481.136541]  [<c020fd9a>] blkdev_get+0xa/0x10
[  481.136544]  [<c020fdfe>] blkdev_open+0x5e/0xb0
[  481.136549]  [<c01e5a39>] __dentry_open+0xb9/0x230
[  481.136552]  [<c01e5c95>] nameidata_to_filp+0x55/0x70
[  481.136555]  [<c020fda0>] ? blkdev_open+0x0/0xb0
[  481.136559]  [<c01f39ea>] do_filp_open+0x53a/0x890
[  481.136564]  [<c01583fb>] ? queue_work_on+0x3b/0x60
[  481.136568]  [<c0158455>] ? queue_work+0x15/0x20
[  481.136572]  [<c01e57d0>] do_sys_open+0x50/0x150
[  481.136577]  [<c01653e1>] ? do_gettimeofday+0x11/0x40
[  481.136580]  [<c01e5939>] sys_open+0x29/0x40
[  481.136584]  [<c010336c>] syscall_call+0x7/0xb
[  481.136592] hald-addon-st D c08145c0     0  1298   1106 0x00000000
[  481.136596]  f5745df8 00000086 f406a000 c08145c0 f3a6a848 c08145c0 d2e85bbc 0000004f
[  481.136602]  c08145c0 c08145c0 f3a6a848 c08145c0 00000000 0000004f c08145c0 f52281c0
[  481.136608]  f3a6a5b0 f6ec0410 f6ec0414 ffffffff f5745e24 c056fdd6 c03082f0 f6ec0418
[  481.136614] Call Trace:
[  481.136618]  [<c056fdd6>] __mutex_lock_slowpath+0xc6/0x130
[  481.136622]  [<c03082f0>] ? exact_match+0x0/0x10
[  481.136625]  [<c056fcf0>] mutex_lock+0x20/0x40
[  481.136628]  [<c020faaf>] __blkdev_get+0x2f/0x310
[  481.136632]  [<c0487860>] ? apparmor_file_alloc_security+0x20/0x90
[  481.136635]  [<c020fd9a>] blkdev_get+0xa/0x10
[  481.136638]  [<c020fdfe>] blkdev_open+0x5e/0xb0
[  481.136641]  [<c01e5a39>] __dentry_open+0xb9/0x230
[  481.136645]  [<c01e5c95>] nameidata_to_filp+0x55/0x70
[  481.136648]  [<c020fda0>] ? blkdev_open+0x0/0xb0
[  481.136651]  [<c01f39ea>] do_filp_open+0x53a/0x890
[  481.136655]  [<c01f0765>] ? getname+0x25/0xf0
[  481.136659]  [<c01e57d0>] do_sys_open+0x50/0x150
[  481.136663]  [<c01653e1>] ? do_gettimeofday+0x11/0x40
[  481.136666]  [<c01e5939>] sys_open+0x29/0x40
[  481.136669]  [<c010336c>] syscall_call+0x7/0xb
[  481.136682] devkit-disks- D c08145c0     0  2177   2176 0x00000000
[  481.136686]  f133dbd8 00000086 c4d70b54 c08145c0 f39b2848 c08145c0 d34be066 0000004f
[  481.136692]  c08145c0 c08145c0 f39b2848 c08145c0 d34bc15e 0000004f c08145c0 f66f96c0
[  481.136698]  f39b25b0 f133dc88 7fffffff f133dc8c f133dc34 c056f735 f6400ea0 f133dc08
[  481.136704] Call Trace:
[  481.136708]  [<c056f735>] schedule_timeout+0x185/0x200
[  481.136712]  [<c031210d>] ? kobject_put+0x1d/0x50
[  481.136715]  [<c0570e63>] ? _spin_lock_irq+0x13/0x20
[  481.136719]  [<c03b8bb3>] ? scsi_request_fn+0xc3/0x4b0
[  481.136722]  [<c056f452>] wait_for_common+0xa2/0x120
[  481.136726]  [<c013c5a0>] ? default_wake_function+0x0/0x10
[  481.136729]  [<c056f562>] wait_for_completion+0x12/0x20
[  481.136733]  [<c03066a5>] blk_execute_rq+0x75/0xd0
[  481.136736]  [<c0306560>] ? blk_end_sync_rq+0x0/0x30
[  481.136739]  [<c03031cd>] ? get_request_wait+0x1d/0x160
[  481.136744]  [<c03028bf>] ? __freed_request+0x9f/0x120
[  481.136747]  [<c030370b>] ? blk_get_request+0x5b/0x80
[  481.136750]  [<c03ba042>] scsi_execute+0xb2/0x140
[  481.136753]  [<c03ba275>] scsi_execute_req+0x85/0x140
[  481.136757]  [<c03c2670>] sd_spinup_disk+0x80/0x4f0
[  481.136763]  [<c03c4ef7>] ? sd_revalidate_disk+0x67/0x2b0
[  481.136768]  [<c03c4f22>] sd_revalidate_disk+0x92/0x2b0
[  481.136773]  [<c03c48ce>] ? sd_media_changed+0xbe/0x260
[  481.136778]  [<c0312272>] ? kobject_get+0x12/0x20
[  481.136784]  [<c020e9e0>] check_disk_change+0x50/0x60
[  481.136789]  [<c03c24bd>] sd_open+0x7d/0x1b0
[  481.136794]  [<c0312272>] ? kobject_get+0x12/0x20
[  481.136799]  [<c020faf6>] __blkdev_get+0x76/0x310
[  481.136804]  [<c0487860>] ? apparmor_file_alloc_security+0x20/0x90
[  481.136809]  [<c020fd9a>] blkdev_get+0xa/0x10
[  481.136814]  [<c020fdfe>] blkdev_open+0x5e/0xb0
[  481.136819]  [<c01e5a39>] __dentry_open+0xb9/0x230
[  481.136823]  [<c01e5c95>] nameidata_to_filp+0x55/0x70
[  481.136828]  [<c020fda0>] ? blkdev_open+0x0/0xb0
[  481.136833]  [<c01f39ea>] do_filp_open+0x53a/0x890
[  481.136838]  [<c03b2350>] ? scsi_device_put+0x30/0x50
[  481.136844]  [<c03c17d5>] ? scsi_disk_put+0x35/0x40
[  481.136850]  [<c01fa4e0>] ? iput+0x20/0x60
[  481.136856]  [<c01e57d0>] do_sys_open+0x50/0x150
[  481.136862]  [<c01653e1>] ? do_gettimeofday+0x11/0x40
[  481.136867]  [<c01e5939>] sys_open+0x29/0x40
[  481.136872]  [<c010336c>] syscall_call+0x7/0xb
[  509.207229] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  519.447778] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  535.689295] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  535.929216] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  546.161761] usb 5-2.2: reset full speed USB device using uhci_hcd and address 4
[  546.326706] sd 6:0:0:2: Device offlined - not ready after error recovery

```

Additional info, just in case it's needed:
```
sudo lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 03f9:0100 KeyTronic Corp. Keyboard
Bus 005 Device 006: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 004: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 002: ID 0424:2502 Standard Microsystems Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
sudo cat /proc/scsi/usb-storage/6
   Host scsi6: usb-storage
       Vendor: SMSC
      Product: USB2223
Serial Number: 000223223223
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

```
```
sudo cat /proc/scsi/sg/device_strs 
ATA     	SAMSUNG HD501LJ 	CR10
ATA     	INTEL SSDSA2MH08	045C
TSSTcorp	CDDVDW SH-S223F 	SB03
ATA     	WDC WD20EARS-00S	80.0
SMSC    	223 U HS-CF     	3.60
SMSC    	223 U HS-MS     	3.60
SMSC    	223 U HS-SM     	3.60
SMSC    	223 U HS-SD/MMC 	3.60

```
```
ls /sys/bus/usb/devices/
1-0:1.0  2-1      3-0:1.0  5-0:1.0  5-2.1    5-2.1.1    5-2.1.1:1.0  5-2.1.2:1.0  5-2.2:1.0  7-0:1.0  usb2  usb4  usb6
2-0:1.0  2-1:1.0  4-0:1.0  5-2      5-2:1.0  5-2.1:1.0  5-2.1.2      5-2.2        6-0:1.0    usb1     usb3  usb5  usb7

```
```
ls /dev/
adsp             disk      hpet   loop7               nvidiactl  ram11  ram8    sdb1        sg0       sndstat  tty13  tty23  tty33  tty43  tty53  tty63    usbmon1  vcs4   vcsa7
audio            dsp       input  mapper              oldmem     ram12  ram9    sdb2        sg1       sr0      tty14  tty24  tty34  tty44  tty54  tty7     usbmon2  vcs5   zero
binder           dvd       kmsg   mcelog              pktcdvd    ram13  random  sdb5        sg2       stderr   tty15  tty25  tty35  tty45  tty55  tty8     usbmon3  vcs6
block            dvdrw     log    mem                 port       ram14  rfkill  sdc         sg3       stdin    tty16  tty26  tty36  tty46  tty56  tty9     usbmon4  vcs7
bus              ecryptfs  loop0  mixer               ppp        ram15  rtc     sdd         sg4       stdout   tty17  tty27  tty37  tty47  tty57  ttyS0    usbmon5  vcsa
cdrom            fd        loop1  net                 psaux      ram2   rtc0    sde         sg5       tty      tty18  tty28  tty38  tty48  tty58  ttyS1    usbmon6  vcsa1
cdrw             fd0       loop2  network_latency     ptmx       ram3   scd0    sdf         sg6       tty0     tty19  tty29  tty39  tty49  tty59  ttyS2    usbmon7  vcsa2
char             full      loop3  network_throughput  pts        ram4   sda     sdg         sg7       tty1     tty2   tty3   tty4   tty5   tty6   ttyS3    vcs      vcsa3
console          fuse      loop4  null                ram0       ram5   sda1    sequencer   shm       tty10    tty20  tty30  tty40  tty50  tty60  ttyUSB0  vcs1     vcsa4
core             hidraw0   loop5  nvidia0             ram1       ram6   sda2    sequencer2  snapshot  tty11    tty21  tty31  tty41  tty51  tty61  urandom  vcs2     vcsa5
cpu_dma_latency  hidraw1   loop6  nvidia1             ram10      ram7   sdb     serial      snd       tty12    tty22  tty32  tty42  tty52  tty62  usbmon0  vcs3     vcsa6

```

---

