---
title: "New kernel update causes problem with graphics card"
date: 2011-10-28
forum: General Help
---

### Post by Mr Watch on 2011-10-28
Today I updated my system, as I usually do when the update thing pops up. I saw that there was a kernel update, so I had to restart when things had downloaded. When I restarted my system, I noticed instantly that things were a little slow. Something had deactivated my ATI/AMD propretary FGLRX graphics driver. When I tried to activate it, I was given an error, "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"
I went to look at that, but it's foreign to me. Should I delete my new kernel and boot from my older one, or is there a way to fix this and make my driver activate?

My jockey.log file:
```
2011-10-28 22:03:34,905 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c>
2011-10-28 22:03:34,906 DEBUG: reading modalias file /lib/modules/2.6.38-11-generic/modules.alias
2011-10-28 22:03:34,975 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-10-28 22:03:34,986 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-28 22:03:35,034 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-10-28 22:03:35,040 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-10-28 22:03:35,046 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-10-28 22:03:35,061 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-10-28 22:03:35,074 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-28 22:03:35,233 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-28 22:03:35,320 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-28 22:03:35,321 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-28 22:03:35,339 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-28 22:03:35,340 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-28 22:03:35,342 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-28 22:03:35,346 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-28 22:03:35,346 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-28 22:03:35,357 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-28 22:03:35,358 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-28 22:03:35,362 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-28 22:03:35,362 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-28 22:03:35,364 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-28 22:03:35,364 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-28 22:03:35,364 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-28 22:03:35,365 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-10-28 22:03:35,419 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-10-28 22:03:35,419 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-10-28 22:03:35,449 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-10-28 22:03:35,450 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-10-28 22:03:35,450 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-28 22:03:35,454 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-28 22:03:35,501 DEBUG: Software modem not available
2011-10-28 22:03:35,501 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-28 22:03:35,504 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:03:35,505 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-28 22:03:35,509 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-28 22:03:35,509 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-28 22:03:35,564 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-28 22:03:35,564 DEBUG: Firmware for DVB cards not available
2011-10-28 22:03:35,564 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-28 22:03:35,566 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-28 22:03:35,570 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-28 22:03:35,570 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-28 22:03:35,570 DEBUG: all custom handlers loaded
2011-10-28 22:03:35,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2011-10-28 22:03:35,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,13A,13B,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2011-10-28 22:03:35,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C7200 series;')
2011-10-28 22:03:35,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:35,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-28 22:03:35,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-28 22:03:35,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2011-10-28 22:03:35,777 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-28 22:03:35,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-28 22:03:35,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:eisa')
2011-10-28 22:03:35,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2011-10-28 22:03:35,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-28 22:03:35,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-28 22:03:35,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-28 22:03:35,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2011-10-28 22:03:35,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:regulatory')
2011-10-28 22:03:35,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-10-28 22:03:35,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2011-10-28 22:03:35,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-28 22:03:35,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2011-10-28 22:03:35,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:35,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00')
2011-10-28 22:03:36,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:36,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:36,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-28 22:03:36,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d000068B8sv0000174Bsd00001482bc03sc00i00')
2011-10-28 22:03:36,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:36,022 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:03:37,280 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:03:36,023 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-28 22:03:37,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-28 22:03:37,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2011-10-28 22:03:37,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-28 22:03:37,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-28 22:03:37,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-28 22:03:37,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2011-10-28 22:03:37,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-28 22:03:37,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-28 22:03:37,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2011-10-28 22:03:37,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0003v060Bp3190e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-10-28 22:03:37,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2011-10-28 22:03:37,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0302:bd08/18/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88T-VEVO/USB3:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-28 22:03:37,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-28 22:03:37,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,B6,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,a20,m4,lsfw')
2011-10-28 22:03:37,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-28 22:03:37,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v060Bp3190d0140dc00dsc00dp00ic03isc01ip01')
2011-10-28 22:03:37,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2011-10-28 22:03:37,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-28 22:03:37,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2011-10-28 22:03:37,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2011-10-28 22:03:37,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-28 22:03:37,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-28 22:03:37,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001002d0000AA58sv0000174Bsd0000AA58bc04sc03i00')
2011-10-28 22:03:37,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-28 22:03:37,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'usb:v060Bp3190d0140dc00dsc00dp00ic03isc00ip00')
2011-10-28 22:03:37,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001814d00000601sv00001814sd00002860bc02sc80i00')
2011-10-28 22:03:37,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2860sta', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-28 22:03:37,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-28 22:03:37,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'input:b0003v060Bp3190e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-28 22:03:37,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x883a98c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2011-10-28 22:03:37,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,13A,13B,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C7200 series;')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:eisa')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:regulatory')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d000068B8sv0000174Bsd00001482bc03sc00i00')
2011-10-28 22:03:37,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0003v060Bp3190e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0302:bd08/18/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88T-VEVO/USB3:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,B6,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,a20,m4,lsfw')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v060Bp3190d0140dc00dsc00dp00ic03isc01ip01')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2011-10-28 22:03:37,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001002d0000AA58sv0000174Bsd0000AA58bc04sc03i00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'usb:v060Bp3190d0140dc00dsc00dp00ic03isc00ip00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001814d00000601sv00001814sd00002860bc02sc80i00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'input:b0003v060Bp3190e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-28 22:03:37,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c4cb0c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-28 22:03:42,792 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:03:42,878 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:03:42,949 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:03:51,353 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:03:55,528 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:03:55,528 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-10-28 22:03:55,529 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-28 22:04:00,969 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:01,021 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,060 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,111 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,174 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,226 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,296 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:04,348 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:10,772 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:10,823 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:11,037 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:04:11,038 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-10-28 22:04:11,038 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-28 22:04:13,899 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:04:13,950 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,128 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,179 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,242 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,294 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,364 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:42,416 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:52,904 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:52,956 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:53,156 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:05:53,156 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-10-28 22:05:53,156 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-28 22:05:56,031 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:05:56,083 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,251 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,302 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,365 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,417 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,489 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:04,540 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:07,275 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:07,327 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:07,475 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:07,527 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:07,962 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:08,014 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:10,042 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:10,093 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:10,291 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:06:10,292 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-10-28 22:06:10,292 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-28 22:06:13,132 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:13,183 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,459 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,510 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,574 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,625 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,696 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:06:15,748 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:09:09,537 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:09:09,588 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:09:15,332 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-28 22:09:15,332 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-10-28 22:09:15,333 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-28 22:09:18,209 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:09:18,260 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:03,801 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:03,854 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:03,918 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:03,971 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:04,043 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-10-28 22:10:04,095 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
```

---

### Post by dcstar on 2011-10-29
> **Mr Watch said:**
> Today I updated my system, as I usually do when the update thing pops up. I saw that there was a kernel update, so I had to restart when things had downloaded. When I restarted my system, I noticed instantly that things were a little slow. Something had deactivated my ATI/AMD propretary FGLRX graphics driver. When I tried to activate it, I was given an error, "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"
I went to look at that, but it's foreign to me. Should I delete my new kernel and boot from my older one, or is there a way to fix this and make my driver activate?
.......

Updates do not all get to a repository at once, the video update is probably not there yet.

Boot from the previous kernel until it arrives.

---

