---
title: "HUAWEI E1550 sometimes works and sometimes doesn't"
date: 2010-05-17
forum: General Help
---

### Post by muctadir on 2010-05-17
hi. i am using huawei e1550 wireless modem. my ubuntu 10.04 didn't recognize the modem. but after i installed usb-modeswitch and wrote a rule in /etc/udev/rules.d/15-huawei-e1550.rules the modem is recognized. the rule is like this-
SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

but still i am having some problems. sometimes the modem is not recognized and i have to restart the computer and replug-in the modem to make it recognized. after all this i can connect to the internet. below is the log when the modem can't connect-
May 17 12:43:07 planet-muctadir kernel: [  545.640032] usb 1-1: new high speed USB device using ehci_hcd and address 24
May 17 12:43:07 planet-muctadir kernel: [  545.783394] usb 1-1: configuration #1 chosen from 1 choice
May 17 12:43:07 planet-muctadir kernel: [  545.787888] scsi100 : SCSI emulation for USB Mass Storage devices
May 17 12:43:07 planet-muctadir kernel: [  545.788101] usb-storage: device found at 24
May 17 12:43:07 planet-muctadir kernel: [  545.788104] usb-storage: waiting for device to settle before scanning
May 17 12:43:07 planet-muctadir kernel: [  545.788137] scsi101 : SCSI emulation for USB Mass Storage devices
May 17 12:43:07 planet-muctadir kernel: [  545.788252] usb-storage: device found at 24
May 17 12:43:07 planet-muctadir kernel: [  545.788255] usb-storage: waiting for device to settle before scanning
May 17 12:43:10 planet-muctadir kernel: [  547.912656] usb 1-1: usbfs: process 10017 (modem-modeswitc) did not claim interface 0 before use
May 17 12:43:10 planet-muctadir usb-modeswitch: switching 12d1:1446 (HUAWEI Technology: HUAWEI Mobile)
May 17 12:43:10 planet-muctadir kernel: [  548.432845] usb 1-1: USB disconnect, address 24
May 17 12:43:16 planet-muctadir kernel: [  554.388013] usb 1-1: new high speed USB device using ehci_hcd and address 25
May 17 12:43:16 planet-muctadir kernel: [  554.531428] usb 1-1: configuration #1 chosen from 1 choice
May 17 12:43:16 planet-muctadir kernel: [  554.536434] option 1-1:1.0: GSM modem (1-port) converter detected
May 17 12:43:16 planet-muctadir kernel: [  554.536541] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
May 17 12:43:16 planet-muctadir kernel: [  554.536667] option 1-1:1.1: GSM modem (1-port) converter detected
May 17 12:43:16 planet-muctadir kernel: [  554.536756] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
May 17 12:43:16 planet-muctadir kernel: [  554.536878] option 1-1:1.2: GSM modem (1-port) converter detected
May 17 12:43:16 planet-muctadir kernel: [  554.536945] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
May 17 12:43:16 planet-muctadir kernel: [  554.537058] option 1-1:1.3: GSM modem (1-port) converter detected
May 17 12:43:16 planet-muctadir kernel: [  554.537123] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
May 17 12:43:16 planet-muctadir kernel: [  554.538472] scsi106 : SCSI emulation for USB Mass Storage devices
May 17 12:43:16 planet-muctadir kernel: [  554.538629] usb-storage: device found at 25
May 17 12:43:16 planet-muctadir kernel: [  554.538631] usb-storage: waiting for device to settle before scanning
May 17 12:43:16 planet-muctadir kernel: [  554.539469] scsi107 : SCSI emulation for USB Mass Storage devices
May 17 12:43:16 planet-muctadir kernel: [  554.539633] usb-storage: device found at 25
May 17 12:43:16 planet-muctadir kernel: [  554.539635] usb-storage: waiting for device to settle before scanning
May 17 12:43:16 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:16 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:16 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:17 planet-muctadir usb-modeswitch: switched to 12d1:140c (HUAWEI Technology: HUAWEI Mobile)
May 17 12:43:19 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:19 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:19 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:19 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:19 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:19 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:21 planet-muctadir kernel: [  559.537762] usb-storage: device scan complete
May 17 12:43:21 planet-muctadir kernel: [  559.539313] usb-storage: device scan complete
May 17 12:43:21 planet-muctadir kernel: [  559.539458] scsi 106:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
May 17 12:43:21 planet-muctadir kernel: [  559.541618] scsi 107:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
May 17 12:43:21 planet-muctadir kernel: [  559.560302] sr1: scsi-1 drive
May 17 12:43:21 planet-muctadir kernel: [  559.560443] sr 106:0:0:0: Attached scsi CD-ROM sr1
May 17 12:43:21 planet-muctadir kernel: [  559.560543] sr 106:0:0:0: Attached scsi generic sg3 type 5
May 17 12:43:21 planet-muctadir kernel: [  559.561214] sd 107:0:0:0: Attached scsi generic sg5 type 0
May 17 12:43:21 planet-muctadir kernel: [  559.570556] sd 107:0:0:0: [sdb] Attached SCSI removable disk
May 17 12:43:22 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:22 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:22 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:22 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:22 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:22 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:25 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:25 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:25 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:25 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:25 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:25 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:28 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:28 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:28 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:28 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:28 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:28 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:31 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:31 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:31 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:31 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:31 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:31 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:34 planet-muctadir kernel: [  572.323260] ISO 9660 Extensions: Microsoft Joliet Level 1
May 17 12:43:34 planet-muctadir kernel: [  572.326262] ISOFS: changing to secondary root
May 17 12:43:34 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:34 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:34 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:34 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:34 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:34 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:37 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:37 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:37 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:37 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:37 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:37 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:40 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:40 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:40 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:40 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:40 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:40 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:43 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:43 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:43 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:43 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:43 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:43 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:46 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:46 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:46 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:46 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:46 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:46 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:49 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:49 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:49 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:49 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:49 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:49 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:52 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:52 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:52 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:52 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:52 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:52 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:55 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:55 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:55 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:55 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:55 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:55 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:43:58 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:43:58 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:43:58 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:43:58 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:43:58 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:43:58 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:01 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:01 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:01 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:01 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:01 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:01 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:04 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:04 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:04 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:04 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:04 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:04 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:07 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:07 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:07 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:07 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:07 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:07 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:10 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:10 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:10 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:10 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:10 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:10 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:13 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:13 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:13 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:13 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:13 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:13 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:44:16 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:44:16 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:44:16 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:44:16 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:44:16 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:44:16 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check


