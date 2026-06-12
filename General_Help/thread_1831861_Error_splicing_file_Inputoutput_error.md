---
title: "Error splicing file: Input/output error"
date: 2011-08-23
forum: General Help
---

### Post by CaptSaltyJack on 2011-08-23
Anyone know what causes this error when I try to copy a file from a USB thumb drive? Sad thing is, it only happens on one specific USB port.. so I'm hoping I didn't get a bad laptop from System76. :(

syslog below:

```
Aug 23 22:34:26 obsidian kernel: [  360.290789] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:26 obsidian kernel: [  360.408081] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:26 obsidian kernel: [  360.429848] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:26 obsidian kernel: [  360.429972] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:26 obsidian kernel: [  360.429982] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:26 obsidian kernel: [  360.722062] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:26 obsidian kernel: [  360.837663] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:26 obsidian kernel: [  360.859586] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:26 obsidian kernel: [  360.859706] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:26 obsidian kernel: [  360.859717] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:26 obsidian kernel: [  360.863248] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:26 obsidian kernel: [  360.977742] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:26 obsidian kernel: [  360.999350] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:26 obsidian kernel: [  360.999498] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:26 obsidian kernel: [  360.999511] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:26 obsidian kernel: [  361.002712] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.117508] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.139356] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.139500] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.139510] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.142899] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.257404] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.279172] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.279326] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.279336] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.282617] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.397323] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.419155] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.419274] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.419284] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.422773] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.537249] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.558920] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.559063] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.559076] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.559707] sd 10:0:0:0: [sdb] Unhandled error code
Aug 23 22:34:27 obsidian kernel: [  361.559715] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Aug 23 22:34:27 obsidian kernel: [  361.559727] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 97 55 70 00 00 f0 00
Aug 23 22:34:27 obsidian kernel: [  361.559757] end_request: I/O error, dev sdb, sector 9917808
Aug 23 22:34:27 obsidian kernel: [  361.560458] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.677074] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.708745] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.708890] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.708903] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.710162] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.827036] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.848770] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.848896] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.848906] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.850397] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:27 obsidian kernel: [  361.966861] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:27 obsidian kernel: [  361.988599] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:27 obsidian kernel: [  361.988725] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:27 obsidian kernel: [  361.988735] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:27 obsidian kernel: [  361.990345] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.106733] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.128805] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.128930] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.128940] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.130504] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.246642] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.268316] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.268454] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.268461] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.269734] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.386499] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.408338] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.408475] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.408485] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.409268] sd 10:0:0:0: [sdb] Unhandled error code
Aug 23 22:34:28 obsidian kernel: [  362.409276] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Aug 23 22:34:28 obsidian kernel: [  362.409285] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 97 56 60 00 00 10 00
Aug 23 22:34:28 obsidian kernel: [  362.409304] end_request: I/O error, dev sdb, sector 9918048
Aug 23 22:34:28 obsidian kernel: [  362.410142] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.526311] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.548293] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.548432] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.548442] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.549875] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.666302] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.688224] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.688377] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.688387] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.689871] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.806067] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.827955] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.828079] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.828089] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.829531] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:28 obsidian kernel: [  362.946047] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:28 obsidian kernel: [  362.967912] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:28 obsidian kernel: [  362.968031] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:28 obsidian kernel: [  362.968041] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:28 obsidian kernel: [  362.969492] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.085879] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.107708] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.107810] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.107817] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.109141] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.225831] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.247569] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.247697] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.247707] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.248622] sd 10:0:0:0: [sdb] Unhandled error code
Aug 23 22:34:29 obsidian kernel: [  363.248630] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Aug 23 22:34:29 obsidian kernel: [  363.248638] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 97 56 70 00 00 f0 00
Aug 23 22:34:29 obsidian kernel: [  363.248657] end_request: I/O error, dev sdb, sector 9918064
Aug 23 22:34:29 obsidian kernel: [  363.249528] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.365665] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.387403] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.387536] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.387546] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.389018] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.505595] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.527420] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.527563] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.527574] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.528867] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.645447] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.667122] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.667270] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.667283] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.668574] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.785280] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.807116] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.807270] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.807290] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.808793] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:29 obsidian kernel: [  363.925208] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:29 obsidian kernel: [  363.947096] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:29 obsidian kernel: [  363.947234] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:29 obsidian kernel: [  363.947244] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:29 obsidian kernel: [  363.948745] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.065038] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.086984] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.087118] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.087126] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.087762] sd 10:0:0:0: [sdb] Unhandled error code
Aug 23 22:34:30 obsidian kernel: [  364.087766] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Aug 23 22:34:30 obsidian kernel: [  364.087774] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 97 57 60 00 00 10 00
Aug 23 22:34:30 obsidian kernel: [  364.087793] end_request: I/O error, dev sdb, sector 9918304
Aug 23 22:34:30 obsidian kernel: [  364.090482] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.204797] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.226760] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.226884] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.226894] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.230381] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.344812] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.366534] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.366667] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.366678] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.370057] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.484806] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.506545] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.506672] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.506682] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.510441] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.624757] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.646480] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.646651] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.646661] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.650027] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.764589] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.786333] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.786554] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.786564] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.789920] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Aug 23 22:34:30 obsidian kernel: [  364.904350] usb 3-4: reset high speed USB device using xhci_hcd and address 5
Aug 23 22:34:30 obsidian kernel: [  364.926409] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Aug 23 22:34:30 obsidian kernel: [  364.926533] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b180
Aug 23 22:34:30 obsidian kernel: [  364.926544] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880200d0b1c0
Aug 23 22:34:30 obsidian kernel: [  364.927338] sd 10:0:0:0: [sdb] Unhandled error code
Aug 23 22:34:30 obsidian kernel: [  364.927346] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Aug 23 22:34:30 obsidian kernel: [  364.927354] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 97 55 70 00 00 80 00
Aug 23 22:34:30 obsidian kernel: [  364.927373] end_request: I/O error, dev sdb, sector 9917808


```

---

