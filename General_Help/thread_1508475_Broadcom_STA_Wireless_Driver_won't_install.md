---
title: "Broadcom STA Wireless Driver won't install"
date: 2010-06-13
forum: General Help
---

### Post by Cthulhu_Dreams on 2010-06-13
It just says "Sorry, Installation of this Driver Failed"

Here is the log:

```
010-06-12 21:35:16,961 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680>
2010-06-12 21:35:16,963 DEBUG: reading modalias file /lib/modules/2.6.32-22-preempt/modules.alias
2010-06-12 21:35:17,093 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-12 21:35:17,109 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-12 21:35:17,154 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-12 21:35:17,164 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-12 21:35:17,176 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-12 21:35:17,188 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-12 21:35:17,208 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-12 21:35:17,441 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-12 21:35:17,474 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-12 21:35:17,524 DEBUG: Software modem not available
2010-06-12 21:35:17,525 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-12 21:35:17,601 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-12 21:35:17,602 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-12 21:35:17,627 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-12 21:35:17,628 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-12 21:35:17,628 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-12 21:35:17,681 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-12 21:35:17,683 DEBUG: Firmware for DVB cards not available
2010-06-12 21:35:17,683 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-12 21:35:17,730 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-12 21:35:17,731 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-12 21:35:17,743 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:35:17,749 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-12 21:35:17,750 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-12 21:35:17,763 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:35:17,764 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-12 21:35:17,771 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-12 21:35:17,772 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-12 21:35:17,784 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:35:17,785 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-12 21:35:17,793 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-12 21:35:17,794 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-12 21:35:17,804 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-12 21:35:17,805 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-12 21:35:17,810 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:35:17,817 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-12 21:35:17,817 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-12 21:35:17,818 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-12 21:35:17,822 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-12 21:35:17,823 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-12 21:35:17,823 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-12 21:35:17,823 DEBUG: all custom handlers loaded
2010-06-12 21:35:17,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 21:35:17,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 21:35:18,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 21:35:18,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 21:35:18,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 21:35:18,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 21:35:18,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:35:18,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 21:35:18,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 21:35:18,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 21:35:18,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 21:35:18,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 21:35:18,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 21:35:18,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 21:35:18,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 21:35:18,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,321 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:35:18,321 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:18,321 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-12 21:35:18,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 21:35:18,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 21:35:18,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 21:35:18,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 21:35:18,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 21:35:18,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 21:35:18,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 21:35:18,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 21:35:18,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 21:35:18,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 21:35:18,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 21:35:18,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 21:35:18,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 21:35:18,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 21:35:18,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 21:35:18,355 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 21:35:18,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 21:35:18,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 21:35:18,361 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:35:18,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 21:35:18,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 21:35:18,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 21:35:18,374 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 21:35:18,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 21:35:18,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 21:35:18,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 21:35:18,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 21:35:18,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 21:35:18,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 21:35:18,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 21:35:18,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:35:18,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:35:18,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 21:35:18,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 21:35:18,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 21:35:18,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 21:35:18,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b2b680> about HardwareID('modalias', 'acpi:device:')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 21:35:18,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 21:35:18,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 21:35:18,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 21:35:18,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 21:35:18,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 21:35:18,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 21:35:18,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30f5a70> about HardwareID('modalias', 'acpi:device:')
2010-06-12 21:35:18,460 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:18,504 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:18,540 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:26,004 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:27,087 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:31,103 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:35:31,104 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-12 21:35:31,152 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:32,705 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:32,724 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:32,752 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:34,161 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:34,382 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:35:34,383 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-12 21:35:34,413 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:37,557 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:37,575 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:37,605 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:35:54,679 DEBUG: Shutting down
2010-06-12 21:36:17,760 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680>
2010-06-12 21:36:17,762 DEBUG: reading modalias file /lib/modules/2.6.32-22-preempt/modules.alias
2010-06-12 21:36:17,872 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-12 21:36:17,872 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-12 21:36:17,901 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-12 21:36:17,903 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-12 21:36:17,906 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-12 21:36:17,907 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-12 21:36:17,910 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-12 21:36:18,146 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-12 21:36:18,157 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-12 21:36:18,168 DEBUG: Software modem not available
2010-06-12 21:36:18,168 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-12 21:36:18,181 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-12 21:36:18,181 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-12 21:36:18,186 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-12 21:36:18,186 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-12 21:36:18,186 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-12 21:36:18,199 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-12 21:36:18,200 DEBUG: Firmware for DVB cards not available
2010-06-12 21:36:18,200 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-12 21:36:18,206 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-12 21:36:18,207 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-12 21:36:18,214 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:36:18,219 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-12 21:36:18,220 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-12 21:36:18,228 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:36:18,228 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-12 21:36:18,232 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-12 21:36:18,233 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-12 21:36:18,240 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 21:36:18,241 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-12 21:36:18,246 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-12 21:36:18,246 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-12 21:36:18,254 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-12 21:36:18,254 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-12 21:36:18,259 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:36:18,266 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-12 21:36:18,267 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-12 21:36:18,267 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-12 21:36:18,272 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-12 21:36:18,272 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-12 21:36:18,272 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-12 21:36:18,272 DEBUG: all custom handlers loaded
2010-06-12 21:36:18,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 21:36:18,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 21:36:18,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 21:36:18,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 21:36:18,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 21:36:18,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 21:36:18,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:36:18,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 21:36:18,662 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 21:36:18,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 21:36:18,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 21:36:18,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 21:36:18,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 21:36:18,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 21:36:18,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 21:36:18,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,716 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:36:18,717 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:36:18,716 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-12 21:36:18,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 21:36:18,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 21:36:18,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 21:36:18,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 21:36:18,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 21:36:18,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 21:36:18,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 21:36:18,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 21:36:18,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 21:36:18,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 21:36:18,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 21:36:18,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 21:36:18,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 21:36:18,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 21:36:18,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 21:36:18,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 21:36:18,756 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 21:36:18,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 21:36:18,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:36:18,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 21:36:18,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 21:36:18,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 21:36:18,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 21:36:18,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 21:36:18,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 21:36:18,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 21:36:18,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 21:36:18,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 21:36:18,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 21:36:18,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 21:36:18,780 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:36:18,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:36:18,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 21:36:18,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 21:36:18,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 21:36:18,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 21:36:18,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 21:36:18,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2853680> about HardwareID('modalias', 'acpi:device:')
2010-06-12 21:36:18,805 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 21:36:18,806 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 21:36:18,807 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 21:36:18,808 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 21:36:18,809 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:36:18,810 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 21:36:18,811 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cea758> about HardwareID('modalias', 'acpi:device:')
2010-06-12 21:36:18,856 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:36:18,894 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:36:18,969 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:36:21,027 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:36:25,662 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 21:36:25,663 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-12 21:36:25,685 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:39:33,955 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:39:33,974 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 21:39:34,007 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:28:14,653 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680>
2010-06-12 22:28:14,670 DEBUG: reading modalias file /lib/modules/2.6.32-22-preempt/modules.alias
2010-06-12 22:28:14,817 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-12 22:28:14,828 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-12 22:28:14,879 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-12 22:28:14,894 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-12 22:28:14,906 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-12 22:28:14,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-12 22:28:14,938 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-12 22:28:15,212 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-12 22:28:15,241 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-12 22:28:15,310 DEBUG: Software modem not available
2010-06-12 22:28:15,310 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-12 22:28:15,387 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-12 22:28:15,388 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-12 22:28:15,402 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-12 22:28:15,402 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-12 22:28:15,402 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-12 22:28:15,457 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-12 22:28:15,457 DEBUG: Firmware for DVB cards not available
2010-06-12 22:28:15,458 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-12 22:28:15,509 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-12 22:28:15,510 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-12 22:28:15,521 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 22:28:15,527 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-12 22:28:15,528 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-12 22:28:15,542 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 22:28:15,542 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-12 22:28:15,550 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-12 22:28:15,550 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-12 22:28:15,561 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-12 22:28:15,561 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-12 22:28:15,566 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-12 22:28:15,567 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-12 22:28:15,575 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-12 22:28:15,575 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-12 22:28:15,645 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 22:28:15,658 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-12 22:28:15,658 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-12 22:28:15,658 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-12 22:28:15,667 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-12 22:28:15,667 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-12 22:28:15,668 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-12 22:28:15,668 DEBUG: all custom handlers loaded
2010-06-12 22:28:15,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 22:28:15,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 22:28:15,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:15,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 22:28:15,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 22:28:15,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 22:28:16,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 22:28:16,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 22:28:16,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 22:28:16,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 22:28:16,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 22:28:16,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 22:28:16,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 22:28:16,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 22:28:16,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 22:28:16,032 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 22:28:16,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,078 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 22:28:16,079 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-12 22:28:16,079 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-12 22:28:16,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 22:28:16,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 22:28:16,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 22:28:16,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 22:28:16,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 22:28:16,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 22:28:16,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 22:28:16,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 22:28:16,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 22:28:16,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 22:28:16,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 22:28:16,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 22:28:16,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 22:28:16,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 22:28:16,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 22:28:16,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 22:28:16,119 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 22:28:16,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 22:28:16,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 22:28:16,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 22:28:16,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 22:28:16,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 22:28:16,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 22:28:16,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 22:28:16,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 22:28:16,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 22:28:16,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 22:28:16,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 22:28:16,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 22:28:16,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 22:28:16,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 22:28:16,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 22:28:16,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 22:28:16,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 22:28:16,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 22:28:16,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 22:28:16,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-06-12 22:28:16,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11d5680> about HardwareID('modalias', 'acpi:device:')
2010-06-12 22:28:16,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'platform:pcspkr')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-12 22:28:16,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-12 22:28:16,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-12 22:28:16,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-12 22:28:16,172 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-12 22:28:16,173 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-12 22:28:16,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-12 22:28:16,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-12 22:28:16,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-12 22:28:16,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-12 22:28:16,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-12 22:28:16,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-12 22:28:16,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-12 22:28:16,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x166c758> about HardwareID('modalias', 'acpi:device:')
2010-06-12 22:28:16,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-12 22:28:16,380 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-12 22:28:16,410 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-12 22:28:18,457 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-12 22:28:21,895 DEBUG: Installing package: bcmwl-kernel-source
2010-06-12 22:28:25,431 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-06-12 22:28:25,750 DEBUG: install progress statusChange dkms 0.000000
2010-06-12 22:28:25,751 DEBUG: install progress statusChange dkms 10.000000
2010-06-12 22:28:26,723 DEBUG: install progress statusChange dkms 20.000000
2010-06-12 22:28:26,772 DEBUG: install progress statusChange dkms 30.000000
2010-06-12 22:28:26,875 DEBUG: install progress statusChange bcmwl-kernel-source 30.000000
2010-06-12 22:28:26,875 DEBUG: install progress statusChange bcmwl-kernel-source 40.000000
2010-06-12 22:28:28,317 DEBUG: install progress statusChange bcmwl-kernel-source 50.000000
2010-06-12 22:28:28,370 DEBUG: install progress statusChange bcmwl-kernel-source 60.000000
2010-06-12 22:28:28,429 DEBUG: install progress statusChange man-db 60.000000
2010-06-12 22:28:29,143 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-06-12 22:28:29,238 DEBUG: install progress statusChange dkms 60.000000
2010-06-12 22:28:29,998 DEBUG: install progress statusChange dkms 70.000000
2010-06-12 22:28:30,047 DEBUG: install progress statusChange dkms 80.000000
2010-06-12 22:28:30,087 DEBUG: install progress statusChange bcmwl-kernel-source 80.000000
2010-06-12 22:28:30,132 DEBUG: install progress statusChange bcmwl-kernel-source 90.000000
2010-06-12 22:28:30,504 DEBUG: install progress statusChange bcmwl-kernel-source 100.000000
2010-06-12 22:28:30,623 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-06-12 22:28:40,550 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 193758 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-22-preempt
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-preempt

2010-06-12 22:28:40,754 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 22:28:40,754 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-12 22:28:40,802 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:29:32,214 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:29:32,238 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:29:32,272 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:30:44,944 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-12 22:30:45,196 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-12 22:30:45,196 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-12 22:30:45,218 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by Sef on 2010-06-13
1) What are your computer specs?

2) How are you trying to install the driver?

---

### Post by techunit on 2010-06-13
Are you connected to the internet via eithernet?

---

### Post by Cthulhu_Dreams on 2010-06-13
Connect via Ethernet, trying to install through "Hardware Drivers", what specs are relevant and how do I go about finding them?  I searched around but as you can imagine the word "specs" turns up a lot of results....  I'm using 10.04  oh...and I remembered this:

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


---

### Post by Cthulhu_Dreams on 2010-06-13
I tried reinstalling it manually through synaptic. The hardware drivers screen says "No Proprietary Drivers are in use on this system" although the Ubuntu Software Centre says bcmwl-kernel-source is installed.  The Network Manager Applet still doesn't give an option for wireless.

---

### Post by JustinR on 2010-06-13
Try:
```
sudo apt-get update
```

Then restart your computer and see if Jockey lists any drivers.

---

### Post by Cthulhu_Dreams on 2010-06-13
Nothing.

---

### Post by Cthulhu_Dreams on 2010-06-17
Bump

---

### Post by Cthulhu_Dreams on 2010-06-19
Bump

---

### Post by Cthulhu_Dreams on 2010-06-20
Bump

---

### Post by Cthulhu_Dreams on 2010-06-21
Bump

---

### Post by bobcollard on 2010-06-21
Solution:
[http://ubuntuforums.org/showthread.php?t=1347483&page=2](http://ubuntuforums.org/showthread.php?t=1347483&page=2)

---

### Post by Cthulhu_Dreams on 2010-06-23
Promising, but it did not work.  Some notes:

> 1. sudo rmmod b43 ssb wl

None of those existed.

> 2. sudo apt-get --purge remove linux-backports-modules-karmic
b43-fwcutter bcmwl-kernel-source

The indicated backports did not exist.  While this is expected since I'm
using Lucid, a quick browse of Synaptic's results for "backports" didn't
reveal any installed backports.

> 
3. Open all the files in /etc/modprobe.d/ and make sure that all of
these lines AREN'T there:

There was a .conf called blacklist-b43 - I deleted it.  Additionally the
blacklist-local.conf contained one line that only blacked listed b43, so
I deleted that too.

> 4. Open /etc/modules and make sure that these aren't
there:

There is no directory called modules in /etc/

Output of terminal upon completion of the remaining steps and restart:

```
adrian@Alpha-60:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for adrian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer
required:
  libkworkspace4 diffstat libgnomepanel2.24-cil
  libplasma-geolocation-interface4 libplasmaclock4 libweather-ion4 quilt
  kdebase-workspace-bin mysql-server-core-5.1 libprocessui4
