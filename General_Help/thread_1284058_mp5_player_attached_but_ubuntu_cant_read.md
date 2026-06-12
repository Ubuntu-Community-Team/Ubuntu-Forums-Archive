---
title: "mp5 player attached but ubuntu cant read"
date: 2009-10-06
forum: General Help
---

### Post by muhammadg on 2009-10-06
my mp5 player is attached but ubuntu cant read here is my dmesg 

 : 0 ANSI: 0
[21101.497025] scsi 3:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21101.504500] sd 3:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21101.608360] sd 3:0:0:0: [sdc] Write Protect is off
[21101.608367] sd 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21101.608372] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[21101.608734] sd 3:0:0:0: [sdc] READ CAPACITY failed
[21101.608738] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21101.608745] sd 3:0:0:0: [sdc] Sense not available.
[21101.608798] sd 3:0:0:0: [sdc] Write Protect is off
[21101.608802] sd 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21101.608805] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[21101.609050] sd 3:0:0:0: [sdc] READ CAPACITY failed
[21101.609053] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21101.609059] sd 3:0:0:0: [sdc] Sense not available.
[21101.609111] sd 3:0:0:0: [sdc] Write Protect is off
[21101.609115] sd 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21101.609118] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[21101.609288] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[21101.609410] sd 3:0:0:0: Attached scsi generic sg3 type 0
[21101.609723] sd 3:0:0:1: [sdd] READ CAPACITY failed
[21101.609726] sd 3:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21101.609732] sd 3:0:0:1: [sdd] Sense not available.
[21101.609787] sd 3:0:0:1: [sdd] Write Protect is off
[21101.609791] sd 3:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21101.609794] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[21101.609900] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[21101.609978] sd 3:0:0:1: Attached scsi generic sg4 type 0
[21101.610045] usb 1-3: USB disconnect, address 4
[21118.732029] usb 1-3: new high speed USB device using ehci_hcd and address 5
[21118.896960] usb 1-3: configuration #1 chosen from 1 choice
[21118.960547] scsi4 : SCSI emulation for USB Mass Storage devices
[21118.964779] usb-storage: device found at 5
[21118.964784] usb-storage: waiting for device to settle before scanning
[21123.964225] usb-storage: device scan complete
[21123.964689] scsi 4:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21123.965046] scsi 4:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21123.969227] sd 4:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21124.068383] sd 4:0:0:0: [sdc] Write Protect is off
[21124.068390] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21124.068394] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[21124.068763] sd 4:0:0:0: [sdc] READ CAPACITY failed
[21124.068767] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21124.068773] sd 4:0:0:0: [sdc] Sense not available.
[21124.068828] sd 4:0:0:0: [sdc] Write Protect is off
[21124.068831] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21124.068834] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[21124.069085] sd 4:0:0:0: [sdc] READ CAPACITY failed
[21124.069088] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21124.069094] sd 4:0:0:0: [sdc] Sense not available.
[21124.069148] sd 4:0:0:0: [sdc] Write Protect is off
[21124.069151] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21124.069154] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[21124.069321] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[21124.069442] sd 4:0:0:0: Attached scsi generic sg3 type 0
[21124.069756] sd 4:0:0:1: [sdd] READ CAPACITY failed
[21124.069759] sd 4:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21124.069765] sd 4:0:0:1: [sdd] Sense not available.
[21124.069821] sd 4:0:0:1: [sdd] Write Protect is off
[21124.069825] sd 4:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21124.069828] sd 4:0:0:1: [sdd] Assuming drive cache: write through
[21124.069934] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[21124.070012] sd 4:0:0:1: Attached scsi generic sg4 type 0
[21124.070078] usb 1-3: USB disconnect, address 5
[21163.116021] usb 1-3: new high speed USB device using ehci_hcd and address 6
[21163.282768] usb 1-3: configuration #1 chosen from 1 choice
[21163.319695] scsi5 : SCSI emulation for USB Mass Storage devices
[21163.322292] usb-storage: device found at 6
[21163.322297] usb-storage: waiting for device to settle before scanning
[21168.326424] usb-storage: device scan complete
[21168.326950] scsi 5:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21168.327432] scsi 5:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21168.332674] sd 5:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21168.388526] sd 5:0:0:0: [sdc] Write Protect is off
[21168.388532] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21168.388537] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21168.388902] sd 5:0:0:0: [sdc] READ CAPACITY failed
[21168.388906] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21168.388913] sd 5:0:0:0: [sdc] Sense not available.
[21168.388966] sd 5:0:0:0: [sdc] Write Protect is off
[21168.388970] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21168.388973] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21168.389215] sd 5:0:0:0: [sdc] READ CAPACITY failed
[21168.389218] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21168.389223] sd 5:0:0:0: [sdc] Sense not available.
[21168.389275] sd 5:0:0:0: [sdc] Write Protect is off
[21168.389279] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21168.389282] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21168.389442] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[21168.389559] sd 5:0:0:0: Attached scsi generic sg3 type 0
[21168.389863] sd 5:0:0:1: [sdd] READ CAPACITY failed
[21168.389866] sd 5:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21168.389872] sd 5:0:0:1: [sdd] Sense not available.
[21168.389925] sd 5:0:0:1: [sdd] Write Protect is off
[21168.389929] sd 5:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21168.389932] sd 5:0:0:1: [sdd] Assuming drive cache: write through
[21168.390037] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[21168.390116] sd 5:0:0:1: Attached scsi generic sg4 type 0
[21168.390186] usb 1-3: USB disconnect, address 6
[21203.352028] usb 1-3: new high speed USB device using ehci_hcd and address 7
[21203.517751] usb 1-3: configuration #1 chosen from 1 choice
[21203.554972] scsi6 : SCSI emulation for USB Mass Storage devices
[21203.557561] usb-storage: device found at 7
[21203.557566] usb-storage: waiting for device to settle before scanning
[21208.556283] usb-storage: device scan complete
[21208.556741] scsi 6:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21208.557103] scsi 6:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21208.561613] sd 6:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21208.652419] sd 6:0:0:0: [sdc] Write Protect is off
[21208.652426] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21208.652430] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[21208.652784] sd 6:0:0:0: [sdc] READ CAPACITY failed
[21208.652788] sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21208.652795] sd 6:0:0:0: [sdc] Sense not available.
[21208.652848] sd 6:0:0:0: [sdc] Write Protect is off
[21208.652851] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21208.652854] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[21208.653096] sd 6:0:0:0: [sdc] READ CAPACITY failed
[21208.653100] sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21208.653105] sd 6:0:0:0: [sdc] Sense not available.
[21208.653157] sd 6:0:0:0: [sdc] Write Protect is off
[21208.653161] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21208.653164] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[21208.653332] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[21208.653455] sd 6:0:0:0: Attached scsi generic sg3 type 0
[21208.653765] sd 6:0:0:1: [sdd] READ CAPACITY failed
[21208.653769] sd 6:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21208.653774] sd 6:0:0:1: [sdd] Sense not available.
[21208.653829] sd 6:0:0:1: [sdd] Write Protect is off
[21208.653832] sd 6:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21208.653835] sd 6:0:0:1: [sdd] Assuming drive cache: write through
[21208.653945] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[21208.654025] sd 6:0:0:1: Attached scsi generic sg4 type 0
[21208.654099] usb 1-3: USB disconnect, address 7
[21217.440028] usb 1-3: new high speed USB device using ehci_hcd and address 8
[21217.639569] usb 1-3: configuration #1 chosen from 1 choice
[21217.684068] scsi7 : SCSI emulation for USB Mass Storage devices
[21217.688754] usb-storage: device found at 8
[21217.688759] usb-storage: waiting for device to settle before scanning
[21222.694306] usb-storage: device scan complete
[21222.694864] scsi 7:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21222.695352] scsi 7:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21222.699629] sd 7:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21222.814645] usb 1-3: reset high speed USB device using ehci_hcd and address 8
[21223.004514] sd 7:0:0:0: [sdc] Write Protect is off
[21223.004521] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21223.004526] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[21223.004902] sd 7:0:0:0: [sdc] READ CAPACITY failed
[21223.004906] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21223.004913] sd 7:0:0:0: [sdc] Sense not available.
[21223.004969] sd 7:0:0:0: [sdc] Write Protect is off
[21223.004973] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21223.004976] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[21223.005229] sd 7:0:0:0: [sdc] READ CAPACITY failed
[21223.005233] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21223.005239] sd 7:0:0:0: [sdc] Sense not available.
[21223.005292] sd 7:0:0:0: [sdc] Write Protect is off
[21223.005296] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21223.005298] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[21223.012080] usb 1-3: USB disconnect, address 8
[21223.012466] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[21223.012560] sd 7:0:0:0: Attached scsi generic sg3 type 0
[21223.012785] sd 7:0:0:1: [sdd] READ CAPACITY failed
[21223.012789] sd 7:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[21223.012796] sd 7:0:0:1: [sdd] Sense not available.
[21223.012819] sd 7:0:0:1: [sdd] Write Protect is off
[21223.012823] sd 7:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21223.012827] sd 7:0:0:1: [sdd] Assuming drive cache: write through
[21223.012949] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[21223.013028] sd 7:0:0:1: Attached scsi generic sg4 type 0
[21673.672027] usb 1-3: new high speed USB device using ehci_hcd and address 9
[21673.838694] usb 1-3: configuration #1 chosen from 1 choice
[21673.876208] scsi8 : SCSI emulation for USB Mass Storage devices
[21673.879075] usb-storage: device found at 9
[21673.879080] usb-storage: waiting for device to settle before scanning
[21674.081703] usb 1-3: USB disconnect, address 9
[21674.784032] usb 1-3: new high speed USB device using ehci_hcd and address 10
[21674.917060] usb 1-3: configuration #1 chosen from 1 choice
[21674.985229] scsi9 : SCSI emulation for USB Mass Storage devices
[21674.988847] usb-storage: device found at 10
[21674.988852] usb-storage: waiting for device to settle before scanning
[21679.988286] usb-storage: device scan complete
[21679.988755] scsi 9:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21679.989110] scsi 9:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21679.993483] sd 9:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21680.104036] usb 1-3: reset high speed USB device using ehci_hcd and address 10
[21680.296388] sd 9:0:0:0: [sdc] Write Protect is off
[21680.296395] sd 9:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21680.296400] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[21680.296760] sd 9:0:0:0: [sdc] READ CAPACITY failed
[21680.296764] sd 9:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21680.296771] sd 9:0:0:0: [sdc] Sense not available.
[21680.296824] sd 9:0:0:0: [sdc] Write Protect is off
[21680.296827] sd 9:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21680.296830] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[21680.297075] sd 9:0:0:0: [sdc] READ CAPACITY failed
[21680.297078] sd 9:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21680.297084] sd 9:0:0:0: [sdc] Sense not available.
[21680.297135] sd 9:0:0:0: [sdc] Write Protect is off
[21680.297139] sd 9:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21680.297142] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[21680.297319] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[21680.297432] sd 9:0:0:0: Attached scsi generic sg3 type 0
[21680.297740] sd 9:0:0:1: [sdd] READ CAPACITY failed
[21680.297743] sd 9:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21680.297749] sd 9:0:0:1: [sdd] Sense not available.
[21680.297801] sd 9:0:0:1: [sdd] Write Protect is off
[21680.297805] sd 9:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21680.297808] sd 9:0:0:1: [sdd] Assuming drive cache: write through
[21680.297916] sd 9:0:0:1: [sdd] Attached SCSI removable disk
[21680.297996] sd 9:0:0:1: Attached scsi generic sg4 type 0
[21680.298071] usb 1-3: USB disconnect, address 10
[21735.332126] usb 1-3: new high speed USB device using ehci_hcd and address 11
[21735.512831] usb 1-3: configuration #1 chosen from 1 choice
[21735.558114] scsi10 : SCSI emulation for USB Mass Storage devices
[21735.561050] usb-storage: device found at 11
[21735.561054] usb-storage: waiting for device to settle before scanning
[21740.560191] usb-storage: device scan complete
[21740.560664] scsi 10:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[21740.561021] scsi 10:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[21740.565397] sd 10:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[21740.620494] sd 10:0:0:0: [sdc] Write Protect is off
[21740.620502] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21740.620506] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[21740.620875] sd 10:0:0:0: [sdc] READ CAPACITY failed
[21740.620879] sd 10:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21740.620885] sd 10:0:0:0: [sdc] Sense not available.
[21740.620938] sd 10:0:0:0: [sdc] Write Protect is off
[21740.620942] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21740.620945] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[21740.621186] sd 10:0:0:0: [sdc] READ CAPACITY failed
[21740.621189] sd 10:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21740.621195] sd 10:0:0:0: [sdc] Sense not available.
[21740.621246] sd 10:0:0:0: [sdc] Write Protect is off
[21740.621250] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[21740.621253] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[21740.621418] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[21740.621538] sd 10:0:0:0: Attached scsi generic sg3 type 0
[21740.621837] sd 10:0:0:1: [sdd] READ CAPACITY failed
[21740.621841] sd 10:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21740.621847] sd 10:0:0:1: [sdd] Sense not available.
[21740.621901] sd 10:0:0:1: [sdd] Write Protect is off
[21740.621905] sd 10:0:0:1: [sdd] Mode Sense: 00 00 00 00
[21740.621908] sd 10:0:0:1: [sdd] Assuming drive cache: write through
[21740.622017] sd 10:0:0:1: [sdd] Attached SCSI removable disk
[21740.622093] sd 10:0:0:1: Attached scsi generic sg4 type 0
[21740.622173] usb 1-3: USB disconnect, address 11
[22039.720030] usb 1-3: new high speed USB device using ehci_hcd and address 12
[22039.887191] usb 1-3: configuration #1 chosen from 1 choice
[22039.930400] scsi11 : SCSI emulation for USB Mass Storage devices
[22039.933352] usb-storage: device found at 12
[22039.933357] usb-storage: waiting for device to settle before scanning
[22044.932245] usb-storage: device scan complete
[22044.932718] scsi 11:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[22044.933074] scsi 11:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[22044.937096] sd 11:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[22045.096033] usb 1-3: reset high speed USB device using ehci_hcd and address 12
[22045.344041] usb 1-3: reset high speed USB device using ehci_hcd and address 12
[22045.400471] sd 11:0:0:0: [sdc] Write Protect is off
[22045.400477] sd 11:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22045.400481] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[22045.400849] sd 11:0:0:0: [sdc] READ CAPACITY failed
[22045.400853] sd 11:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22045.400859] sd 11:0:0:0: [sdc] Sense not available.
[22045.400913] sd 11:0:0:0: [sdc] Write Protect is off
[22045.400917] sd 11:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22045.400920] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[22045.401169] sd 11:0:0:0: [sdc] READ CAPACITY failed
[22045.401172] sd 11:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22045.401178] sd 11:0:0:0: [sdc] Sense not available.
[22045.401230] sd 11:0:0:0: [sdc] Write Protect is off
[22045.401234] sd 11:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22045.401236] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[22045.401411] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[22045.401533] sd 11:0:0:0: Attached scsi generic sg3 type 0
[22045.401844] sd 11:0:0:1: [sdd] READ CAPACITY failed
[22045.401847] sd 11:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22045.401853] sd 11:0:0:1: [sdd] Sense not available.
[22045.401909] sd 11:0:0:1: [sdd] Write Protect is off
[22045.401913] sd 11:0:0:1: [sdd] Mode Sense: 00 00 00 00
[22045.401916] sd 11:0:0:1: [sdd] Assuming drive cache: write through
[22045.402024] sd 11:0:0:1: [sdd] Attached SCSI removable disk
[22045.402108] sd 11:0:0:1: Attached scsi generic sg4 type 0
[22045.402178] usb 1-3: USB disconnect, address 12
[22048.548040] usb 1-3: new high speed USB device using ehci_hcd and address 13
[22048.713565] usb 1-3: configuration #1 chosen from 1 choice
[22048.754422] scsi12 : SCSI emulation for USB Mass Storage devices
[22048.757381] usb-storage: device found at 13
[22048.757386] usb-storage: waiting for device to settle before scanning
[22053.756206] usb-storage: device scan complete
[22053.756677] scsi 12:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[22053.757033] scsi 12:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[22053.761290] sd 12:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[22053.916046] usb 1-3: reset high speed USB device using ehci_hcd and address 13
[22053.972479] sd 12:0:0:0: [sdc] Write Protect is off
[22053.972486] sd 12:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22053.972490] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[22053.972858] sd 12:0:0:0: [sdc] READ CAPACITY failed
[22053.972862] sd 12:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22053.972869] sd 12:0:0:0: [sdc] Sense not available.
[22053.972921] sd 12:0:0:0: [sdc] Write Protect is off
[22053.972925] sd 12:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22053.972928] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[22053.973169] sd 12:0:0:0: [sdc] READ CAPACITY failed
[22053.973173] sd 12:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22053.973178] sd 12:0:0:0: [sdc] Sense not available.
[22053.973229] sd 12:0:0:0: [sdc] Write Protect is off
[22053.973233] sd 12:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22053.973236] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[22053.973403] sd 12:0:0:0: [sdc] Attached SCSI removable disk
[22053.973528] sd 12:0:0:0: Attached scsi generic sg3 type 0
[22053.973842] sd 12:0:0:1: [sdd] READ CAPACITY failed
[22053.973846] sd 12:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22053.973851] sd 12:0:0:1: [sdd] Sense not available.
[22053.973907] sd 12:0:0:1: [sdd] Write Protect is off
[22053.973910] sd 12:0:0:1: [sdd] Mode Sense: 00 00 00 00
[22053.973914] sd 12:0:0:1: [sdd] Assuming drive cache: write through
[22053.974024] sd 12:0:0:1: [sdd] Attached SCSI removable disk
[22053.974108] sd 12:0:0:1: Attached scsi generic sg4 type 0
[22053.974178] usb 1-3: USB disconnect, address 13
[22064.128548] usb 1-3: new high speed USB device using ehci_hcd and address 14
[22064.294273] usb 1-3: configuration #1 chosen from 1 choice
[22064.337879] scsi13 : SCSI emulation for USB Mass Storage devices
[22064.340800] usb-storage: device found at 14
[22064.340806] usb-storage: waiting for device to settle before scanning
[22069.340205] usb-storage: device scan complete
[22069.340676] scsi 13:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[22069.341034] scsi 13:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[22069.345537] sd 13:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[22069.460048] usb 1-3: reset high speed USB device using ehci_hcd and address 14
[22069.516364] sd 13:0:0:0: [sdc] Write Protect is off
[22069.516372] sd 13:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22069.516376] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[22069.516751] sd 13:0:0:0: [sdc] READ CAPACITY failed
[22069.516755] sd 13:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22069.516762] sd 13:0:0:0: [sdc] Sense not available.
[22069.516815] sd 13:0:0:0: [sdc] Write Protect is off
[22069.516818] sd 13:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22069.516821] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[22069.517071] sd 13:0:0:0: [sdc] READ CAPACITY failed
[22069.517074] sd 13:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22069.517080] sd 13:0:0:0: [sdc] Sense not available.
[22069.517133] sd 13:0:0:0: [sdc] Write Protect is off
[22069.517136] sd 13:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22069.517139] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[22069.517312] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[22069.517435] sd 13:0:0:0: Attached scsi generic sg3 type 0
[22069.517747] sd 13:0:0:1: [sdd] READ CAPACITY failed
[22069.517751] sd 13:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22069.517756] sd 13:0:0:1: [sdd] Sense not available.
[22069.517811] sd 13:0:0:1: [sdd] Write Protect is off
[22069.517815] sd 13:0:0:1: [sdd] Mode Sense: 00 00 00 00
[22069.517818] sd 13:0:0:1: [sdd] Assuming drive cache: write through
[22069.517926] sd 13:0:0:1: [sdd] Attached SCSI removable disk
[22069.518007] sd 13:0:0:1: Attached scsi generic sg4 type 0
[22069.518075] usb 1-3: USB disconnect, address 14
[22077.668032] usb 1-3: new high speed USB device using ehci_hcd and address 15
[22077.834418] usb 1-3: configuration #1 chosen from 1 choice
[22077.873334] scsi14 : SCSI emulation for USB Mass Storage devices
[22077.877102] usb-storage: device found at 15
[22077.877107] usb-storage: waiting for device to settle before scanning
[22082.876281] usb-storage: device scan complete
[22082.876756] scsi 14:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[22082.877113] scsi 14:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[22082.881383] sd 14:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[22083.028538] usb 1-3: reset high speed USB device using ehci_hcd and address 15
[22083.220404] sd 14:0:0:0: [sdc] Write Protect is off
[22083.220411] sd 14:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22083.220415] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[22083.220778] sd 14:0:0:0: [sdc] READ CAPACITY failed
[22083.220782] sd 14:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22083.220789] sd 14:0:0:0: [sdc] Sense not available.
[22083.220843] sd 14:0:0:0: [sdc] Write Protect is off
[22083.220846] sd 14:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22083.220849] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[22083.221094] sd 14:0:0:0: [sdc] READ CAPACITY failed
[22083.221098] sd 14:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22083.221103] sd 14:0:0:0: [sdc] Sense not available.
[22083.221156] sd 14:0:0:0: [sdc] Write Protect is off
[22083.221159] sd 14:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22083.221162] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[22083.221330] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[22083.221455] sd 14:0:0:0: Attached scsi generic sg3 type 0
[22083.221779] sd 14:0:0:1: [sdd] READ CAPACITY failed
[22083.221782] sd 14:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22083.221788] sd 14:0:0:1: [sdd] Sense not available.
[22083.221844] sd 14:0:0:1: [sdd] Write Protect is off
[22083.221848] sd 14:0:0:1: [sdd] Mode Sense: 00 00 00 00
[22083.221851] sd 14:0:0:1: [sdd] Assuming drive cache: write through
[22083.221958] sd 14:0:0:1: [sdd] Attached SCSI removable disk
[22083.222037] sd 14:0:0:1: Attached scsi generic sg4 type 0
[22083.222105] usb 1-3: USB disconnect, address 15
[22101.276275] usb 1-3: new high speed USB device using ehci_hcd and address 16
[22101.443304] usb 1-3: configuration #1 chosen from 1 choice
[22101.491576] scsi15 : SCSI emulation for USB Mass Storage devices
[22101.494437] usb-storage: device found at 16
[22101.494442] usb-storage: waiting for device to settle before scanning
[22106.492243] usb-storage: device scan complete
[22106.492718] scsi 15:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[22106.493073] scsi 15:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[22106.497223] sd 15:0:0:0: [sdc] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[22106.608040] usb 1-3: reset high speed USB device using ehci_hcd and address 16
[22106.856036] usb 1-3: reset high speed USB device using ehci_hcd and address 16
[22107.104080] usb 1-3: reset high speed USB device using ehci_hcd and address 16
[22107.160434] sd 15:0:0:0: [sdc] Write Protect is off
[22107.160441] sd 15:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22107.160445] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[22107.160813] sd 15:0:0:0: [sdc] READ CAPACITY failed
[22107.160816] sd 15:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22107.160823] sd 15:0:0:0: [sdc] Sense not available.
[22107.160877] sd 15:0:0:0: [sdc] Write Protect is off
[22107.160880] sd 15:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22107.160883] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[22107.161128] sd 15:0:0:0: [sdc] READ CAPACITY failed
[22107.161131] sd 15:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[22107.161137] sd 15:0:0:0: [sdc] Sense not available.
[22107.161189] sd 15:0:0:0: [sdc] Write Protect is off
[22107.161193] sd 15:0:0:0: [sdc] Mode Sense: 00 00 00 00
[22107.161196] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[22107.168246] usb 1-3: USB disconnect, address 16
[22107.169372] sd 15:0:0:0: [sdc] Attached SCSI removable disk
[22107.169491] sd 15:0:0:0: Attached scsi generic sg3 type 0
[22107.169711] sd 15:0:0:1: [sdd] READ CAPACITY failed
[22107.169715] sd 15:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[22107.169722] sd 15:0:0:1: [sdd] Sense not available.
[22107.169744] sd 15:0:0:1: [sdd] Write Protect is off
[22107.169749] sd 15:0:0:1: [sdd] Mode Sense: 00 00 00 00
[22107.169755] sd 15:0:0:1: [sdd] Assuming drive cache: write through
[22107.169877] sd 15:0:0:1: [sdd] Attached SCSI removable disk
[22107.169959] sd 15:0:0:1: Attached scsi generic sg4 type 0
[22132.220056] usb 1-3: new high speed USB device using ehci_hcd and address 17

---

### Post by kvarley on 2010-04-27
Is it an Onda VX747 by any chance?

---

