---
title: "K3520 Vodafone Mobile Partner Modem Cannot Detect and Install for Acer Aspire 5550"
date: 2010-04-28
forum: General Help
---

### Post by Cripple on 2010-04-28
Hi all,
 
I'm new in ubuntu. I have a problem that my K3520 vodafone mobile partner cannot be install and detect. If possible can teach me how to install the modem and then connect the internet. Thanks
 
Regards,
Cripple

---

### Post by tuxulin on 2010-04-28
[http://swiss.ubuntuforums.org/showthread.php?t=1244135&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1244135&page=2)

---

### Post by klemes on 2010-04-28
See the below post for information about connecting to the Internet with the above modem:

[http://ubuntuforums.org/archive/index.php/t-1244135.html](http://ubuntuforums.org/archive/index.php/t-1244135.html)

You can then ask here for everything that you do not understand or need help for.

Also could you unplug and than plug back in the USB modem and afterwards post the output of this command :

```
dmesg | tail -f
```
:popcorn:

---

### Post by Cripple on 2010-04-28
Hi Tuxulin and Klemes,
 
Thanks for reply my post, for ur information Tuxulin i already found that tread before. All the step i had follow but nothing happen.
 
 
This is the command for dmesg|tail -f
 
[ 1898.305250] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 1898.637245] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 1898.913267] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 1899.189263] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 1899.481277] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 1899.646925] sd 12:0:0:1: [sdb] Assuming drive cache: write through
[ 1899.646939]  sdb: sdb1
[ 1902.000204] wlan0: Trigger new scan to find an IBSS to join
[ 1904.425427] wlan0: Creating new IBSS network, BSSID d6:cb:71:18:eb:7e
[ 1906.988233] wlan0: Trigger new scan to find an IBSS to join
 
 
Thanks and Regards,
Cripple

---

### Post by klemes on 2010-04-28
Your modem does not seem to be recognized properly(meaning creating /dev/ttyUSB0-1 modem devices as it should)
What version of Ubuntu do you use?
Better give us some more info:

```
lsb_release -r
lsusb
dmesg |grep usb
```

---

### Post by Cripple on 2010-04-29
Hi thanks for your respond and sorry for late. its hard for me to online now. I use ubuntu 9.10
 
this is the code from the command u give before
 