libprocesscore4
  libsolidcontrol4 libsolidcontrolifaces4 akonadi-server libksgrd4
  libtaskmanager4 mysql-client-core-5.1 module-assistant
  kdebase-workspace-data libplasmagenericshell4 python-configobj
  kdebase-workspace-kgreet-plugins libkephal4
plasma-dataengines-workspace
  ksysguardd libkscreensaver5 libkfontinst4
libplasma-applet-system-monitor4
  kdepim-runtime plasma-widgets-workspace
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/896kB of archives.
After this operation, 2,867kB of additional disk space will be used.
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 194116 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36
+bdcom-0ubuntu3_amd64.deb) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-22-preempt
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-preempt
adrian@Alpha-60:~$ 
```

---

### Post by Cthulhu_Dreams on 2010-06-25
Bump

---

### Post by Amerinidiot1231 on 2010-06-27
I am having the same trouble on my Inspiron 1525; here is the log:

```
2010-06-26 08:55:40,433 DEBUG: Updating repository indexes...
2010-06-26 08:55:40,644 DEBUG: ... fail!
2010-06-26 08:55:56,000 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bc4cec>
2010-06-26 08:55:56,001 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 08:55:56,154 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 08:55:56,164 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 08:55:56,211 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 08:55:56,226 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 08:55:56,237 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 08:55:56,240 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 08:55:56,243 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 08:55:56,268 WARNING: _detect_handlers(): No package repositories available, skipping check
2010-06-26 08:55:56,340 WARNING: new_used_available(): No package repositories available, skipping check
2010-06-26 08:55:56,358 DEBUG: Updating repository indexes...
2010-06-26 08:55:56,492 DEBUG: ... fail!
2010-06-26 08:56:02,224 DEBUG: Shutting down
2010-06-26 12:42:52,238 DEBUG: Updating repository indexes...
2010-06-26 12:42:52,419 DEBUG: ... fail!
2010-06-26 12:43:07,628 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a966ac>
2010-06-26 12:43:07,629 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 12:43:07,785 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 12:43:07,795 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 12:43:07,842 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 12:43:07,856 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 12:43:07,868 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 12:43:07,871 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 12:43:07,874 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 12:43:07,899 WARNING: _detect_handlers(): No package repositories available, skipping check
2010-06-26 12:43:07,943 WARNING: new_used_available(): No package repositories available, skipping check
2010-06-26 12:44:23,414 DEBUG: Updating repository indexes...
2010-06-26 12:44:23,542 DEBUG: ... fail!
2010-06-26 12:44:30,766 DEBUG: Shutting down
2010-06-26 12:46:58,757 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac>
2010-06-26 12:46:58,758 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 12:46:58,886 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 12:46:58,886 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 12:46:58,920 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 12:46:58,921 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 12:46:58,924 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 12:46:58,926 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 12:46:58,929 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 12:47:00,302 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 12:47:00,403 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 12:47:00,406 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 12:47:00,448 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 12:47:00,449 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 12:47:00,456 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:47:00,459 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 12:47:00,460 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 12:47:00,467 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:47:00,467 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 12:47:00,470 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 12:47:00,471 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 12:47:00,478 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:47:00,478 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 12:47:00,508 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 12:47:00,508 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 12:47:00,513 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 12:47:00,513 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 12:47:00,514 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 12:47:00,518 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 12:47:00,519 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 12:47:00,526 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 12:47:00,526 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 12:47:00,531 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 12:47:00,531 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 12:47:00,532 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 12:47:00,532 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 12:47:00,536 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:47:00,543 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 12:47:00,544 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 12:47:00,544 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 12:47:00,552 DEBUG: Could not instantiate Handler subclass __builtin__.SlModem from name SlModem
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package sl-modem-daemon does not exist
2010-06-26 12:47:00,553 DEBUG: all custom handlers loaded
2010-06-26 12:47:00,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:47:00,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:47:01,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:47:01,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:47:01,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:47:01,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:47:01,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:47:01,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'platform:regulatory')
2010-06-26 12:47:01,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:47:01,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:47:01,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:47:01,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:47:01,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:47:01,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:47:01,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:47:01,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:47:01,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:47:01,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:47:01,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:47:01,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:47:01,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:47:01,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:47:01,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:47:01,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:47:01,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:47:01,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:47:01,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:47:01,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:47:01,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:47:01,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:47:01,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:47:01,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:47:01,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:47:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:47:01,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-06-26 12:47:01,186 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-06-26 12:47:01,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:47:01,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:47:01,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:47:01,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:47:01,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:47:01,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:47:01,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:47:01,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:47:01,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:47:01,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:47:01,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:47:01,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:47:01,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:47:01,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:47:01,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:47:01,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:47:01,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:47:01,361 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,361 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:47:01,361 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:47:01,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,415 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:47:01,416 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:47:01,415 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 12:47:01,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:47:01,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:47:01,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:47:01,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x912feac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:47:01,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:47:01,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:47:01,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:47:01,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'platform:regulatory')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:47:01,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:47:01,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:47:01,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:47:01,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:47:01,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:47:01,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:47:01,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:47:01,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:47:01,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:47:01,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:47:01,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:47:01,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9516c0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:47:01,759 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:47:02,208 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:47:04,241 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:47:06,167 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:47:10,933 DEBUG: Installing package: bcmwl-kernel-source
2010-06-26 12:47:16,330 WARNING: Package fetching failed: Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found