and this is the log when the modem is connected-

May 17 12:45:55 planet-muctadir kernel: [   59.744016] usb 1-1: new high speed USB device using ehci_hcd and address 3
May 17 12:45:56 planet-muctadir kernel: [   59.887445] usb 1-1: configuration #1 chosen from 1 choice
May 17 12:45:56 planet-muctadir kernel: [   59.891698] scsi3 : SCSI emulation for USB Mass Storage devices
May 17 12:45:56 planet-muctadir kernel: [   59.891806] usb-storage: device found at 3
May 17 12:45:56 planet-muctadir kernel: [   59.891808] usb-storage: waiting for device to settle before scanning
May 17 12:45:56 planet-muctadir kernel: [   59.891826] scsi4 : SCSI emulation for USB Mass Storage devices
May 17 12:45:56 planet-muctadir kernel: [   59.891901] usb-storage: device found at 3
May 17 12:45:56 planet-muctadir kernel: [   59.891903] usb-storage: waiting for device to settle before scanning
May 17 12:45:58 planet-muctadir kernel: [   62.355577] usb 1-1: usbfs: process 2831 (modem-modeswitc) did not claim interface 0 before use
May 17 12:45:59 planet-muctadir usb-modeswitch: switching 12d1:1446 (HUAWEI Technology: HUAWEI Mobile)
May 17 12:45:59 planet-muctadir kernel: [   63.143668] usb 1-1: USB disconnect, address 3
May 17 12:46:05 planet-muctadir kernel: [   69.496020] usb 1-1: new high speed USB device using ehci_hcd and address 4
May 17 12:46:05 planet-muctadir kernel: [   69.639468] usb 1-1: configuration #1 chosen from 1 choice
May 17 12:46:05 planet-muctadir kernel: [   69.645134] scsi9 : SCSI emulation for USB Mass Storage devices
May 17 12:46:05 planet-muctadir kernel: [   69.645256] usb-storage: device found at 4
May 17 12:46:05 planet-muctadir kernel: [   69.645258] usb-storage: waiting for device to settle before scanning
May 17 12:46:05 planet-muctadir kernel: [   69.646132] scsi10 : SCSI emulation for USB Mass Storage devices
May 17 12:46:05 planet-muctadir kernel: [   69.646228] usb-storage: device found at 4
May 17 12:46:05 planet-muctadir kernel: [   69.646229] usb-storage: waiting for device to settle before scanning
May 17 12:46:06 planet-muctadir kernel: [   70.158745] usbcore: registered new interface driver usbserial
May 17 12:46:06 planet-muctadir kernel: [   70.158756] USB Serial support registered for generic
May 17 12:46:06 planet-muctadir kernel: [   70.265258] usbcore: registered new interface driver usbserial_generic
May 17 12:46:06 planet-muctadir kernel: [   70.265261] usbserial: USB Serial Driver core
May 17 12:46:06 planet-muctadir kernel: [   70.275651] USB Serial support registered for GSM modem (1-port)
May 17 12:46:06 planet-muctadir kernel: [   70.275876] option 1-1:1.0: GSM modem (1-port) converter detected
May 17 12:46:06 planet-muctadir kernel: [   70.276028] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
May 17 12:46:06 planet-muctadir kernel: [   70.276041] option 1-1:1.1: GSM modem (1-port) converter detected
May 17 12:46:06 planet-muctadir kernel: [   70.276141] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
May 17 12:46:06 planet-muctadir kernel: [   70.276151] option 1-1:1.2: GSM modem (1-port) converter detected
May 17 12:46:06 planet-muctadir kernel: [   70.276233] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
May 17 12:46:06 planet-muctadir kernel: [   70.276243] option 1-1:1.3: GSM modem (1-port) converter detected
May 17 12:46:06 planet-muctadir kernel: [   70.276339] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
May 17 12:46:06 planet-muctadir kernel: [   70.276358] usbcore: registered new interface driver option
May 17 12:46:06 planet-muctadir kernel: [   70.276360] option: v0.7.2:USB Driver for GSM modems
May 17 12:46:06 planet-muctadir usb-modeswitch: switched to 12d1:140c (HUAWEI Technology: HUAWEI Mobile)
May 17 12:46:08 planet-muctadir modem-manager: (Huawei): (ttyUSB3) deferring support check
May 17 12:46:08 planet-muctadir modem-manager: (Huawei): (ttyUSB2) deferring support check
May 17 12:46:08 planet-muctadir modem-manager: (ttyUSB0) opening serial device...
May 17 12:46:08 planet-muctadir modem-manager: (ttyUSB0): probe requested by plugin 'Huawei'
May 17 12:46:08 planet-muctadir modem-manager: (Huawei): (ttyUSB1) deferring support check
May 17 12:46:09 planet-muctadir modem-manager: (ttyUSB0) closing serial device...
May 17 12:46:09 planet-muctadir modem-manager: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB0
May 17 12:46:09 planet-muctadir modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
May 17 12:46:09 planet-muctadir modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 as /org/freedesktop/ModemManager/Modems/0
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): new GSM device (driver: 'option1')
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/1
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): now managed
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)
May 17 12:46:09 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) starting connection 'GrameenPhone Default'
May 17 12:46:09 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
May 17 12:46:09 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
May 17 12:46:09 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
May 17 12:46:09 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
May 17 12:46:09 planet-muctadir modem-manager: (ttyUSB0) opening serial device...
May 17 12:46:09 planet-muctadir modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
May 17 12:46:09 planet-muctadir modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
May 17 12:46:10 planet-muctadir kernel: [   74.645604] usb-storage: device scan complete
May 17 12:46:10 planet-muctadir kernel: [   74.647454] usb-storage: device scan complete
May 17 12:46:10 planet-muctadir kernel: [   74.647604] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
May 17 12:46:10 planet-muctadir kernel: [   74.649594] scsi 10:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
May 17 12:46:10 planet-muctadir kernel: [   74.675449] sr1: scsi-1 drive
May 17 12:46:10 planet-muctadir kernel: [   74.675607] sr 9:0:0:0: Attached scsi CD-ROM sr1
May 17 12:46:10 planet-muctadir kernel: [   74.675693] sr 9:0:0:0: Attached scsi generic sg2 type 5
May 17 12:46:10 planet-muctadir kernel: [   74.676606] sd 10:0:0:0: Attached scsi generic sg3 type 0
May 17 12:46:10 planet-muctadir kernel: [   74.685448] sd 10:0:0:0: [sdb] Attached SCSI removable disk
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB3): re-checking support...
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB3) opening serial device...
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB2): re-checking support...
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB2) opening serial device...
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB3) closing serial device...
May 17 12:46:11 planet-muctadir modem-manager: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB3
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB1): re-checking support...
May 17 12:46:11 planet-muctadir modem-manager: (ttyUSB1) opening serial device...
May 17 12:46:14 planet-muctadir modem-manager: Registration state changed: 1
May 17 12:46:14 planet-muctadir modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
May 17 12:46:14 planet-muctadir modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
May 17 12:46:14 planet-muctadir modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
May 17 12:46:14 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
May 17 12:46:14 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Starting pppd connection
May 17 12:46:14 planet-muctadir NetworkManager: <debug> [1274078774.107364] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
May 17 12:46:14 planet-muctadir NetworkManager: <debug> [1274078774.120388] nm_ppp_manager_start(): ppp started with pid 3141
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
May 17 12:46:14 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
May 17 12:46:14 planet-muctadir pppd[3141]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
May 17 12:46:14 planet-muctadir pppd[3141]: pppd 2.4.5 started by root, uid 0
May 17 12:46:14 planet-muctadir pppd[3141]: Using interface ppp0
May 17 12:46:14 planet-muctadir pppd[3141]: Connect: ppp0 <--> /dev/ttyUSB0
May 17 12:46:14 planet-muctadir pppd[3141]: CHAP authentication succeeded
May 17 12:46:14 planet-muctadir pppd[3141]: CHAP authentication succeeded
May 17 12:46:14 planet-muctadir kernel: [   78.074814] PPP BSD Compression module registered
May 17 12:46:14 planet-muctadir kernel: [   78.097018] PPP Deflate Compression module registered
May 17 12:46:14 planet-muctadir NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 17 12:46:14 planet-muctadir NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB2) closing serial device...
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB2) opening serial device...
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB1) closing serial device...
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB1) opening serial device...
May 17 12:46:16 planet-muctadir modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
May 17 12:46:20 planet-muctadir AptDaemon: INFO: Initializing daemon
May 17 12:46:21 planet-muctadir pppd[3141]: Could not determine remote IP address: defaulting to 10.64.64.64
May 17 12:46:21 planet-muctadir pppd[3141]: Cannot determine ethernet address for proxy ARP
May 17 12:46:21 planet-muctadir pppd[3141]: local  IP address 10.130.33.243
May 17 12:46:21 planet-muctadir pppd[3141]: remote IP address 10.64.64.64
May 17 12:46:21 planet-muctadir NetworkManager: <info>  PPP manager(IP Config Get) reply received.
May 17 12:46:21 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May 17 12:46:21 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) started...
May 17 12:46:21 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 17 12:46:21 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) complete.
May 17 12:46:21 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
May 17 12:46:22 planet-muctadir NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 (reason 0)
May 17 12:46:22 planet-muctadir NetworkManager: <info>  Policy set 'GrameenPhone Default' (ppp0) as default for routing and DNS.
May 17 12:46:22 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) successful, device activated.
May 17 12:46:22 planet-muctadir NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.

please help me fixing this. thanks in advance....

---

### Post by nabilnasir on 2010-11-17
try read this.. hope i can help you out!

[http://yoga1290.wordpress.com/2010/05/05/simple-trick-2-get-etisalathuawei-e1550-work-under-ubuntu-10-04/](http://yoga1290.wordpress.com/2010/05/05/simple-trick-2-get-etisalathuawei-e1550-work-under-ubuntu-10-04/)

---