```
[EMAIL="rizal@Cripple:~$"]rizal@Cripple:~$[/EMAIL] lsb_release -r
Release: 9.10
[EMAIL="rizal@Cripple:~$"]rizal@Cripple:~$[/EMAIL] lsusb
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 030: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[EMAIL="rizal@Cripple:~$"]rizal@Cripple:~$[/EMAIL] dmesg|grep usb
[38295.252255] usb 1-1: new high speed USB device using ehci_hcd and address 10
[38295.395254] usb 1-1: configuration #1 chosen from 1 choice
[38295.401944] usb-storage: device found at 10
[38295.401949] usb-storage: waiting for device to settle before scanning
[38300.400690] usb-storage: device scan complete
[39250.136222] usb 3-1: USB disconnect, address 2
[40658.305248] usb 1-1: USB disconnect, address 10
[40658.560221] usb 1-1: new high speed USB device using ehci_hcd and address 11
[40658.701930] usb 1-1: configuration #1 chosen from 1 choice
[40658.702851] usb-storage: device found at 11
[40658.702856] usb-storage: waiting for device to settle before scanning
[40659.084640] usb 1-1: USB disconnect, address 11
[40659.356221] usb 1-1: new high speed USB device using ehci_hcd and address 12
[40659.498053] usb 1-1: configuration #1 chosen from 1 choice
[40659.498965] usb-storage: device found at 12
[40659.498970] usb-storage: waiting for device to settle before scanning
[40660.653302] usb 1-1: USB disconnect, address 12
[40660.924260] usb 1-1: new high speed USB device using ehci_hcd and address 13
[40661.066054] usb 1-1: configuration #1 chosen from 1 choice
[40661.067497] usb-storage: device found at 13
[40661.067502] usb-storage: waiting for device to settle before scanning
[40662.630303] usb 1-1: USB disconnect, address 13
[40662.900255] usb 1-1: new high speed USB device using ehci_hcd and address 14
[40663.428242] usb 1-1: device not accepting address 14, error -71
[40663.540251] usb 1-1: new high speed USB device using ehci_hcd and address 15
[40663.852261] usb 1-1: new high speed USB device using ehci_hcd and address 16
[40663.994180] usb 1-1: configuration #1 chosen from 1 choice
[40663.995586] usb-storage: device found at 16
[40663.995590] usb-storage: waiting for device to settle before scanning
[40666.454805] usb 1-1: USB disconnect, address 16
[40666.724252] usb 1-1: new high speed USB device using ehci_hcd and address 17
[40666.866053] usb 1-1: configuration #1 chosen from 1 choice
[40666.867453] usb-storage: device found at 17
[40666.867457] usb-storage: waiting for device to settle before scanning
[40666.903156] usb 1-1: USB disconnect, address 17
[40667.152250] usb 1-1: new high speed USB device using ehci_hcd and address 18
[40667.294177] usb 1-1: configuration #1 chosen from 1 choice
[40667.295579] usb-storage: device found at 18
[40667.295584] usb-storage: waiting for device to settle before scanning
[40668.905122] usb 1-1: USB disconnect, address 18
[40669.176259] usb 1-1: new high speed USB device using ehci_hcd and address 19
[40669.318055] usb 1-1: configuration #1 chosen from 1 choice
[40669.319465] usb-storage: device found at 19
[40669.319469] usb-storage: waiting for device to settle before scanning
[40669.388528] usb 1-1: USB disconnect, address 19
[40669.660184] usb 1-1: new high speed USB device using ehci_hcd and address 20
[40669.802059] usb 1-1: configuration #1 chosen from 1 choice
[40669.802985] usb-storage: device found at 20
[40669.802991] usb-storage: waiting for device to settle before scanning
[40669.901029] usb 1-1: USB disconnect, address 20
[40670.172258] usb 1-1: new high speed USB device using ehci_hcd and address 21
[40670.700239] usb 1-1: device not accepting address 21, error -71
[40670.812259] usb 1-1: new high speed USB device using ehci_hcd and address 22
[40670.954055] usb 1-1: configuration #1 chosen from 1 choice
[40670.955464] usb-storage: device found at 22
[40670.955469] usb-storage: waiting for device to settle before scanning
[40672.222614] usb 1-1: USB disconnect, address 22
[40672.492199] usb 1-1: new high speed USB device using ehci_hcd and address 23
[40673.020192] usb 1-1: device not accepting address 23, error -71
[40673.132254] usb 1-1: new high speed USB device using ehci_hcd and address 24
[40673.274055] usb 1-1: configuration #1 chosen from 1 choice
[40673.275466] usb-storage: device found at 24
[40673.275470] usb-storage: waiting for device to settle before scanning
[40673.521052] usb 1-1: USB disconnect, address 24
[40673.792249] usb 1-1: new high speed USB device using ehci_hcd and address 25
[40673.934054] usb 1-1: configuration #1 chosen from 1 choice
[40673.935458] usb-storage: device found at 25
[40673.935462] usb-storage: waiting for device to settle before scanning
[40674.065554] usb 1-1: USB disconnect, address 25
[40674.336246] usb 1-1: new high speed USB device using ehci_hcd and address 26
[40674.888251] usb 2-1: new full speed USB device using uhci_hcd and address 3
[40675.192221] usb 2-1: new full speed USB device using uhci_hcd and address 4
[40675.632256] usb 2-1: new full speed USB device using uhci_hcd and address 5
[40675.932251] usb 2-1: new full speed USB device using uhci_hcd and address 6
[40676.078331] usb 2-1: not running at top speed; connect to a high speed hub
[40676.109508] usb 2-1: configuration #1 chosen from 1 choice
[40676.112685] usb-storage: device found at 6
[40676.112689] usb-storage: waiting for device to settle before scanning
[40681.114407] usb-storage: device scan complete
[40685.064318] usb 2-1: USB disconnect, address 6
[40685.304262] usb 1-1: new high speed USB device using ehci_hcd and address 27
[40685.446005] usb 1-1: configuration #1 chosen from 1 choice
[40685.446908] usb-storage: device found at 27
[40685.446913] usb-storage: waiting for device to settle before scanning
[40689.888628] usb 1-1: USB disconnect, address 27
[40721.840253] usb 4-1: new full speed USB device using uhci_hcd and address 5
[40722.003501] usb 4-1: configuration #1 chosen from 1 choice
[40722.020695] usb-storage: device found at 5
[40722.020701] usb-storage: waiting for device to settle before scanning
[40722.456300] usb 4-1: USB disconnect, address 5
[40722.696255] usb 4-1: new full speed USB device using uhci_hcd and address 6
[40722.859509] usb 4-1: configuration #1 chosen from 1 choice
[40722.883333] usb-storage: device found at 6
[40722.883338] usb-storage: waiting for device to settle before scanning
[40722.924237] usbcore: registered new interface driver usbserial
[40723.120262] usb 1-1: new high speed USB device using ehci_hcd and address 30
[40723.263216] usb 1-1: configuration #1 chosen from 1 choice
[40723.278838] usb-storage: device found at 30
[40723.278844] usb-storage: waiting for device to settle before scanning
[40723.279072] usbcore: registered new interface driver usbserial_generic
[40723.279077] usbserial: USB Serial Driver core
[40723.307848] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40723.307970] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40723.308132] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40723.308174] usbcore: registered new interface driver option
[40727.881394] usb-storage: device scan complete
[40728.104234] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40728.255730] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40728.259325] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40728.262505] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40728.284778] usb-storage: device scan complete
[40728.388104] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40728.536703] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40728.540194] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40728.557917] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40728.696078] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40728.843706] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40728.847228] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40728.866949] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40729.004099] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40729.151673] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40729.154107] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40729.154330] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40729.304098] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40729.455733] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40729.456331] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40729.468223] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40729.612100] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40729.759699] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40729.760710] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40729.761202] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40729.916099] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40730.063704] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40730.067764] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40730.067985] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40730.205097] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40730.352704] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40730.356242] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40730.359192] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40730.508102] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40730.657656] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40730.662904] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40730.676485] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40730.813080] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40730.963702] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40730.965054] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40730.971315] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40731.120088] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40731.271068] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40731.277910] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40731.292094] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40731.436103] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40731.585511] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40731.606669] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40731.606872] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40731.752097] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40731.902963] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40731.904322] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40731.909683] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40732.057147] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40732.205707] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40732.224697] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40732.232109] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40732.396097] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40732.555515] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40732.564172] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40732.573608] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40732.752077] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40732.920778] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40732.941268] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40732.941438] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40733.080078] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40733.231716] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40733.235239] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40733.242796] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40733.388179] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40733.599708] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40733.603274] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40733.615057] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40733.761123] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40733.912703] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40733.915930] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40733.916210] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40734.058350] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40734.212486] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40734.212731] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40734.212938] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40734.365755] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40734.528859] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40734.528987] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40734.550549] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40734.728239] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40734.907973] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40734.932248] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40734.936447] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40735.123741] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40735.312214] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40735.316197] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40735.338870] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40735.488053] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40735.640699] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40735.644150] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40735.649291] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40735.789067] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40735.937499] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40735.949881] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40735.960212] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40736.128130] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40736.292508] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40736.292747] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40736.311331] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40736.444942] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40736.632176] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40736.635211] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40736.645174] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40736.784108] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40736.959501] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40736.965224] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40736.965360] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40737.097047] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40737.268213] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40737.278683] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40737.281561] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40737.452288] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40737.605656] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40737.606975] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40737.607346] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40738.265267] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40738.473684] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40738.477142] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40738.480336] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40738.621280] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40738.783819] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40738.784805] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40738.786110] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40738.925234] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40739.134714] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40739.136113] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40739.139326] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40739.273247] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40739.425652] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40739.429163] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40739.442100] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40739.564231] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40739.715698] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40739.716687] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40739.719837] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40739.857455] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40740.026394] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40740.026520] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40740.026645] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40740.152230] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40740.307725] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40740.311243] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40740.314390] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40740.511454] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40740.661707] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40740.666953] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40740.667188] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40740.810696] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40740.964673] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40740.968108] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40740.970583] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40741.105287] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40741.258735] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40741.260803] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40741.268090] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40741.436210] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40741.583730] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40741.587018] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40741.590649] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40741.744228] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40741.892675] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40741.893487] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40741.893710] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40742.036215] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40742.201377] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40742.201510] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40742.221310] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40742.356232] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40742.507732] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40742.511318] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40742.514531] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40742.708075] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40742.855721] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40742.859518] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40742.859751] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40743.028215] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40743.176695] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40743.180187] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40743.195610] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40743.345607] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40743.495681] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40743.499256] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40743.502441] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40743.649281] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40743.802735] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40743.804154] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40743.809885] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40743.953235] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40744.105671] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40744.109127] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40744.109363] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40744.265264] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40744.417686] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40744.421285] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40744.445307] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40744.585303] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40744.736718] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40744.740184] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40744.757834] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[40744.893146] usb 4-1: reset full speed USB device using uhci_hcd and address 6
[40745.040725] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[40745.042217] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[40745.042461] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
```