2010-06-26 12:48:02,379 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:48:02,619 DEBUG: Installing package: bcmwl-kernel-source
2010-06-26 12:48:15,251 WARNING: Package fetching failed: Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb Disk not found.
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found

2010-06-26 12:48:40,845 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:48:51,241 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:48:51,482 DEBUG: Installing package: bcmwl-kernel-source
2010-06-26 12:48:53,426 WARNING: Package fetching failed: Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb Disk not found.
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found

2010-06-26 12:49:39,135 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:49:39,396 DEBUG: Installing package: bcmwl-kernel-source
2010-06-26 12:51:45,346 WARNING: Package fetching failed: Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb Disk not found.
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found
Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found

2010-06-26 12:53:18,522 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:53:18,936 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:53:24,124 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:53:25,835 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-06-26 12:53:29,952 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:53:29,953 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 12:53:29,977 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:53:37,382 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:53:37,429 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:53:37,619 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:08,981 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:09,315 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:54:09,316 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 12:54:09,349 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:51,531 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:51,554 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:51,695 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:54:54,686 DEBUG: Shutting down
2010-06-26 12:57:18,999 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac>
2010-06-26 12:57:19,019 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 12:57:19,162 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 12:57:19,172 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 12:57:19,220 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 12:57:19,234 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 12:57:19,246 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 12:57:19,248 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 12:57:19,263 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 12:57:19,305 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 12:57:19,395 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 12:57:19,398 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 12:57:19,435 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 12:57:19,436 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 12:57:19,443 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:57:19,446 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 12:57:19,447 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 12:57:19,454 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:57:19,454 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 12:57:19,458 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 12:57:19,458 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 12:57:19,465 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:57:19,466 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 12:57:19,500 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 12:57:19,501 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 12:57:19,505 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 12:57:19,506 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 12:57:19,506 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 12:57:19,510 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 12:57:19,511 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 12:57:19,518 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 12:57:19,518 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 12:57:19,523 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 12:57:19,523 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 12:57:19,524 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 12:57:19,524 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 12:57:19,528 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:57:19,535 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 12:57:19,536 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 12:57:19,536 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 12:57:19,545 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 12:57:19,596 DEBUG: Software modem not available
2010-06-26 12:57:19,596 DEBUG: all custom handlers loaded
2010-06-26 12:57:19,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:57:19,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:57:20,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:57:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:57:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:57:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:57:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:57:20,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:57:20,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:57:20,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:57:20,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:57:20,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:57:20,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:57:20,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:57:20,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:57:20,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:57:20,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:57:20,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:57:20,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:57:20,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:57:20,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:57:20,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:57:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:57:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:57:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:57:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:57:20,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:57:20,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:57:20,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:57:20,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:57:20,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:57:20,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:57:20,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:57:20,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:57:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:57:20,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:57:20,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:57:20,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:57:20,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:57:20,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:57:20,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:57:20,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:57:20,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:57:20,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:57:20,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:57:20,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:57:20,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:57:20,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:57:20,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:57:20,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:57:20,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:57:20,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:57:20,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,398 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:57:20,398 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:20,398 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 12:57:20,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:57:20,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:57:20,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cb2eac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:57:20,400 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:57:20,401 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:57:20,402 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:57:20,403 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:57:20,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:57:20,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:57:20,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:57:20,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:57:20,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9099c0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:57:20,463 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:20,529 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:20,572 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:25,280 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:30,690 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:57:30,690 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 12:57:30,724 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:39,040 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:39,085 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:39,156 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:40,564 DEBUG: handler kmod:wl previously unseen
2010-06-26 12:57:40,564 DEBUG: writing back check cache /var/cache/jockey/check
2010-06-26 12:57:40,565 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:40,584 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:57:41,036 DEBUG: Shutting down
2010-06-26 12:58:03,057 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac>
2010-06-26 12:58:03,058 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 12:58:03,186 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 12:58:03,186 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 12:58:03,219 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 12:58:03,221 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 12:58:03,223 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 12:58:03,225 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 12:58:03,228 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 12:58:03,262 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 12:58:03,274 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 12:58:03,275 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 12:58:03,281 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 12:58:03,282 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 12:58:03,289 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:58:03,293 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 12:58:03,293 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 12:58:03,301 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:58:03,301 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 12:58:03,304 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 12:58:03,305 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 12:58:03,312 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 12:58:03,312 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 12:58:03,325 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 12:58:03,325 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 12:58:03,334 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 12:58:03,335 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 12:58:03,335 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 12:58:03,339 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 12:58:03,340 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 12:58:03,347 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 12:58:03,348 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 12:58:03,352 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 12:58:03,352 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 12:58:03,353 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 12:58:03,353 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 12:58:03,357 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:58:03,364 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 12:58:03,365 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 12:58:03,365 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 12:58:03,374 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 12:58:03,383 DEBUG: Software modem not available
2010-06-26 12:58:03,383 DEBUG: all custom handlers loaded
2010-06-26 12:58:03,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:58:03,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:58:03,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:58:03,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:58:03,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:58:03,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:58:03,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:58:03,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:58:03,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:58:03,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:58:03,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:58:03,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:58:03,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:58:03,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:58:03,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:58:03,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:58:03,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:58:03,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:58:03,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:58:03,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:58:03,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:58:03,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:58:03,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:58:03,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:58:03,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:58:03,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:58:03,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:58:03,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:58:03,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:58:03,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:58:03,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:58:03,878 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:58:03,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:58:03,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:58:03,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:58:03,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:58:03,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:58:03,900 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:58:03,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:58:03,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:58:03,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:58:03,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:58:03,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:58:03,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:58:03,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:58:03,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:58:03,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:58:03,925 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:58:03,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:58:03,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:58:03,941 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:58:03,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:58:03,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,996 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:58:03,997 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:03,996 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 12:58:03,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:58:03,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:58:03,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 12:58:03,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c94eac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:58:03,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 12:58:03,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 12:58:03,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 12:58:03,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 12:58:03,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 12:58:04,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 12:58:04,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 12:58:04,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 12:58:04,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:04,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 12:58:04,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 12:58:04,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907bc0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 12:58:04,097 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:04,119 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:04,157 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:10,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:17,553 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 12:58:17,553 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 12:58:17,573 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:18,626 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:18,648 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:18,687 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 12:58:21,074 DEBUG: Shutting down
2010-06-26 13:01:09,722 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac>
2010-06-26 13:01:09,723 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 13:01:09,845 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 13:01:09,845 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 13:01:09,884 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 13:01:09,885 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 13:01:09,888 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 13:01:09,889 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 13:01:09,893 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 13:01:09,927 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 13:01:09,938 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 13:01:09,940 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 13:01:09,946 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 13:01:09,947 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 13:01:09,954 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:01:09,957 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 13:01:09,958 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 13:01:09,965 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:01:09,965 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 13:01:09,969 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 13:01:09,969 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 13:01:09,977 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:01:09,977 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 13:01:09,989 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 13:01:09,990 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 13:01:09,994 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 13:01:09,995 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 13:01:09,995 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 13:01:09,999 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 13:01:10,000 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 13:01:10,007 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 13:01:10,007 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 13:01:10,012 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 13:01:10,012 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 13:01:10,012 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 13:01:10,013 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 13:01:10,017 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:01:10,024 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 13:01:10,024 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 13:01:10,025 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 13:01:10,033 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 13:01:10,042 DEBUG: Software modem not available
2010-06-26 13:01:10,043 DEBUG: all custom handlers loaded
2010-06-26 13:01:10,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:01:10,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:01:10,449 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:01:10,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:01:10,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:01:10,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:01:10,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:01:10,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:01:10,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:01:10,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:01:10,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:01:10,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:01:10,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:01:10,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:01:10,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:01:10,524 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:01:10,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:01:10,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:01:10,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:01:10,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:01:10,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:01:10,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:01:10,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:01:10,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:01:10,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:01:10,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:01:10,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:01:10,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:01:10,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:01:10,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:01:10,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:01:10,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:01:10,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:01:10,559 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,559 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:01:10,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:01:10,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:01:10,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:01:10,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:01:10,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:01:10,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:01:10,570 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:01:10,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:01:10,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:01:10,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:01:10,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:01:10,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:01:10,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:01:10,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:01:10,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:01:10,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:01:10,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:01:10,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:01:10,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,662 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:01:10,663 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:01:10,663 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 13:01:10,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:01:10,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:01:10,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:01:10,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8856eac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:01:10,664 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:01:10,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:01:10,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:01:10,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:01:10,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:01:10,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:01:10,671 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:01:10,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c3dc0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:01:10,768 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:01:10,808 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:01:10,846 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:01:14,059 DEBUG: Shutting down
2010-06-26 13:04:16,167 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c>
2010-06-26 13:04:16,168 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 13:04:16,296 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 13:04:16,330 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 13:04:16,331 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 13:04:16,334 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 13:04:16,335 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 13:04:16,339 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 13:04:16,373 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 13:04:16,384 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 13:04:16,386 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 13:04:16,392 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 13:04:16,393 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 13:04:16,400 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:04:16,404 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 13:04:16,404 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 13:04:16,411 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:04:16,412 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 13:04:16,415 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 13:04:16,416 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 13:04:16,423 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:04:16,423 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 13:04:16,441 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 13:04:16,441 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 13:04:16,446 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 13:04:16,446 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 13:04:16,446 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 13:04:16,451 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 13:04:16,451 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 13:04:16,459 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 13:04:16,459 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 13:04:16,463 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 13:04:16,464 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 13:04:16,464 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 13:04:16,464 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 13:04:16,468 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:04:16,476 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 13:04:16,476 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 13:04:16,476 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 13:04:16,485 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 13:04:16,494 DEBUG: Software modem not available
2010-06-26 13:04:16,495 DEBUG: all custom handlers loaded
2010-06-26 13:04:16,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:04:16,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:04:16,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:04:16,899 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,899 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:04:16,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:04:16,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:04:16,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:16,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:04:16,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:04:16,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:04:16,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:04:16,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:04:16,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:04:16,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:04:16,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:04:16,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:04:16,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:04:16,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:04:16,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:04:16,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:04:16,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:04:16,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:04:16,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,975 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:04:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:04:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:04:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:04:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:04:16,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:04:16,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:16,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:04:16,982 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:04:16,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:04:16,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:04:16,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:04:16,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:04:16,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:04:16,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:04:16,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:16,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:04:17,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:04:17,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:04:17,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:04:17,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:04:17,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:04:17,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:04:17,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:04:17,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:04:17,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:04:17,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:04:17,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:04:17,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:04:17,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:04:17,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:04:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:04:17,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:04:17,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:04:17,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:04:17,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:04:17,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90ebe6c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:04:17,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:04:17,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:04:17,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:04:17,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:04:17,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:04:17,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x94d37ac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:04:22,085 DEBUG: Shutting down
2010-06-26 13:18:40,774 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac>
2010-06-26 13:18:40,775 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 13:18:40,904 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 13:18:40,904 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 13:18:40,937 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 13:18:40,939 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 13:18:40,941 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 13:18:40,943 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 13:18:40,947 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 13:18:40,980 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 13:18:40,992 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 13:18:40,994 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 13:18:41,000 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 13:18:41,001 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 13:18:41,008 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:18:41,012 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 13:18:41,012 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 13:18:41,019 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:18:41,020 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 13:18:41,023 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 13:18:41,024 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 13:18:41,031 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:18:41,031 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 13:18:41,044 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 13:18:41,044 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 13:18:41,049 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 13:18:41,049 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 13:18:41,050 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 13:18:41,054 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 13:18:41,055 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 13:18:41,062 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 13:18:41,062 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 13:18:41,067 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 13:18:41,067 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 13:18:41,068 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 13:18:41,068 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 13:18:41,072 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:18:41,079 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 13:18:41,080 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 13:18:41,080 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 13:18:41,089 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 13:18:41,102 DEBUG: Software modem not available
2010-06-26 13:18:41,103 DEBUG: all custom handlers loaded
2010-06-26 13:18:41,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:18:41,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:18:41,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:18:41,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:18:41,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:18:41,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:18:41,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:18:41,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:18:41,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:18:41,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:18:41,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:18:41,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:18:41,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:18:41,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:18:41,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:18:41,570 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:18:41,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:18:41,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:18:41,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:18:41,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:18:41,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:18:41,581 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,581 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:18:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:18:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:18:41,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:18:41,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:18:41,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:18:41,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:18:41,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:18:41,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:18:41,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:18:41,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:18:41,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:18:41,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:18:41,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:18:41,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:18:41,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:18:41,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:18:41,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:18:41,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:18:41,615 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:18:41,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,619 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,622 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:18:41,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:18:41,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:18:41,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:18:41,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:18:41,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:18:41,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:18:41,637 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,637 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:18:41,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:18:41,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:18:41,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:18:41,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,702 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:18:41,702 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:18:41,702 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 13:18:41,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:18:41,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:18:41,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:18:41,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8932eac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:18:41,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:18:41,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:18:41,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:18:41,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:18:41,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:18:41,711 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:18:41,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:18:41,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:18:41,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:18:41,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:18:41,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:18:41,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:18:41,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:18:41,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d19c0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:18:41,801 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:18:41,841 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:18:41,879 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:18:44,675 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:18:49,260 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:18:49,261 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 13:18:49,281 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:19:08,454 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:19:08,476 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:19:08,515 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:19:10,119 DEBUG: Shutting down
2010-06-26 13:22:40,239 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac>
2010-06-26 13:22:40,240 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 13:22:40,364 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 13:22:40,364 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 13:22:40,403 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 13:22:40,405 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 13:22:40,407 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 13:22:40,409 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 13:22:40,412 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 13:22:40,447 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 13:22:40,459 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 915, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 100, in name
    self._package_defaults()
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 85, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 173, in package_description
    raise ValueError, 'package %s does not exist' % package
