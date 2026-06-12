---
title: "Unmounting one USB device screws up the rest"
date: 2009-07-06
forum: General Help
---

### Post by EReckase on 2009-07-06
I have a music server that has 4 500 gb drives attached.  Two of the drives are internal SATA drives, the other two are external USB drives. fstab:

```
LABEL=Music1	/media/Music1	ext3	defaults	0	2
LABEL=Music2	/media/Music2	ext3	defaults	0	2
/dev/sdb1	/media/Music3	ext3	defaults	0	2
/dev/sdc1	/media/Music4	ext3	defaults	0	2
```

When I plug other storage into the USB hub that I'm using (it has 3 ports), everything is fine until I unmount that new storage (whether it be a hard drive or an mp3 player).  Unmounting the storage disconnects one or both of the other two external hard drives, instantaneously, and requiring a drive check because those drives weren't umounted cleanly.

Here's the relevant part of my syslog.  This starts when I plug in my Sansa Clip...note that it appears that other stuff is disconnected first.  I plugged in the Sansa Clip at 18:56:03, and copied some music onto it.  When I umount the Clip at 18:58:05, why does the other drive disconnect at 19:00:05?  

This is a 64-bit Hardy machine.

```
Jul  5 18:56:03 f64 kernel: [ 8172.821546] usb 2-3: USB disconnect, address 2
Jul  5 18:56:03 f64 kernel: [ 8172.821552] usb 2-3.2: USB disconnect, address 3
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.315731] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:56:03 f64 kernel: [ 8172.867717] usb 2-3.3: USB disconnect, address 4
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.378982] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_758f20a7_95de_45e6_9c26_65f5322d030e'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.429812] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_6400AAK_External_574341535932383836353731_0_0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.441816] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.441882] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.461019] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.465943] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.470091] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.474688] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_ec6e1434_6937_4eb0_a746_28fbebb16449'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.497595] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_5000AAKB_Externa_57442D574341505732363736383238_0_0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.500045] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.501241] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.503420] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.534833] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.538509] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_606_noserial_if0'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.541602] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_606_noserial'). 
Jul  5 18:56:03 f64 kernel: [ 8173.184444] usb 2-3: new high speed USB device using ehci_hcd and address 5
Jul  5 18:56:03 f64 kernel: [ 8173.317808] usb 2-3: configuration #1 chosen from 1 choice
Jul  5 18:56:03 f64 kernel: [ 8173.318138] hub 2-3:1.0: USB hub found
Jul  5 18:56:03 f64 kernel: [ 8173.318491] hub 2-3:1.0: 4 ports detected
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.806791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_606_noserial'). 
Jul  5 18:56:03 f64 NetworkManager: <debug> [1246841763.862387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jul  5 18:56:04 f64 kernel: [ 8173.619828] usb 2-3.2: new high speed USB device using ehci_hcd and address 6
Jul  5 18:56:04 f64 kernel: [ 8173.712858] usb 2-3.2: configuration #1 chosen from 1 choice
Jul  5 18:56:04 f64 NetworkManager: <debug> [1246841764.202558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731'). 
Jul  5 18:56:04 f64 kernel: [ 8173.719883] scsi10 : SCSI emulation for USB Mass Storage devices
Jul  5 18:56:04 f64 kernel: [ 8173.720972] usb-storage: device found at 6
Jul  5 18:56:04 f64 kernel: [ 8173.720977] usb-storage: waiting for device to settle before scanning
Jul  5 18:56:04 f64 NetworkManager: <debug> [1246841764.259074] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0'). 
Jul  5 18:56:04 f64 kernel: [ 8173.923650] usb 2-3.3: new high speed USB device using ehci_hcd and address 7
Jul  5 18:56:04 f64 kernel: [ 8174.019305] usb 2-3.3: configuration #1 chosen from 1 choice
Jul  5 18:56:04 f64 kernel: [ 8174.019613] scsi11 : SCSI emulation for USB Mass Storage devices
Jul  5 18:56:04 f64 kernel: [ 8174.019817] usb-storage: device found at 7
Jul  5 18:56:04 f64 kernel: [ 8174.019820] usb-storage: waiting for device to settle before scanning
Jul  5 18:56:04 f64 NetworkManager: <debug> [1246841764.510710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238'). 
Jul  5 18:56:04 f64 NetworkManager: <debug> [1246841764.556384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0'). 
Jul  5 18:56:09 f64 kernel: [ 8178.710095] usb-storage: device scan complete
Jul  5 18:56:09 f64 kernel: [ 8178.712034] scsi 10:0:0:0: Direct-Access     WD       6400AAK External 1.05 PQ: 0 ANSI: 4
Jul  5 18:56:09 f64 kernel: [ 8178.720022] sd 10:0:0:0: [sdf] 1250263728 512-byte hardware sectors (640135 MB)
Jul  5 18:56:09 f64 kernel: [ 8178.723129] sd 10:0:0:0: [sdf] Write Protect is off
Jul  5 18:56:09 f64 kernel: [ 8178.723132] sd 10:0:0:0: [sdf] Mode Sense: 21 00 00 00
Jul  5 18:56:09 f64 kernel: [ 8178.723134] sd 10:0:0:0: [sdf] Assuming drive cache: write through
Jul  5 18:56:09 f64 kernel: [ 8178.726995] sd 10:0:0:0: [sdf] 1250263728 512-byte hardware sectors (640135 MB)
Jul  5 18:56:09 f64 kernel: [ 8178.730112] sd 10:0:0:0: [sdf] Write Protect is off
Jul  5 18:56:09 f64 kernel: [ 8178.730114] sd 10:0:0:0: [sdf] Mode Sense: 21 00 00 00
Jul  5 18:56:09 f64 kernel: [ 8178.730116] sd 10:0:0:0: [sdf] Assuming drive cache: write through
Jul  5 18:56:09 f64 kernel: [ 8178.730120]  sdf: sdf1
Jul  5 18:56:09 f64 kernel: [ 8178.745151] sd 10:0:0:0: [sdf] Attached SCSI disk
Jul  5 18:56:09 f64 kernel: [ 8178.745186] sd 10:0:0:0: Attached scsi generic sg4 type 0
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.247134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.249041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.262247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.342114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_6400AAK_External_574341535932383836353731_0_0'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.441348] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_758f20a7_95de_45e6_9c26_65f5322d030e'). 
Jul  5 18:56:09 f64 kernel: [ 8179.010420] usb-storage: device scan complete
Jul  5 18:56:09 f64 kernel: [ 8179.045690] scsi 11:0:0:0: Direct-Access     WD       5000AAKB Externa l108 PQ: 0 ANSI: 0
Jul  5 18:56:09 f64 kernel: [ 8179.054415] sd 11:0:0:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
Jul  5 18:56:09 f64 kernel: [ 8179.057525] sd 11:0:0:0: [sdg] Write Protect is off
Jul  5 18:56:09 f64 kernel: [ 8179.057528] sd 11:0:0:0: [sdg] Mode Sense: 03 00 00 00
Jul  5 18:56:09 f64 kernel: [ 8179.057530] sd 11:0:0:0: [sdg] Assuming drive cache: write through
Jul  5 18:56:09 f64 kernel: [ 8179.061395] sd 11:0:0:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
Jul  5 18:56:09 f64 kernel: [ 8179.064512] sd 11:0:0:0: [sdg] Write Protect is off
Jul  5 18:56:09 f64 kernel: [ 8179.064514] sd 11:0:0:0: [sdg] Mode Sense: 03 00 00 00
Jul  5 18:56:09 f64 kernel: [ 8179.064516] sd 11:0:0:0: [sdg] Assuming drive cache: write through
Jul  5 18:56:09 f64 kernel: [ 8179.064522]  sdg: sdg1
Jul  5 18:56:09 f64 kernel: [ 8179.074320] sd 11:0:0:0: [sdg] Attached SCSI disk
Jul  5 18:56:09 f64 kernel: [ 8179.074360] sd 11:0:0:0: Attached scsi generic sg5 type 0
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.581764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.585599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.592341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_901_57442D574341505732363736383238_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.688815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_5000AAKB_Externa_57442D574341505732363736383238_0_0'). 
Jul  5 18:56:09 f64 NetworkManager: <debug> [1246841769.839163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_ec6e1434_6937_4eb0_a746_28fbebb16449'). 
Jul  5 18:56:13 f64 kernel: [ 8182.778650] usb 2-3.1: new high speed USB device using ehci_hcd and address 9
Jul  5 18:56:13 f64 kernel: [ 8182.872425] usb 2-3.1: configuration #1 chosen from 1 choice
Jul  5 18:56:13 f64 NetworkManager: <debug> [1246841773.380054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000'). 
Jul  5 18:56:13 f64 kernel: [ 8182.893004] scsi12 : SCSI emulation for USB Mass Storage devices
Jul  5 18:56:13 f64 kernel: [ 8182.893274] usb-storage: device found at 9
Jul  5 18:56:13 f64 kernel: [ 8182.893277] usb-storage: waiting for device to settle before scanning
Jul  5 18:56:13 f64 NetworkManager: <debug> [1246841773.425837] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0'). 
Jul  5 18:56:18 f64 kernel: [ 8187.884957] usb-storage: device scan complete
Jul  5 18:56:18 f64 kernel: [ 8187.887309] scsi 12:0:0:0: Direct-Access     SanDisk  Sansa Clip 2GB   v02. PQ: 0 ANSI: 0
Jul  5 18:56:18 f64 kernel: [ 8187.895286] sd 12:0:0:0: [sdh] 3801088 512-byte hardware sectors (1946 MB)
Jul  5 18:56:18 f64 kernel: [ 8187.898148] sd 12:0:0:0: [sdh] Write Protect is off
Jul  5 18:56:18 f64 kernel: [ 8187.898150] sd 12:0:0:0: [sdh] Mode Sense: 04 00 00 00
Jul  5 18:56:18 f64 kernel: [ 8187.898152] sd 12:0:0:0: [sdh] Assuming drive cache: write through
Jul  5 18:56:18 f64 kernel: [ 8187.906258] sd 12:0:0:0: [sdh] 3801088 512-byte hardware sectors (1946 MB)
Jul  5 18:56:18 f64 kernel: [ 8187.909125] sd 12:0:0:0: [sdh] Write Protect is off
Jul  5 18:56:18 f64 kernel: [ 8187.909129] sd 12:0:0:0: [sdh] Mode Sense: 04 00 00 00
Jul  5 18:56:18 f64 kernel: [ 8187.909130] sd 12:0:0:0: [sdh] Assuming drive cache: write through
Jul  5 18:56:18 f64 kernel: [ 8187.909289]  sdh:
Jul  5 18:56:18 f64 kernel: [ 8187.917146] sd 12:0:0:0: [sdh] Attached SCSI removable disk
Jul  5 18:56:18 f64 kernel: [ 8187.917250] sd 12:0:0:0: Attached scsi generic sg6 type 0
Jul  5 18:56:18 f64 NetworkManager: <debug> [1246841778.443187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host'). 
Jul  5 18:56:18 f64 NetworkManager: <debug> [1246841778.446151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:56:18 f64 NetworkManager: <debug> [1246841778.454694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:56:18 f64 NetworkManager: <debug> [1246841778.556239] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Sansa_Clip_2GB_DF06F0014326B6A80000000000000000_0_0'). 
Jul  5 18:56:18 f64 NetworkManager: <debug> [1246841778.629067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0123_4567'). 
Jul  5 18:56:18 f64 hald: mounted /dev/sdh on behalf of uid 1000
Jul  5 18:58:05 f64 kernel: [ 8294.760891] usb 2-3.1: USB disconnect, address 9
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.478278] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.484678] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0123_4567'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.484738] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Sansa_Clip_2GB_DF06F0014326B6A80000000000000000_0_0'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.518764] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host_scsi_device_lun0'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.518827] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0_scsi_host'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.522913] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000_if0'). 
Jul  5 18:58:05 f64 NetworkManager: <debug> [1246841885.542035] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_7435_DF06F0014326B6A80000000000000000'). 
Jul  5 19:00:06 f64 kernel: [ 8415.372536] usb 2-3.2: USB disconnect, address 6
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.316996] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.333277] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_758f20a7_95de_45e6_9c26_65f5322d030e'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.359039] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_6400AAK_External_574341535932383836353731_0_0'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.369434] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.369500] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.373758] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0'). 
Jul  5 19:00:06 f64 NetworkManager: <debug> [1246842006.377661] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731'). 
Jul  5 19:00:14 f64 kernel: [ 8423.749000] usb 2-3.2: new high speed USB device using ehci_hcd and address 10
Jul  5 19:00:14 f64 kernel: [ 8423.842275] usb 2-3.2: configuration #1 chosen from 1 choice
Jul  5 19:00:14 f64 kernel: [ 8423.842396] scsi13 : SCSI emulation for USB Mass Storage devices
Jul  5 19:00:14 f64 kernel: [ 8423.842488] usb-storage: device found at 10
Jul  5 19:00:14 f64 kernel: [ 8423.842491] usb-storage: waiting for device to settle before scanning
Jul  5 19:00:14 f64 NetworkManager: <debug> [1246842014.803407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731'). 
Jul  5 19:00:14 f64 NetworkManager: <debug> [1246842014.851886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0'). 
Jul  5 19:00:19 f64 kernel: [ 8428.831237] usb-storage: device scan complete
Jul  5 19:00:19 f64 kernel: [ 8428.833338] scsi 13:0:0:0: Direct-Access     WD       6400AAK External 1.05 PQ: 0 ANSI: 4
Jul  5 19:00:19 f64 kernel: [ 8428.837327] sd 13:0:0:0: [sdf] 1250263728 512-byte hardware sectors (640135 MB)
Jul  5 19:00:19 f64 kernel: [ 8428.841326] sd 13:0:0:0: [sdf] Write Protect is off
Jul  5 19:00:19 f64 kernel: [ 8428.841331] sd 13:0:0:0: [sdf] Mode Sense: 21 00 00 00
Jul  5 19:00:19 f64 kernel: [ 8428.841333] sd 13:0:0:0: [sdf] Assuming drive cache: write through
Jul  5 19:00:19 f64 kernel: [ 8428.845307] sd 13:0:0:0: [sdf] 1250263728 512-byte hardware sectors (640135 MB)
Jul  5 19:00:19 f64 kernel: [ 8428.848469] sd 13:0:0:0: [sdf] Write Protect is off
Jul  5 19:00:19 f64 kernel: [ 8428.848476] sd 13:0:0:0: [sdf] Mode Sense: 21 00 00 00
Jul  5 19:00:19 f64 kernel: [ 8428.848479] sd 13:0:0:0: [sdf] Assuming drive cache: write through
Jul  5 19:00:19 f64 kernel: [ 8428.848484]  sdf: sdf1
Jul  5 19:00:19 f64 kernel: [ 8428.862485] sd 13:0:0:0: [sdf] Attached SCSI disk
Jul  5 19:00:19 f64 kernel: [ 8428.862524] sd 13:0:0:0: Attached scsi generic sg4 type 0
Jul  5 19:00:19 f64 NetworkManager: <debug> [1246842019.839902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host'). 
Jul  5 19:00:19 f64 NetworkManager: <debug> [1246842019.840997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0'). 
Jul  5 19:00:19 f64 NetworkManager: <debug> [1246842019.855601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_1001_574341535932383836353731_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 19:00:19 f64 NetworkManager: <debug> [1246842019.937871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_6400AAK_External_574341535932383836353731_0_0'). 
Jul  5 19:00:20 f64 NetworkManager: <debug> [1246842020.029526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_758f20a7_95de_45e6_9c26_65f5322d030e'). 
```

---