---

### Post by klemes on 2010-04-29
Well everything seems alright from that and you seem to have a /dev/ttyUSB0-2 USB modem available after all.Whatever software you are using give /dev/ttyUSB0 as your modem device and everything should be straightforward from then on.
If you are using wvdial to connect with your modem simply copy the /etc/wvdial.conf that you'll find in the link I posted in the previous post in this thread and the use command wvdial or sudo wvdial to connect to the Internet.
If this however is not the case post the output of wvdial command and we will think of something.....:popcorn::guitar:

---

### Post by klemes on 2010-04-29
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet" #substitute APN here
Phone = *99***1#
Stupid Mode = 1

the above is the /etc/wvdial.conf you must use to connect.
Simply substitute internet with whatever the name of the APN your carrier uses and you are all set....

---

### Post by Cripple on 2010-04-29
Thanks a lot...i didnt understand what software should i use...in the modem, got setup.exe but execute just for windows..the problem now i dunno what to do next after plug in the modem. did I required to find any software or anything else?

---

### Post by klemes on 2010-04-29
I recommend using wvdial .Type sudo wvdial in a console and if it responds something like 'wvdial:command not found'
then you need to install it by:

```
sudo apt-get install wvdial
```

Then proceed to edit /etc/wvdial.conf with:

Alt+F2 -->gksudo gedit /etc/wvdial.conf