ValueError: package linux-firmware-nonfree does not exist
2010-06-26 13:22:40,460 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 13:22:40,467 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 13:22:40,467 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 13:22:40,475 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:22:40,478 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 13:22:40,479 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 13:22:40,486 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:22:40,487 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 13:22:40,490 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 13:22:40,491 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 13:22:40,498 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 13:22:40,498 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 13:22:40,511 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 13:22:40,511 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 13:22:40,516 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 13:22:40,517 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 13:22:40,517 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 13:22:40,521 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 13:22:40,522 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 13:22:40,529 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 13:22:40,530 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 13:22:40,534 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 13:22:40,535 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 13:22:40,535 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 13:22:40,535 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 13:22:40,539 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:22:40,547 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 13:22:40,547 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 13:22:40,547 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 13:22:40,556 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 13:22:40,565 DEBUG: Software modem not available
2010-06-26 13:22:40,566 DEBUG: all custom handlers loaded
2010-06-26 13:22:40,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:22:40,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:22:40,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:40,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:22:40,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:40,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:40,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:22:40,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:22:40,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:22:40,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:40,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:22:40,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:40,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:22:40,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:22:41,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:22:41,012 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:22:41,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:22:41,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:22:41,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:22:41,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:22:41,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:22:41,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:22:41,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:22:41,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:22:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:22:41,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:22:41,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:22:41,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:22:41,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:22:41,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:22:41,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:22:41,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:22:41,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:22:41,062 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:22:41,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:22:41,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:22:41,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,064 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,064 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:22:41,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:22:41,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:22:41,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:22:41,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:22:41,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:22:41,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:22:41,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:22:41,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:22:41,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:22:41,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:22:41,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:22:41,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:22:41,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:22:41,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:22:41,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:22:41,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:22:41,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:22:41,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:22:41,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:22:41,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:22:41,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,176 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:22:41,177 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:22:41,177 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 13:22:41,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:22:41,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:22:41,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 13:22:41,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d5feac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:22:41,179 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 13:22:41,179 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 13:22:41,179 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 13:22:41,184 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:22:41,185 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 13:22:41,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 13:22:41,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 13:22:41,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 13:22:41,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 13:22:41,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 13:22:41,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 13:22:41,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa146c0c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 13:22:41,264 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:22:41,305 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:22:41,342 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:22:58,142 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:23:02,222 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 13:23:02,223 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 13:23:02,251 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:23:05,094 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:23:05,142 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 13:23:05,234 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 14:01:29,683 DEBUG: Shutting down
2010-06-26 15:41:27,787 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec>
2010-06-26 15:41:27,829 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 15:41:27,969 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 15:41:27,969 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 15:41:28,010 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 15:41:28,011 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 15:41:28,014 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 15:41:28,016 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 15:41:28,020 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 15:41:28,330 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 15:41:28,394 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-26 15:41:28,394 DEBUG: Firmware for DVB cards not available
2010-06-26 15:41:28,394 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 15:41:28,419 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 15:41:28,419 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 15:41:28,427 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 15:41:28,431 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 15:41:28,432 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 15:41:28,440 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 15:41:28,441 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 15:41:28,445 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 15:41:28,445 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 15:41:28,453 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 15:41:28,454 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 15:41:28,496 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 15:41:28,497 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 15:41:28,509 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 15:41:28,509 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 15:41:28,509 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 15:41:28,514 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 15:41:28,514 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 15:41:28,523 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 15:41:28,524 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 15:41:28,528 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 15:41:28,529 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 15:41:28,529 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 15:41:28,529 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 15:41:28,533 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 15:41:28,542 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 15:41:28,542 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 15:41:28,542 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 15:41:28,552 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 15:41:28,613 DEBUG: Software modem not available
2010-06-26 15:41:28,613 DEBUG: all custom handlers loaded
2010-06-26 15:41:28,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 15:41:28,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 15:41:29,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 15:41:29,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 15:41:29,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 15:41:29,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 15:41:29,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 15:41:29,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 15:41:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 15:41:29,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 15:41:29,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 15:41:29,070 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 15:41:29,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 15:41:29,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 15:41:29,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 15:41:29,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'platform:eisa')
2010-06-26 15:41:29,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 15:41:29,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 15:41:29,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 15:41:29,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 15:41:29,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 15:41:29,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:device:')
2010-06-26 15:41:29,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 15:41:29,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 15:41:29,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 15:41:29,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 15:41:29,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 15:41:29,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 15:41:29,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 15:41:29,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 15:41:29,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 15:41:29,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 15:41:29,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 15:41:29,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 15:41:29,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 15:41:29,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 15:41:29,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 15:41:29,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 15:41:29,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 15:41:29,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 15:41:29,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 15:41:29,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 15:41:29,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 15:41:29,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 15:41:29,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 15:41:29,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 15:41:29,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 15:41:29,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 15:41:29,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 15:41:29,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 15:41:29,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 15:41:29,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 15:41:29,236 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,240 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 15:41:29,241 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:41:29,241 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 15:41:29,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 15:41:29,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 15:41:29,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 15:41:29,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87078ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 15:41:29,242 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 15:41:29,243 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 15:41:29,244 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 15:41:29,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 15:41:29,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 15:41:29,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 15:41:29,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 15:41:29,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 15:41:29,250 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 15:41:29,250 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 15:41:29,250 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 15:41:29,250 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8ad3f8c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 15:41:29,309 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:41:29,350 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:41:29,413 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:08,340 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:11,817 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 15:50:11,818 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 15:50:11,857 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:12,218 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 15:50:12,219 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 15:50:12,240 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:13,295 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:13,337 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:13,416 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:13,436 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:16,032 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:16,055 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 15:50:16,096 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:28,106 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c>
2010-06-26 16:07:28,107 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 16:07:28,234 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-26 16:07:28,234 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 16:07:28,274 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 16:07:28,275 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 16:07:28,278 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 16:07:28,279 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 16:07:28,283 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 16:07:28,597 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 16:07:28,610 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-26 16:07:28,611 DEBUG: Firmware for DVB cards not available
2010-06-26 16:07:28,611 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 16:07:28,617 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 16:07:28,618 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 16:07:28,626 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:07:28,630 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 16:07:28,630 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 16:07:28,639 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:07:28,640 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 16:07:28,644 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 16:07:28,644 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 16:07:28,652 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:07:28,653 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 16:07:28,666 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 16:07:28,667 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 16:07:28,677 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 16:07:28,677 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 16:07:28,677 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 16:07:28,683 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 16:07:28,683 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 16:07:28,692 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 16:07:28,692 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 16:07:28,697 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 16:07:28,698 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 16:07:28,698 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 16:07:28,698 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 16:07:28,702 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 16:07:28,711 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 16:07:28,711 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 16:07:28,711 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 16:07:28,721 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 16:07:28,730 DEBUG: Software modem not available
2010-06-26 16:07:28,731 DEBUG: all custom handlers loaded
2010-06-26 16:07:28,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:07:29,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:07:29,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:07:29,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:07:29,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:07:29,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:07:29,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:07:29,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:07:29,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:07:29,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:07:29,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:07:29,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:07:29,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:07:29,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:07:29,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:07:29,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:07:29,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:07:29,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:07:29,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:07:29,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:07:29,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:07:29,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:07:29,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:07:29,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:07:29,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:07:29,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:07:29,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:07:29,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:07:29,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:07:29,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:07:29,231 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:07:29,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:07:29,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:07:29,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:07:29,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:07:29,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:07:29,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:07:29,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:07:29,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:07:29,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:07:29,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:07:29,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:07:29,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:07:29,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:07:29,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:07:29,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:07:29,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:07:29,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:07:29,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:07:29,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:07:29,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:07:29,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:07:29,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,350 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 16:07:29,351 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:29,351 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-26 16:07:29,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:07:29,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:07:29,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:07:29,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f1706c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:07:29,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:07:29,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:07:29,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:07:29,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:07:29,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2acdac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:07:29,410 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:31,304 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:38,617 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 16:07:38,618 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-26 16:07:38,646 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:40,613 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:40,637 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:07:40,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-26 16:08:41,211 DEBUG: Shutting down
2010-06-26 16:09:01,839 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c>
2010-06-26 16:09:01,840 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-06-26 16:09:01,971 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 16:09:02,063 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 16:09:02,064 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 16:09:02,077 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 16:09:02,079 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 16:09:02,092 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 16:09:02,996 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 16:09:03,035 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-26 16:09:03,036 DEBUG: Firmware for DVB cards not available
2010-06-26 16:09:03,036 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 16:09:03,048 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 16:09:03,049 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 16:09:03,067 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:09:03,077 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 16:09:03,078 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 16:09:03,096 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:09:03,096 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 16:09:03,108 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 16:09:03,109 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 16:09:03,127 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:09:03,127 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 16:09:03,159 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 16:09:03,159 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 16:09:03,171 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 16:09:03,171 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 16:09:03,171 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 16:09:03,181 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 16:09:03,182 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 16:09:03,203 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 16:09:03,203 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 16:09:03,211 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 16:09:03,211 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 16:09:03,211 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 16:09:03,212 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 16:09:03,220 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 16:09:03,237 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 16:09:03,237 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 16:09:03,237 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 16:09:03,260 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 16:09:03,279 DEBUG: Software modem not available
2010-06-26 16:09:03,279 DEBUG: all custom handlers loaded
2010-06-26 16:09:03,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:09:03,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:09:04,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:09:04,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:09:04,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:09:04,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:09:04,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:09:04,027 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:09:04,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:09:04,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:09:04,055 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:09:04,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:09:04,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:09:04,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:09:04,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:09:04,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:09:04,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:09:04,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:09:04,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:09:04,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:09:04,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:09:04,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:09:04,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:09:04,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:09:04,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:09:04,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:09:04,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:09:04,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:09:04,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:09:04,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:09:04,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:09:04,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:09:04,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:09:04,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:09:04,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:09:04,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:09:04,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:09:04,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:09:04,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:09:04,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:09:04,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:09:04,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:09:04,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:09:04,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:09:04,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:09:04,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:09:04,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:09:04,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:09:04,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:09:04,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:09:04,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:09:04,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:09:04,218 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:09:04,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:09:04,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:09:04,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ce702c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:09:04,219 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,220 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:09:04,221 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:09:04,222 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:09:04,223 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:09:04,224 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:09:04,225 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:09:04,226 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:09:04,227 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x907d94c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:09:11,857 DEBUG: Shutting down
2010-06-26 16:11:44,551 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c>
2010-06-26 16:11:44,575 DEBUG: reading modalias file /lib/modules/2.6.32-22-generic/modules.alias
2010-06-26 16:11:44,710 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-26 16:11:44,752 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-26 16:11:44,763 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-26 16:11:44,783 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-26 16:11:44,785 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-26 16:11:44,822 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-26 16:11:45,145 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-26 16:11:45,255 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-26 16:11:45,255 DEBUG: Firmware for DVB cards not available
2010-06-26 16:11:45,256 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-26 16:11:45,305 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-26 16:11:45,306 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-26 16:11:45,314 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:11:45,317 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-26 16:11:45,318 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-26 16:11:45,326 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:11:45,327 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-26 16:11:45,331 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-26 16:11:45,332 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-26 16:11:45,339 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-26 16:11:45,340 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-26 16:11:45,400 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-26 16:11:45,400 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-26 16:11:45,414 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-26 16:11:45,415 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-26 16:11:45,415 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-26 16:11:45,420 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-26 16:11:45,420 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-26 16:11:45,428 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-26 16:11:45,429 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-26 16:11:45,433 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-26 16:11:45,434 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-26 16:11:45,434 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-26 16:11:45,434 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-26 16:11:45,439 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-26 16:11:45,447 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-26 16:11:45,447 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-26 16:11:45,447 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-26 16:11:45,457 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-26 16:11:45,487 DEBUG: Software modem not available
2010-06-26 16:11:45,488 DEBUG: all custom handlers loaded
2010-06-26 16:11:45,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:11:45,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:11:46,062 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:11:46,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:11:46,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:11:46,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:11:46,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:11:46,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:11:46,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:11:46,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:11:46,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:11:46,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:11:46,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:11:46,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:11:46,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:11:46,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:11:46,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:11:46,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:11:46,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:11:46,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:11:46,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:11:46,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:11:46,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:11:46,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:11:46,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:11:46,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:11:46,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:11:46,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:11:46,151 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:11:46,151 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:11:46,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:11:46,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:11:46,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:11:46,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:11:46,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:11:46,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:11:46,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:11:46,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:11:46,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:11:46,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:11:46,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:11:46,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:11:46,193 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,193 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:11:46,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:11:46,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:11:46,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:11:46,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:11:46,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:11:46,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:11:46,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:11:46,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:11:46,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:11:46,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:11:46,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:11:46,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-26 16:11:46,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x886d02c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:11:46,264 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd0000022Fbc03sc80i00')
2010-06-26 16:11:46,264 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-26 16:11:46,264 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd0000022Fbc0Csc00i10')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-26 16:11:46,265 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd0000022Fbc08sc05i01')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'platform:dcdbas')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd0000022Fbc02sc00i00')
2010-06-26 16:11:46,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'platform:eisa')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd0000022Fbc06sc00i00')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd0000022Fbc03sc00i00')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:device:')
2010-06-26 16:11:46,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd0000022Fbc06sc01i00')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-06-26 16:11:46,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA16:bd10/16/2008:svnDellInc.:pnInspiron1525:pvr:rvnDellInc.:rn0U990C:rvr:cvnDellInc.:ct8:cvr:')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-26 16:11:46,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd0000022Fbc0Csc05i00')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd0000022Fbc01sc06i01')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd0000022Fbc0Csc03i00')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd0000022Fbc0Csc03i20')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd0000022Fbc04sc03i00')
2010-06-26 16:11:46,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'platform:pcspkr')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd0000022Fbc08sc80i00')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'input:b0003v05A9p2640e0100-e0,1,kD4,ramlsfw')
2010-06-26 16:11:46,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c0394c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-26 16:11:50,481 DEBUG: Shutting down 
```

---

### Post by Amerinidiot1231 on 2010-06-27
That is trying to activate the driver through "Hardware Drivers" with a fresh Ubuntu Studio installation, connected to the Internet via a Ethernet cable.

---

### Post by Amerinidiot1231 on 2010-06-28
So I figured it out, both broadcom wireless drivers are being blacklisted.  I fixed it by removing the blacklist on almost all the broadcom drivers in:

/etc/modprobe.d/

---

### Post by landersohn on 2010-07-02
Got the exact same problem you have, same error message in the jockey.log file.

I fixed it my manually installing a driver the same way I did under karmic. I got source code (I think from broadcom directly), ran make. This generated wl.ko and wl.o and wl.mod.o as output.

Created directory
/lib/modules/kernel/net/wireless/wl
and copied the wl.ko file into this directory.
then created
/lib/modules/linux_restricted_modules/2.6.32.23/wl
and copied the wl.o and wl.mod.o files into this directory.
You need to change the 2.6.32.23 to whatever kernel you are running (I am using 2.6.32-23)

After the copying, run 

depmod
modprobe wl

and voila, the wireless card works. Of course you have to sudo all of the directory creation and copying.
I also ran a depmod -A afterwards to make sure the wl module gets written into the configuration files properly and gets loaded next boot. Not sure whether that is strictly necessary.

I do not understand why the normal activation of this driver does not work. It worked for me from the live CD but not after install. It appears the problem may be related to the directory that needs to be created (/sys/module/wl/drivers). I get an error if I try to create this directory as root manually as well.

---

