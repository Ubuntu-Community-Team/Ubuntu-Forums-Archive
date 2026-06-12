---
title: "dmesg is riddled with USB messages"
date: 2010-09-04
forum: General Help
---

### Post by kakyoism on 2010-09-04
Since I installed lucid, the dmesg is full of the messages below, which I didn't see in Hardy before. I've experienced quite a few problems that may be related to USB:
[http://ubuntuforums.org/showthread.php?t=1562572](http://ubuntuforums.org/showthread.php?t=1562572)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229)
[http://ubuntuforums.org/showthread.php?t=1562593](http://ubuntuforums.org/showthread.php?t=1562593)

I seriously wonder if they all came from the same problem in USB handling.

Anyone please help. It's driving me crazy having to be ultra-careful to unmount a USB device. Never had this experience with Windows or Mac...

```
[298425.372607] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 856
[298485.369054] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 961
[298545.368046] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 858
[298605.368546] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 722
[298605.453343] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[298647.457368] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[298665.372045] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1093
[298725.372043] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1062
[298737.452822] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[298785.372032] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1060
[298785.444570] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[298811.445257] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[298845.370150] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 926
[298905.368043] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 961
[298965.368044] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1062
[298969.445369] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299025.369539] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 825
[299065.461359] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299085.369570] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 755
[299145.371792] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 858
[299205.372762] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1196
[299265.369539] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 856
[299325.372247] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 485
[299351.453258] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299373.444316] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299385.369530] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 587
[299399.445321] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299445.369540] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 587
[299505.372041] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[299565.369040] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 585
[299611.700299] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299625.369376] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[299665.477029] usb 2-1: new high speed USB device using ehci_hcd and address 25
[299665.615342] usb 2-1: configuration #1 chosen from 1 choice
[299665.616035] scsi21 : SCSI emulation for USB Mass Storage devices
[299665.616149] usb-storage: device found at 25
[299665.616153] usb-storage: waiting for device to settle before scanning
[299670.616929] usb-storage: device scan complete
[299670.619092] scsi 21:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9407 PQ: 0 ANSI: 0
[299670.619632] sd 21:0:0:0: Attached scsi generic sg13 type 0
[299671.225523] sd 21:0:0:0: [sdj] 1986560 512-byte logical blocks: (1.01 GB/970 MiB)
[299671.226650] sd 21:0:0:0: [sdj] Write Protect is off
[299671.226654] sd 21:0:0:0: [sdj] Mode Sense: 03 00 00 00
[299671.226657] sd 21:0:0:0: [sdj] Assuming drive cache: write through
[299671.229883] sd 21:0:0:0: [sdj] Assuming drive cache: write through
[299671.229890]  sdj: sdj1
[299671.233143] sd 21:0:0:0: [sdj] Assuming drive cache: write through
[299671.233148] sd 21:0:0:0: [sdj] Attached SCSI removable disk
[299685.369531] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[299745.369038] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[299749.456909] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299805.371025] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 482
[299865.369041] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 381
[299891.453254] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299907.461274] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299909.457997] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[299925.372388] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 381
[299985.369038] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 719
[300045.368541] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 585
[300105.372541] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 822
[300115.449294] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300131.457431] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300165.369487] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 823
[300225.372041] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[300227.457306] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300249.449246] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300285.372536] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[300345.368542] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 688
[300345.448624] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300405.372038] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 484
[300431.599538] usb 2-1: USB disconnect, address 25
[300465.373047] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 587
[300525.372541] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 619
[300585.372643] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1165
[300645.372542] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 959
[300705.372044] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1062
[300765.372047] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1064
[300779.445252] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300791.450003] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[300825.372044] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1196
[300885.372046] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 961
[300945.368550] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 823
[301005.369542] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1297
[301011.457302] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301025.457359] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301063.453308] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301065.372081] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 957
[301085.444860] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301101.453268] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301115.453317] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301125.372458] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1163
[301175.440323] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301185.372348] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1060
[301245.366148] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 858
[301305.372042] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1400
[301309.445282] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301343.456280] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301365.369542] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1060
[301379.445278] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301425.370257] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 957
[301485.372032] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 926
[301545.372040] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1062
[301551.444304] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301605.369540] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 927
[301665.369540] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 926
[301725.370184] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 858
[301755.461258] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301785.372037] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 824
[301823.447283] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[301833.937581] usb 2-8: USB disconnect, address 5
[301845.369043] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1062
[301905.369538] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 823
[301965.371352] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1165
[302025.371967] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1060
[302085.371879] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1027
[302145.369538] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 722
 
```

---

### Post by kakyoism on 2010-09-05
bump

---

