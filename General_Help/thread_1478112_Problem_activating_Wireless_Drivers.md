---
title: "Problem activating Wireless Drivers"
date: 2010-05-09
forum: General Help
---

### Post by chaitan64arun on 2010-05-09
Hi All,
I just installed Ubuntu 10.04 netbook on my Dell Inspiron 1545. I have a problem activating the wireless drivers. It would be great, if any one of you could help me. I pasted the log for reference. 
Thanks in advance.

2010-05-10 07:18:30,911 DEBUG: Updating repository indexes...
2010-05-10 07:18:31,120 DEBUG: ... fail!
2010-05-10 07:18:46,573 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x899ad8c>
2010-05-10 07:18:46,574 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-05-10 07:18:46,758 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:18:46,774 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:18:46,815 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:18:46,817 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:18:46,821 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:18:46,824 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:18:46,829 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:18:46,850 WARNING: _detect_handlers(): No package repositories available, skipping check
2010-05-10 07:18:46,889 WARNING: new_used_available(): No package repositories available, skipping check
2010-05-10 07:39:56,852 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c>
2010-05-10 07:39:56,853 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-05-10 07:39:56,975 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:39:56,976 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:39:57,009 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:39:57,011 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:39:57,013 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:39:57,015 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:39:57,018 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:39:57,283 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 07:39:57,360 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 07:39:57,361 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 07:39:57,361 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 07:39:57,361 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 07:39:57,416 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 07:39:57,416 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 07:39:57,437 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,437 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 07:39:57,444 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:39:57,455 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 07:39:57,455 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,455 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 07:39:57,469 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 07:39:57,501 DEBUG: Software modem not available
2010-05-10 07:39:57,502 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 07:39:57,510 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 07:39:57,510 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 07:39:57,517 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,520 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 07:39:57,520 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 07:39:57,527 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,528 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 07:39:57,549 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 07:39:57,551 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 07:39:57,562 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,562 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 07:39:57,604 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 07:39:57,604 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,611 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 07:39:57,611 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,611 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 07:39:57,640 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 07:39:57,641 DEBUG: Firmware for DVB cards not available
2010-05-10 07:39:57,641 DEBUG: all custom handlers loaded
2010-05-10 07:39:57,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:39:57,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:39:58,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:39:58,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:39:58,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:39:58,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:39:58,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi :NP0100:')
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:39:58,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:39:58,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:39:58,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:39:58,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:39:58,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi: )NP0C04:')
2010-05-10 07:39:58,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi: )NP0800:')
2010-05-10 07:39:58,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:39:58,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:39:58,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:39:58,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:39:58,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:39:58,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:39:58,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:39:58,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:39:58,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:39:58,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:39:58,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:39:58,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:39:58,185 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-05-10 07:39:58,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:39:58,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:39:58,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:39:58,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:39:58,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:39:58,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 07:39:58,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:39:58,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:39:58,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:39:58,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:39:58,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:39:58,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:39:58,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:39:58,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,389 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:39:58,389 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:39:58,389 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 07:39:58,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:39:58,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0100:')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0200:')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform::cspkr')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,399 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:39:58,676 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:39:59,049 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:21,508 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:38,712 DEBUG: Installing package: b43-fwcutter
2010-05-10 07:40:38,982 WARNING: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2010-05-10 07:40:46,199 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:48,651 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:48,853 DEBUG: Installing package: bcmwl-kernel-source
2010-05-10 07:40:49,123 WARNING: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2010-05-10 07:52:25,573 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c>
2010-05-10 07:52:25,588 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic-pae/modules.alias
2010-05-10 07:52:25,736 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:52:25,752 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:52:25,786 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:52:25,787 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:52:25,790 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:52:25,792 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:52:25,804 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:52:26,057 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 07:52:26,164 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 07:52:26,164 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 07:52:26,164 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 07:52:26,165 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 07:52:26,234 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 07:52:26,235 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 07:52:26,263 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,263 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 07:52:26,268 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:52:26,275 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 07:52:26,275 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,275 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 07:52:26,285 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 07:52:26,338 DEBUG: Software modem not available
2010-05-10 07:52:26,338 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 07:52:26,344 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 07:52:26,345 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 07:52:26,351 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,354 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 07:52:26,355 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 07:52:26,362 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,362 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 07:52:26,382 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 07:52:26,382 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 07:52:26,389 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,390 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 07:52:26,440 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 07:52:26,440 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,445 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 07:52:26,445 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,445 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 07:52:26,492 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 07:52:26,493 DEBUG: Firmware for DVB cards not available
2010-05-10 07:52:26,493 DEBUG: all custom handlers loaded
2010-05-10 07:52:26,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:52:26,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:52:27,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:52:27,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:52:27,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:52:27,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:52:27,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:52:27,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:52:27,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:52:27,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:52:27,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:52:27,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:52:27,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:52:27,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:52:27,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:52:27,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:52:27,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:52:27,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:52:27,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:52:27,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:52:27,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:52:27,186 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-05-10 07:52:27,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:52:27,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:52:27,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0200:')
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:52:27,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:52:27,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:52:27,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:cspkr')
2010-05-10 07:52:27,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:52:27,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:52:27,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:52:27,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:52:27,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:52:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:52:27,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:52:27,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:52:27,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,407 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:52:27,408 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:27,407 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 07:52:27,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:52:27,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpiNP0200:')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:cspkr')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 07:52:27,690 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:28,088 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:31,961 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:35,656 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:40,050 DEBUG: Installing package: bcmwl-kernel-source
2010-05-10 07:56:20,990 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:56:21,962 DEBUG: install progress statusChange linux-backports-modules-wireless-lucid-generic-pae 0.000000
2010-05-10 07:56:22,463 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:56:22,744 DEBUG: install progress statusChange binutils 0.000000
2010-05-10 07:56:22,745 DEBUG: install progress statusChange binutils 1.724140
2010-05-10 07:56:26,482 DEBUG: install progress statusChange binutils 3.448280
2010-05-10 07:56:26,524 DEBUG: install progress statusChange binutils 5.172410
2010-05-10 07:56:26,604 DEBUG: install progress statusChange gcc-4.4 5.172410
2010-05-10 07:56:26,605 DEBUG: install progress statusChange gcc-4.4 6.896550
2010-05-10 07:56:29,028 DEBUG: install progress statusChange gcc-4.4 8.620690
2010-05-10 07:56:29,091 DEBUG: install progress statusChange gcc-4.4 10.344800
2010-05-10 07:56:29,170 DEBUG: install progress statusChange gcc 10.344800
2010-05-10 07:56:29,171 DEBUG: install progress statusChange gcc 12.069000
2010-05-10 07:56:29,481 DEBUG: install progress statusChange gcc 13.793100
2010-05-10 07:56:29,521 DEBUG: install progress statusChange gcc 15.517200
2010-05-10 07:56:29,614 DEBUG: install progress statusChange dkms 15.517200
2010-05-10 07:56:29,618 DEBUG: install progress statusChange dkms 17.241400
2010-05-10 07:56:30,553 DEBUG: install progress statusChange dkms 18.965500
2010-05-10 07:56:30,593 DEBUG: install progress statusChange dkms 20.689700
2010-05-10 07:56:30,686 DEBUG: install progress statusChange linux-libc-dev 20.689700
2010-05-10 07:56:30,687 DEBUG: install progress statusChange linux-libc-dev 22.413800
2010-05-10 07:56:50,345 DEBUG: install progress statusChange linux-libc-dev 24.137900
2010-05-10 07:56:50,375 DEBUG: install progress statusChange linux-libc-dev 25.862100
2010-05-10 07:56:50,447 DEBUG: install progress statusChange libc-dev-bin 25.862100
2010-05-10 07:56:50,448 DEBUG: install progress statusChange libc-dev-bin 27.586200
2010-05-10 07:56:51,012 DEBUG: install progress statusChange libc-dev-bin 29.310300
2010-05-10 07:56:51,063 DEBUG: install progress statusChange libc-dev-bin 31.034500
2010-05-10 07:56:51,159 DEBUG: install progress statusChange libc6-dev 31.034500
2010-05-10 07:56:51,160 DEBUG: install progress statusChange libc6-dev 32.758600
2010-05-10 07:57:07,355 DEBUG: install progress statusChange libc6-dev 34.482800
2010-05-10 07:57:07,396 DEBUG: install progress statusChange libc6-dev 36.206900
2010-05-10 07:57:07,478 DEBUG: install progress statusChange bcmwl-kernel-source 36.206900
2010-05-10 07:57:07,478 DEBUG: install progress statusChange bcmwl-kernel-source 37.931000
2010-05-10 07:57:08,721 DEBUG: install progress statusChange bcmwl-kernel-source 39.655200
2010-05-10 07:57:08,773 DEBUG: install progress statusChange bcmwl-kernel-source 41.379300
2010-05-10 07:57:08,859 DEBUG: install progress statusChange fakeroot 41.379300
2010-05-10 07:57:08,859 DEBUG: install progress statusChange fakeroot 43.103400
2010-05-10 07:57:10,034 DEBUG: install progress statusChange fakeroot 44.827600
2010-05-10 07:57:10,085 DEBUG: install progress statusChange fakeroot 46.551700
2010-05-10 07:57:10,137 DEBUG: install progress statusChange manpages-dev 46.551700
2010-05-10 07:57:10,138 DEBUG: install progress statusChange manpages-dev 48.275900
2010-05-10 07:57:33,890 DEBUG: install progress statusChange manpages-dev 50.000000
2010-05-10 07:57:33,924 DEBUG: install progress statusChange manpages-dev 51.724100
2010-05-10 07:57:33,981 DEBUG: install progress statusChange patch 51.724100
2010-05-10 07:57:33,981 DEBUG: install progress statusChange patch 53.448300
2010-05-10 07:57:34,489 DEBUG: install progress statusChange patch 55.172400
2010-05-10 07:57:34,529 DEBUG: install progress statusChange patch 56.896600
2010-05-10 07:57:34,566 DEBUG: install progress statusChange man-db 56.896600
2010-05-10 07:57:38,141 DEBUG: install progress statusChange dpkg-exec 56.896600
2010-05-10 07:57:38,218 DEBUG: install progress statusChange binutils 56.896600
2010-05-10 07:57:38,265 DEBUG: install progress statusChange binutils 58.620700
2010-05-10 07:57:38,310 DEBUG: install progress statusChange binutils 60.344800
2010-05-10 07:57:38,423 DEBUG: install progress statusChange gcc-4.4 60.344800
2010-05-10 07:57:38,457 DEBUG: install progress statusChange gcc-4.4 62.069000
2010-05-10 07:57:38,491 DEBUG: install progress statusChange gcc-4.4 63.793100
2010-05-10 07:57:38,525 DEBUG: install progress statusChange gcc 63.793100
2010-05-10 07:57:38,570 DEBUG: install progress statusChange gcc 65.517200
2010-05-10 07:57:38,929 DEBUG: install progress statusChange gcc 67.241400
2010-05-10 07:57:38,975 DEBUG: install progress statusChange dkms 67.241400
2010-05-10 07:57:39,543 DEBUG: install progress statusChange dkms 68.965500
2010-05-10 07:57:39,580 DEBUG: install progress statusChange dkms 70.689700
2010-05-10 07:57:39,634 DEBUG: install progress statusChange linux-libc-dev 70.689700
2010-05-10 07:57:39,679 DEBUG: install progress statusChange linux-libc-dev 72.413800
2010-05-10 07:57:39,713 DEBUG: install progress statusChange linux-libc-dev 74.137900
2010-05-10 07:57:39,747 DEBUG: install progress statusChange libc-dev-bin 74.137900
2010-05-10 07:57:39,792 DEBUG: install progress statusChange libc-dev-bin 75.862100
2010-05-10 07:57:39,826 DEBUG: install progress statusChange libc-dev-bin 77.586200
2010-05-10 07:57:39,860 DEBUG: install progress statusChange libc6-dev 77.586200
2010-05-10 07:57:39,905 DEBUG: install progress statusChange libc6-dev 79.310300
2010-05-10 07:57:39,950 DEBUG: install progress statusChange libc6-dev 81.034500
2010-05-10 07:57:39,984 DEBUG: install progress statusChange bcmwl-kernel-source 81.034500
2010-05-10 07:57:40,029 DEBUG: install progress statusChange bcmwl-kernel-source 82.758600
2010-05-10 07:57:40,360 DEBUG: install progress statusChange bcmwl-kernel-source 84.482800
2010-05-10 07:57:40,468 DEBUG: install progress statusChange fakeroot 84.482800
2010-05-10 07:57:40,513 DEBUG: install progress statusChange fakeroot 86.206900
2010-05-10 07:57:40,650 DEBUG: install progress statusChange fakeroot 87.931000
2010-05-10 07:57:40,694 DEBUG: install progress statusChange manpages-dev 87.931000
2010-05-10 07:57:40,739 DEBUG: install progress statusChange manpages-dev 89.655200
2010-05-10 07:57:40,773 DEBUG: install progress statusChange manpages-dev 91.379300
2010-05-10 07:57:40,807 DEBUG: install progress statusChange patch 91.379300
2010-05-10 07:57:40,852 DEBUG: install progress statusChange patch 93.103400
2010-05-10 07:57:40,886 DEBUG: install progress statusChange patch 94.827600
2010-05-10 07:57:40,920 DEBUG: install progress statusChange libc-bin 94.827600
2010-05-10 07:57:41,180 DEBUG: install progress statusChange initramfs-tools 94.827600
2010-05-10 07:57:48,896 DEBUG: (Reading database ... 122021 files and directories currently installed.)
Removing linux-backports-modules-wireless-lucid-generic-pae ...
Selecting previously deselected package binutils.
(Reading database ... 122019 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.20.1-3ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.32-21.32_i386.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.11.1-0ubuntu7_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.11.1-0ubuntu7_i386.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.23-1_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up binutils (2.20.1-3ubuntu5) ...

Setting up gcc-4.4 (4.4.3-4ubuntu5) ...
Setting up gcc (4:4.4.3-1ubuntu1) ...

Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up linux-libc-dev (2.6.32-21.32) ...
Setting up libc-dev-bin (2.11.1-0ubuntu7) ...
Setting up libc6-dev (2.11.1-0ubuntu7) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up manpages-dev (3.23-1) ...
Setting up patch (2.6-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic-pae

2010-05-10 07:57:49,064 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:57:49,065 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 07:57:49,786 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,050 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,074 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,206 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:16,605 DEBUG: Removing package: bcmwl-kernel-source
2010-05-10 07:58:17,026 DEBUG: remove progress statusChange dpkg-exec 0.000000
2010-05-10 07:58:17,271 DEBUG: remove progress statusChange bcmwl-kernel-source 0.000000
2010-05-10 07:58:17,271 DEBUG: remove progress statusChange bcmwl-kernel-source 33.333300
2010-05-10 07:58:17,536 DEBUG: remove progress statusChange bcmwl-kernel-source 66.666700
2010-05-10 07:58:17,686 DEBUG: remove progress statusChange bcmwl-kernel-source 100.000000
2010-05-10 07:58:17,783 DEBUG: remove progress statusChange initramfs-tools 100.000000
2010-05-10 07:58:23,695 DEBUG: (Reading database ... 125319 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic-pae

2010-05-10 07:58:23,859 DEBUG: Installing package: b43-fwcutter
2010-05-10 07:58:26,362 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:58:26,556 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-05-10 07:58:26,557 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-05-10 07:58:27,243 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-05-10 07:58:27,272 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-05-10 07:58:27,321 DEBUG: install progress statusChange man-db 60.000000
2010-05-10 07:58:28,412 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-05-10 07:58:28,486 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-05-10 07:58:28,542 DEBUG: install progress statusChange b43-fwcutter 80.000000
2010-05-10 07:58:28,849 DEBUG: install progress statusChange b43-fwcutter 100.000000
2010-05-10 07:58:29,050 DEBUG: Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 125271 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a012-1build1_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:012-1build1) ...


2010-05-10 07:58:29,368 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
2010-05-10 07:58:38,785 DEBUG: handler firmware:b43 previously unseen
2010-05-10 07:58:38,856 DEBUG: handler kmod:wl previously unseen
2010-05-10 07:58:38,856 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:38,927 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:39,268 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:39,615 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:39,957 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:40,142 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:51,965 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:52,339 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled

---

### Post by Chame_Wizard on 2010-05-09
> **chaitan64arun said:**
> Hi All,
I just installed Ubuntu 10.04 netbook on my Dell Inspiron 1545. I have a problem activating the wireless drivers. It would be great, if any one of you could help me. I pasted the log for reference. 
Thanks in advance.
```

2010-05-10 07:18:30,911 DEBUG: Updating repository indexes...
2010-05-10 07:18:31,120 DEBUG: ... fail!
2010-05-10 07:18:46,573 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x899ad8c>
2010-05-10 07:18:46,574 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-05-10 07:18:46,758 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:18:46,774 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:18:46,815 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:18:46,817 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:18:46,821 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:18:46,824 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:18:46,829 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:18:46,850 WARNING: _detect_handlers(): No package repositories available, skipping check
2010-05-10 07:18:46,889 WARNING: new_used_available(): No package repositories available, skipping check
2010-05-10 07:39:56,852 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c>
2010-05-10 07:39:56,853 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-05-10 07:39:56,975 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:39:56,976 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:39:57,009 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:39:57,011 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:39:57,013 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:39:57,015 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:39:57,018 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:39:57,283 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 07:39:57,360 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 07:39:57,361 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 07:39:57,361 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 07:39:57,361 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 07:39:57,416 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 07:39:57,416 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 07:39:57,437 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,437 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 07:39:57,444 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:39:57,455 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 07:39:57,455 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,455 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 07:39:57,469 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 07:39:57,501 DEBUG: Software modem not available
2010-05-10 07:39:57,502 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 07:39:57,510 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 07:39:57,510 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 07:39:57,517 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,520 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 07:39:57,520 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 07:39:57,527 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,528 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 07:39:57,549 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 07:39:57,551 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 07:39:57,562 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:39:57,562 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 07:39:57,604 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 07:39:57,604 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,611 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 07:39:57,611 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 07:39:57,611 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 07:39:57,640 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 07:39:57,641 DEBUG: Firmware for DVB cards not available
2010-05-10 07:39:57,641 DEBUG: all custom handlers loaded
2010-05-10 07:39:57,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:39:57,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:39:58,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:39:58,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:39:58,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:39:58,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:39:58,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:39:58,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi :NP0100:')
2010-05-10 07:39:58,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:39:58,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:39:58,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:39:58,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:39:58,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:39:58,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi: )NP0C04:')
2010-05-10 07:39:58,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi: )NP0800:')
2010-05-10 07:39:58,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:39:58,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:39:58,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:39:58,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:39:58,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:39:58,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:39:58,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:39:58,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:39:58,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:39:58,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:39:58,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:39:58,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:39:58,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:39:58,185 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-05-10 07:39:58,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:39:58,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:39:58,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:39:58,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:39:58,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:39:58,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:39:58,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:pcspkr')
2010-05-10 07:39:58,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:39:58,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:39:58,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:39:58,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:39:58,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:39:58,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:39:58,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:39:58,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:39:58,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,389 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:39:58,389 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:39:58,389 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 07:39:58,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:39:58,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x984ad8c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0100:')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:39:58,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:39:58,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:39:58,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:39:58,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0200:')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:39:58,396 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform::cspkr')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:39:58,397 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:39:58,398 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:39:58,399 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bfea4c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:39:58,676 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:39:59,049 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:21,508 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:38,712 DEBUG: Installing package: b43-fwcutter
2010-05-10 07:40:38,982 WARNING: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2010-05-10 07:40:46,199 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:48,651 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:40:48,853 DEBUG: Installing package: bcmwl-kernel-source
2010-05-10 07:40:49,123 WARNING: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2010-05-10 07:52:25,573 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c>
2010-05-10 07:52:25,588 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic-pae/modules.alias
2010-05-10 07:52:25,736 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-05-10 07:52:25,752 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-05-10 07:52:25,786 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-05-10 07:52:25,787 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-05-10 07:52:25,790 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-05-10 07:52:25,792 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-05-10 07:52:25,804 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-05-10 07:52:26,057 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-05-10 07:52:26,164 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-05-10 07:52:26,164 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-05-10 07:52:26,164 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-05-10 07:52:26,165 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-05-10 07:52:26,234 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-05-10 07:52:26,235 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-05-10 07:52:26,263 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,263 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-05-10 07:52:26,268 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:52:26,275 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-05-10 07:52:26,275 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,275 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-05-10 07:52:26,285 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-05-10 07:52:26,338 DEBUG: Software modem not available
2010-05-10 07:52:26,338 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-05-10 07:52:26,344 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-05-10 07:52:26,345 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-05-10 07:52:26,351 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,354 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-10 07:52:26,355 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-05-10 07:52:26,362 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,362 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-05-10 07:52:26,382 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-05-10 07:52:26,382 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-05-10 07:52:26,389 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-05-10 07:52:26,390 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-05-10 07:52:26,440 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-05-10 07:52:26,440 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,445 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-05-10 07:52:26,445 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-05-10 07:52:26,445 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-05-10 07:52:26,492 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-05-10 07:52:26,493 DEBUG: Firmware for DVB cards not available
2010-05-10 07:52:26,493 DEBUG: all custom handlers loaded
2010-05-10 07:52:26,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:52:26,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:52:27,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:52:27,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:52:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:52:27,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:52:27,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:52:27,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 07:52:27,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:52:27,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:52:27,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:52:27,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:52:27,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:52:27,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:52:27,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:52:27,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:52:27,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:52:27,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:52:27,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:52:27,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:52:27,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:52:27,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:52:27,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:52:27,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:52:27,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:52:27,186 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-05-10 07:52:27,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:52:27,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:52:27,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0200:')
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:52:27,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:52:27,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:52:27,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:52:27,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:cspkr')
2010-05-10 07:52:27,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0F13:')
2010-05-10 07:52:27,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:52:27,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:52:27,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:52:27,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:52:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:52:27,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:52:27,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:52:27,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,407 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:52:27,408 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:27,407 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-05-10 07:52:27,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:52:27,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d3ed8c> about HardwareID('modalias', 'acpi:NP0303:')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0B00:')
2010-05-10 07:52:27,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C02:')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:dcdbas')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-05-10 07:52:27,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:eisa')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:regulatory')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C04:')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0800:')
2010-05-10 07:52:27,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:device:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0103:NP0C01:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0000:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:nInspiron1545:vr:rvnDellInc.:rn0J037P:rvr:cvnDellInc.:ct8:cvr:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc02ip00')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:NP0C01:')
2010-05-10 07:52:27,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0C45p63EEd8808dcEFdsc02dp01ic0Eisc01ip00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpiNP0200:')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:cspkr')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-05-10 07:52:27,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0003v0C45p63EEe8808-e0,1,kD4,ramlsfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2010-05-10 07:52:27,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f77cc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-05-10 07:52:27,690 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:28,088 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:31,961 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:35,656 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:52:40,050 DEBUG: Installing package: bcmwl-kernel-source
2010-05-10 07:56:20,990 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:56:21,962 DEBUG: install progress statusChange linux-backports-modules-wireless-lucid-generic-pae 0.000000
2010-05-10 07:56:22,463 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:56:22,744 DEBUG: install progress statusChange binutils 0.000000
2010-05-10 07:56:22,745 DEBUG: install progress statusChange binutils 1.724140
2010-05-10 07:56:26,482 DEBUG: install progress statusChange binutils 3.448280
2010-05-10 07:56:26,524 DEBUG: install progress statusChange binutils 5.172410
2010-05-10 07:56:26,604 DEBUG: install progress statusChange gcc-4.4 5.172410
2010-05-10 07:56:26,605 DEBUG: install progress statusChange gcc-4.4 6.896550
2010-05-10 07:56:29,028 DEBUG: install progress statusChange gcc-4.4 8.620690
2010-05-10 07:56:29,091 DEBUG: install progress statusChange gcc-4.4 10.344800
2010-05-10 07:56:29,170 DEBUG: install progress statusChange gcc 10.344800
2010-05-10 07:56:29,171 DEBUG: install progress statusChange gcc 12.069000
2010-05-10 07:56:29,481 DEBUG: install progress statusChange gcc 13.793100
2010-05-10 07:56:29,521 DEBUG: install progress statusChange gcc 15.517200
2010-05-10 07:56:29,614 DEBUG: install progress statusChange dkms 15.517200
2010-05-10 07:56:29,618 DEBUG: install progress statusChange dkms 17.241400
2010-05-10 07:56:30,553 DEBUG: install progress statusChange dkms 18.965500
2010-05-10 07:56:30,593 DEBUG: install progress statusChange dkms 20.689700
2010-05-10 07:56:30,686 DEBUG: install progress statusChange linux-libc-dev 20.689700
2010-05-10 07:56:30,687 DEBUG: install progress statusChange linux-libc-dev 22.413800
2010-05-10 07:56:50,345 DEBUG: install progress statusChange linux-libc-dev 24.137900
2010-05-10 07:56:50,375 DEBUG: install progress statusChange linux-libc-dev 25.862100
2010-05-10 07:56:50,447 DEBUG: install progress statusChange libc-dev-bin 25.862100
2010-05-10 07:56:50,448 DEBUG: install progress statusChange libc-dev-bin 27.586200
2010-05-10 07:56:51,012 DEBUG: install progress statusChange libc-dev-bin 29.310300
2010-05-10 07:56:51,063 DEBUG: install progress statusChange libc-dev-bin 31.034500
2010-05-10 07:56:51,159 DEBUG: install progress statusChange libc6-dev 31.034500
2010-05-10 07:56:51,160 DEBUG: install progress statusChange libc6-dev 32.758600
2010-05-10 07:57:07,355 DEBUG: install progress statusChange libc6-dev 34.482800
2010-05-10 07:57:07,396 DEBUG: install progress statusChange libc6-dev 36.206900
2010-05-10 07:57:07,478 DEBUG: install progress statusChange bcmwl-kernel-source 36.206900
2010-05-10 07:57:07,478 DEBUG: install progress statusChange bcmwl-kernel-source 37.931000
2010-05-10 07:57:08,721 DEBUG: install progress statusChange bcmwl-kernel-source 39.655200
2010-05-10 07:57:08,773 DEBUG: install progress statusChange bcmwl-kernel-source 41.379300
2010-05-10 07:57:08,859 DEBUG: install progress statusChange fakeroot 41.379300
2010-05-10 07:57:08,859 DEBUG: install progress statusChange fakeroot 43.103400
2010-05-10 07:57:10,034 DEBUG: install progress statusChange fakeroot 44.827600
2010-05-10 07:57:10,085 DEBUG: install progress statusChange fakeroot 46.551700
2010-05-10 07:57:10,137 DEBUG: install progress statusChange manpages-dev 46.551700
2010-05-10 07:57:10,138 DEBUG: install progress statusChange manpages-dev 48.275900
2010-05-10 07:57:33,890 DEBUG: install progress statusChange manpages-dev 50.000000
2010-05-10 07:57:33,924 DEBUG: install progress statusChange manpages-dev 51.724100
2010-05-10 07:57:33,981 DEBUG: install progress statusChange patch 51.724100
2010-05-10 07:57:33,981 DEBUG: install progress statusChange patch 53.448300
2010-05-10 07:57:34,489 DEBUG: install progress statusChange patch 55.172400
2010-05-10 07:57:34,529 DEBUG: install progress statusChange patch 56.896600
2010-05-10 07:57:34,566 DEBUG: install progress statusChange man-db 56.896600
2010-05-10 07:57:38,141 DEBUG: install progress statusChange dpkg-exec 56.896600
2010-05-10 07:57:38,218 DEBUG: install progress statusChange binutils 56.896600
2010-05-10 07:57:38,265 DEBUG: install progress statusChange binutils 58.620700
2010-05-10 07:57:38,310 DEBUG: install progress statusChange binutils 60.344800
2010-05-10 07:57:38,423 DEBUG: install progress statusChange gcc-4.4 60.344800
2010-05-10 07:57:38,457 DEBUG: install progress statusChange gcc-4.4 62.069000
2010-05-10 07:57:38,491 DEBUG: install progress statusChange gcc-4.4 63.793100
2010-05-10 07:57:38,525 DEBUG: install progress statusChange gcc 63.793100
2010-05-10 07:57:38,570 DEBUG: install progress statusChange gcc 65.517200
2010-05-10 07:57:38,929 DEBUG: install progress statusChange gcc 67.241400
2010-05-10 07:57:38,975 DEBUG: install progress statusChange dkms 67.241400
2010-05-10 07:57:39,543 DEBUG: install progress statusChange dkms 68.965500
2010-05-10 07:57:39,580 DEBUG: install progress statusChange dkms 70.689700
2010-05-10 07:57:39,634 DEBUG: install progress statusChange linux-libc-dev 70.689700
2010-05-10 07:57:39,679 DEBUG: install progress statusChange linux-libc-dev 72.413800
2010-05-10 07:57:39,713 DEBUG: install progress statusChange linux-libc-dev 74.137900
2010-05-10 07:57:39,747 DEBUG: install progress statusChange libc-dev-bin 74.137900
2010-05-10 07:57:39,792 DEBUG: install progress statusChange libc-dev-bin 75.862100
2010-05-10 07:57:39,826 DEBUG: install progress statusChange libc-dev-bin 77.586200
2010-05-10 07:57:39,860 DEBUG: install progress statusChange libc6-dev 77.586200
2010-05-10 07:57:39,905 DEBUG: install progress statusChange libc6-dev 79.310300
2010-05-10 07:57:39,950 DEBUG: install progress statusChange libc6-dev 81.034500
2010-05-10 07:57:39,984 DEBUG: install progress statusChange bcmwl-kernel-source 81.034500
2010-05-10 07:57:40,029 DEBUG: install progress statusChange bcmwl-kernel-source 82.758600
2010-05-10 07:57:40,360 DEBUG: install progress statusChange bcmwl-kernel-source 84.482800
2010-05-10 07:57:40,468 DEBUG: install progress statusChange fakeroot 84.482800
2010-05-10 07:57:40,513 DEBUG: install progress statusChange fakeroot 86.206900
2010-05-10 07:57:40,650 DEBUG: install progress statusChange fakeroot 87.931000
2010-05-10 07:57:40,694 DEBUG: install progress statusChange manpages-dev 87.931000
2010-05-10 07:57:40,739 DEBUG: install progress statusChange manpages-dev 89.655200
2010-05-10 07:57:40,773 DEBUG: install progress statusChange manpages-dev 91.379300
2010-05-10 07:57:40,807 DEBUG: install progress statusChange patch 91.379300
2010-05-10 07:57:40,852 DEBUG: install progress statusChange patch 93.103400
2010-05-10 07:57:40,886 DEBUG: install progress statusChange patch 94.827600
2010-05-10 07:57:40,920 DEBUG: install progress statusChange libc-bin 94.827600
2010-05-10 07:57:41,180 DEBUG: install progress statusChange initramfs-tools 94.827600
2010-05-10 07:57:48,896 DEBUG: (Reading database ... 122021 files and directories currently installed.)
Removing linux-backports-modules-wireless-lucid-generic-pae ...
Selecting previously deselected package binutils.
(Reading database ... 122019 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.20.1-3ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.32-21.32_i386.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.11.1-0ubuntu7_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.11.1-0ubuntu7_i386.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.23-1_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up binutils (2.20.1-3ubuntu5) ...

Setting up gcc-4.4 (4.4.3-4ubuntu5) ...
Setting up gcc (4:4.4.3-1ubuntu1) ...

Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up linux-libc-dev (2.6.32-21.32) ...
Setting up libc-dev-bin (2.11.1-0ubuntu7) ...
Setting up libc6-dev (2.11.1-0ubuntu7) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up manpages-dev (3.23-1) ...
Setting up patch (2.6-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic-pae

2010-05-10 07:57:49,064 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-05-10 07:57:49,065 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-05-10 07:57:49,786 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,050 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,074 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:04,206 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-10 07:58:16,605 DEBUG: Removing package: bcmwl-kernel-source
2010-05-10 07:58:17,026 DEBUG: remove progress statusChange dpkg-exec 0.000000
2010-05-10 07:58:17,271 DEBUG: remove progress statusChange bcmwl-kernel-source 0.000000
2010-05-10 07:58:17,271 DEBUG: remove progress statusChange bcmwl-kernel-source 33.333300
2010-05-10 07:58:17,536 DEBUG: remove progress statusChange bcmwl-kernel-source 66.666700
2010-05-10 07:58:17,686 DEBUG: remove progress statusChange bcmwl-kernel-source 100.000000
2010-05-10 07:58:17,783 DEBUG: remove progress statusChange initramfs-tools 100.000000
2010-05-10 07:58:23,695 DEBUG: (Reading database ... 125319 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic-pae

2010-05-10 07:58:23,859 DEBUG: Installing package: b43-fwcutter
2010-05-10 07:58:26,362 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-10 07:58:26,556 DEBUG: install progress statusChange b43-fwcutter 0.000000
2010-05-10 07:58:26,557 DEBUG: install progress statusChange b43-fwcutter 20.000000
2010-05-10 07:58:27,243 DEBUG: install progress statusChange b43-fwcutter 40.000000
2010-05-10 07:58:27,272 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-05-10 07:58:27,321 DEBUG: install progress statusChange man-db 60.000000
2010-05-10 07:58:28,412 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-05-10 07:58:28,486 DEBUG: install progress statusChange b43-fwcutter 60.000000
2010-05-10 07:58:28,542 DEBUG: install progress statusChange b43-fwcutter 80.000000
2010-05-10 07:58:28,849 DEBUG: install progress statusChange b43-fwcutter 100.000000
2010-05-10 07:58:29,050 DEBUG: Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 125271 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a012-1build1_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:012-1build1) ...


2010-05-10 07:58:29,368 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
2010-05-10 07:58:38,785 DEBUG: handler firmware:b43 previously unseen
2010-05-10 07:58:38,856 DEBUG: handler kmod:wl previously unseen
2010-05-10 07:58:38,856 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:38,927 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:39,268 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:39,615 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:39,957 DEBUG: writing back check cache /var/cache/jockey/check
2010-05-10 07:58:40,142 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:51,965 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-05-10 07:58:52,339 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```
Can you check yor configuration 
```
iwconfig
```
Some Broadcom cards are known to have problems.

---

### Post by Pjotr123 on 2010-05-09
Probably easy to solve. Apply this how-to:
[http://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom-chipset](http://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom-chipset)

---

### Post by chaitan64arun on 2010-05-11
This is what i got when i used the command iwconfig :
 lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