and tehn copy/paste the above wvdial.conf in it's place.
After that test it (with your modem plugged-in of course)
by running:

sudo wvdial

If everything is a alright you should be a able to connect to the Internet else cut and paste the output of the above command here and we 'll see what's wrong...

---

### Post by Cripple on 2010-04-29
after i type that command on terminal,i just got this things. what should i do next?
 
[EMAIL="rizal@Cripple:~$"]rizal@Cripple:~$[/EMAIL] sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wvdial has no installation candidate
:(

---

### Post by klemes on 2010-04-29
Go to System-->System Administartion-->Software sources

and check every repository available there (except Backports) close and then

sudo apt-get update

and then try again the 

sudo apt-get install wvdiall

command again.

---

### Post by Cripple on 2010-04-29
its seem that i dont have any internet connection there...hmm...anyway thanks for ur support

---

### Post by klemes on 2010-04-29
If you can't get your hands on wvdial then try to configure network-manager to work with your modem but I cannot give you any details there because I have not used it at all for such a purpose(as a matter of fact I have it completely removed it in this particular setup I am using at the moment).
But don't give up I mean it's nothing complicated.
Maybe someone else could give the exact instructions to connect using network-manager here.
And also there is the last resort solution of using pppd command directly ,but for that we will need to edit a couple of files,so we 'll use it as a last resort.

---

### Post by Cripple on 2010-04-30
Hi,

I already fully update my ubuntu 9.10. now can connect already after i follow your step given before. Thanks a lot :popcorn: :) I have 1 more question, how can i use the software that given in the modem, install and use the software :)

---

### Post by b3rylord on 2010-11-01
Hi I am having similar problems to Cripple except that i am using a Compaq Presario laptop with Ubuntu 10.10 installed on a clean hard drive. Wireless is no problem so am able to post this! but my K3250 dongle just sits there flashing at me. I have edited wvdial.conf as per Klemes suggestion

Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = web
Password = web
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet" #substitute APN here
Phone = *99***1#
Stupid Mode = 1

Vodafone confirmed the web web and internet as username password and APN

output of sudo wvdial is :-

 WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory


first day at this and it is a steep learning curve! Any ideas please??

---

### Post by klemes on 2010-11-02
I suggest that you use the Vodafone Mobile Connect software (VMC2)that you 'll find [here]("https://forge.betavine.net/frs/?group_id=12").
Once installed properly it will do the modeswitching thing,configure your modem properly,dial and most importantly keep track of your internet usage in MBytes.( that is useful especially if you don't have unlimited data plan).
Give it a shot and ask whatever you want here or in the betavine forum...:popcorn:

---

### Post by b3rylord on 2010-11-09
According to Ubuntu 10.10 known issues I need to get some stuff from Betavine:-

 bcm_2.99.10-1_all.deb
 python-messaging_0.5-1_all.deb
 sb-modeswitch-data_20100322-2betavine3_all.deb
 wader-core_0.5.3_all.deb

At Betavine it reads:-

If  you install this way your package manager will alert you to  pre-requisites needed, or you could use synaptic to do the hard work!  ;-)

For people who want the easy life just run the following  command which will also update your package management system to get the  latest and greatest packages from our repository.

sh -c 'wget [http://www.betavine.net/repository/bcm_lucid_install.sh](http://www.betavine.net/repository/bcm_lucid_install.sh) -O /tmp/bcm.sh && /usr/bin/xterm -e sudo sh /tmp/bcm.sh'

-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-0-

So I downloaded the four files above and double click on each but I am then told that
 I need to uninstall D-bus service for managing modems for two of the files and  
that a later version is installed for the other two, with no option to 
overwrite the "later" files. I am totally out of my depth now and would appreciate any help to 
get this sorted as I seem to be wading around with no progress.:confused: The "lazy way" alluded to above  just wanders off and does something but gives no indication of what and more importantly where? Synaptic could not find a package in downloads even though all four files are there. Do I need to make a package of these files?

---

