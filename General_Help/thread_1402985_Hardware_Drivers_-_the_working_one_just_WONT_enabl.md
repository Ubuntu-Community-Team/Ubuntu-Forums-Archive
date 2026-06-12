---
title: "Hardware Drivers - the working one just WONT enable"
date: 2010-02-09
forum: General Help
---

### Post by altjx on 2010-02-09
Okay, I've always had trouble with wireless drivers... but I think I finally may know how to get this one working...

Earlier, I was reinstalling Ubuntu and in the live CD, I went ahead and tried to enable Broadcom STA wireless driver, and THERE, I was able to detect wireless networks... So after the installation finished and I finally got back to my own OS, I tried it and it worked! However, it de-activated the driver (meaning the button changed from Remove to Activate)

Everytime I hit "Activate", it says Downloading and installing driver, then it goes back grey, or disabled rather. How do I activate it permanently? I'm almost 100% my wireless nic will work after enabling it

---

### Post by altjx on 2010-02-09
Ok, I just got an error when trying to activate it. This is what the log file shows

```
2010-02-09 17:16:16,302 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c>
2010-02-09 17:16:16,304 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic-pae/modules.alias
2010-02-09 17:16:16,464 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-09 17:16:16,472 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-09 17:16:16,512 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-09 17:16:16,513 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-09 17:16:16,516 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-09 17:16:16,519 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-09 17:16:16,521 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-09 17:16:16,521 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-09 17:16:16,561 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-09 17:16:16,562 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-09 17:16:16,562 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-09 17:16:16,563 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-09 17:16:18,286 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-09 17:16:18,287 DEBUG: Firmware for DVB cards not available
2010-02-09 17:16:18,288 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-09 17:16:18,351 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-09 17:16:18,352 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-09 17:16:18,352 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-09 17:16:18,352 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-09 17:16:18,355 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-09 17:16:18,356 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-09 17:16:18,363 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-09 17:16:18,363 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-09 17:16:18,367 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-09 17:16:18,372 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-09 17:16:18,373 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-09 17:16:18,373 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-09 17:16:18,414 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-09 17:16:18,414 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-09 17:16:18,423 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-09 17:16:18,424 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-09 17:16:18,424 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-09 17:16:18,444 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-09 17:16:18,480 DEBUG: Software modem not available
2010-02-09 17:16:18,480 DEBUG: all custom handlers loaded
2010-02-09 17:16:18,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:16:18,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:16:18,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:16:18,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:16:18,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:16:18,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:16:18,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:18,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:16:18,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:16:18,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:16:18,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:16:18,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:16:18,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:16:18,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:16:18,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:16:18,925 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:16:18,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:16:18,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:16:18,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:16:18,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:16:18,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:16:18,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:16:18,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:16:18,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:16:18,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:16:18,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:16:18,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:16:18,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:16:18,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:16:18,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:16:18,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:16:18,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:16:18,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:18,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:16:18,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:18,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:16:18,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:16:18,993 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-02-09 17:16:19,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:16:19,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:16:19,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:16:19,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:16:19,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:16:19,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:16:19,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:16:19,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:16:19,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:16:19,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:16:19,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:16:19,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:16:19,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:16:19,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,154 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-09 17:16:19,155 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:16:19,154 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-02-09 17:16:19,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:16:19,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:16:19,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:16:19,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:16:19,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:16:19,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x981854c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:16:19,166 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:16:19,167 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:16:19,168 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:16:19,169 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:16:19,170 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:16:19,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:16:19,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:16:19,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:16:19,171 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b9ec4c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:16:19,175 DEBUG: handler firmware:b43 previously unseen
2010-02-09 17:16:19,227 DEBUG: handler kmod:wl previously unseen
2010-02-09 17:16:19,227 DEBUG: writing back check cache /var/cache/jockey/check
2010-02-09 17:16:19,280 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:16:19,402 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:17:01,577 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:17:01,822 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:17:03,187 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:17:04,429 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:17:06,422 DEBUG: Installing package: bcmwl-kernel-source
2010-02-09 17:17:12,269 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-09 17:17:21,042 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 0.000000
2010-02-09 17:17:21,042 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 6.666670
2010-02-09 17:17:22,163 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 13.333300
2010-02-09 17:17:22,219 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 20.000000
2010-02-09 17:17:22,317 DEBUG: install progress statusChange linux-headers-generic 20.000000
2010-02-09 17:17:22,318 DEBUG: install progress statusChange linux-headers-generic 26.666700
2010-02-09 17:17:22,446 DEBUG: install progress statusChange linux-headers-generic 33.333300
2010-02-09 17:17:22,498 DEBUG: install progress statusChange linux-headers-generic 40.000000
2010-02-09 17:17:22,601 DEBUG: install progress statusChange bcmwl-kernel-source 40.000000
2010-02-09 17:17:22,602 DEBUG: install progress statusChange bcmwl-kernel-source 46.666700
2010-02-09 17:17:22,863 DEBUG: install progress statusChange bcmwl-kernel-source 53.333300
2010-02-09 17:17:22,904 DEBUG: install progress statusChange bcmwl-kernel-source 60.000000
2010-02-09 17:17:23,092 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-02-09 17:17:23,176 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 60.000000
2010-02-09 17:17:23,242 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 66.666700
2010-02-09 17:17:23,737 DEBUG: install progress statusChange linux-headers-2.6.31-19-generic 73.333300
2010-02-09 17:17:23,801 DEBUG: install progress statusChange linux-headers-generic 73.333300
2010-02-09 17:17:23,857 DEBUG: install progress statusChange linux-headers-generic 80.000000
2010-02-09 17:17:23,913 DEBUG: install progress statusChange linux-headers-generic 86.666700
2010-02-09 17:17:23,970 DEBUG: install progress statusChange bcmwl-kernel-source 86.666700
2010-02-09 17:17:24,026 DEBUG: install progress statusChange bcmwl-kernel-source 93.333300
2010-02-09 17:17:43,154 DEBUG: install progress statusChange bcmwl-kernel-source 100.000000
2010-02-09 17:17:43,257 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-02-09 17:17:49,860 DEBUG: Selecting previously deselected package linux-headers-2.6.31-19-generic.
(Reading database ... 128162 files and directories currently installed.)
Unpacking linux-headers-2.6.31-19-generic (from .../linux-headers-2.6.31-19-generic_2.6.31-19.56_i386.deb) ...
Selecting previously deselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_2.6.31.19.32_i386.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ...
Setting up linux-headers-2.6.31-19-generic (2.6.31-19.56) ...
 * Running DKMS auto installation service for kernel 2.6.31-19-generic
   ...done.

Setting up linux-headers-generic (2.6.31.19.32) ...
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
First Installation: checking all kernels...
Directory for kernel 2.6.31-19-generic-pae found in /lib/modules
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic-pae

2010-02-09 17:17:49,861 ERROR: Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

2010-02-09 17:17:50,155 DEBUG: unbind/rebind on driver /sys/module/wl/drivers2010-02-09 17:20:10,168 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c>
2010-02-09 17:20:10,169 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic-pae/modules.alias
2010-02-09 17:20:10,272 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-09 17:20:10,280 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-09 17:20:10,305 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-09 17:20:10,306 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-09 17:20:10,309 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-09 17:20:10,312 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-09 17:20:10,314 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-09 17:20:10,314 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-09 17:20:10,351 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-09 17:20:10,352 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-09 17:20:10,352 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-09 17:20:10,352 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-09 17:20:11,477 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-09 17:20:11,477 DEBUG: Firmware for DVB cards not available
2010-02-09 17:20:11,477 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-09 17:20:11,559 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-09 17:20:11,559 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-09 17:20:11,560 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-09 17:20:11,560 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-09 17:20:11,572 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-09 17:20:11,572 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-09 17:20:11,578 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-09 17:20:11,578 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-09 17:20:11,593 WARNING: modinfo for module wl failed: 
2010-02-09 17:20:11,598 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-09 17:20:11,598 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-09 17:20:11,598 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-09 17:20:11,634 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-09 17:20:11,634 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-09 17:20:11,637 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-09 17:20:11,637 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-09 17:20:11,638 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-09 17:20:11,644 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-09 17:20:11,679 DEBUG: Software modem not available
2010-02-09 17:20:11,679 DEBUG: all custom handlers loaded
2010-02-09 17:20:11,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:20:11,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:20:12,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:20:12,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:20:12,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:20:12,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:20:12,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:20:12,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:20:12,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:20:12,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:20:12,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:20:12,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:20:12,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:20:12,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:20:12,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:20:12,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:20:12,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:20:12,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:20:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:20:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:20:12,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:20:12,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:20:12,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:20:12,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:20:12,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:20:12,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:20:12,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:20:12,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:20:12,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:20:12,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:20:12,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:20:12,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:20:12,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:20:12,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:20:12,155 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-02-09 17:20:12,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:20:12,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:20:12,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:20:12,319 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:20:12,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:20:12,319 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:20:12,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:20:12,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:20:12,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:20:12,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:20:12,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:20:12,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:20:12,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:20:12,372 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,375 WARNING: modinfo for module wl failed: 
2010-02-09 17:20:12,375 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:12,375 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-02-09 17:20:12,378 WARNING: modinfo for module wl failed: 
2010-02-09 17:20:12,378 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:12,378 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-02-09 17:20:12,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:20:12,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:20:12,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:20:12,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:20:12,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:20:12,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x978254c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:20:12,390 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:20:12,391 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:20:12,392 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:20:12,393 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:20:12,394 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:20:12,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:20:12,395 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b0dfac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:20:12,672 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:12,938 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:16,316 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:18,237 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:20,280 WARNING: modinfo for module wl failed: 
2010-02-09 17:20:20,281 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:20:20,295 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:20,441 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:20,455 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:20,590 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:25,897 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:30,824 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:32,696 WARNING: modinfo for module wl failed: 
2010-02-09 17:20:32,696 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:20:32,771 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:32,945 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:32,975 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:20:33,113 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:35,013 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:35,268 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:37,310 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:38,692 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:40,345 WARNING: modinfo for module wl failed: 
2010-02-09 17:22:40,346 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:22:40,354 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:40,493 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:40,504 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:22:40,643 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:51,845 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c>
2010-02-09 17:29:51,867 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic-pae/modules.alias
2010-02-09 17:29:51,966 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-09 17:29:51,974 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-09 17:29:51,998 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-09 17:29:51,999 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-09 17:29:52,002 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-09 17:29:52,005 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-09 17:29:52,007 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-09 17:29:52,007 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-09 17:29:52,045 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-09 17:29:52,046 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-09 17:29:52,046 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-09 17:29:52,046 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-09 17:29:52,293 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-09 17:29:52,294 DEBUG: Firmware for DVB cards not available
2010-02-09 17:29:52,294 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-09 17:29:52,364 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-09 17:29:52,364 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-09 17:29:52,364 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-09 17:29:52,364 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-09 17:29:52,376 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-09 17:29:52,376 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-09 17:29:52,512 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-09 17:29:52,512 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-09 17:29:52,532 WARNING: modinfo for module wl failed: 
2010-02-09 17:29:52,620 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-09 17:29:52,620 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-09 17:29:52,620 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-09 17:29:52,774 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-09 17:29:52,774 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-09 17:29:52,777 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-09 17:29:52,777 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-09 17:29:52,777 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-09 17:29:52,821 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-09 17:29:52,862 DEBUG: Software modem not available
2010-02-09 17:29:52,863 DEBUG: all custom handlers loaded
2010-02-09 17:29:52,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:29:53,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:29:53,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:29:53,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:29:53,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:29:53,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:29:53,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:29:53,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:29:53,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:29:53,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:29:53,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:29:53,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:29:53,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:29:53,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:29:53,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:29:53,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:29:53,373 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:29:53,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:29:53,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:29:53,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:29:53,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:29:53,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:29:53,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:29:53,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:29:53,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:29:53,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:29:53,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:29:53,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:29:53,420 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:29:53,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:29:53,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:29:53,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:29:53,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:29:53,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:29:53,438 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2010-02-09 17:29:53,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:29:53,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:29:53,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:29:53,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:29:53,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:29:53,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:29:53,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:29:53,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:29:53,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:29:53,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:29:53,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:29:53,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:29:53,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:29:53,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,587 WARNING: modinfo for module wl failed: 
2010-02-09 17:29:53,587 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:53,587 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-02-09 17:29:53,589 WARNING: modinfo for module wl failed: 
2010-02-09 17:29:53,590 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:53,590 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-02-09 17:29:53,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:29:53,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:29:53,598 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:29:53,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:29:53,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:29:53,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-09 17:29:53,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x950354c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'platform:dcdbas')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:29:53,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'platform:eisa')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'platform:regulatory')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0F13:')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-09 17:29:53,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA11:bd08/27/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-09 17:29:53,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'ssb:v4243id0812rev0F')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v22B8p41D9d0216dc00dsc00dp00ic08isc06ip50')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-02-09 17:29:53,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'platform:pcspkr')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2010-02-09 17:29:53,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x988efac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-09 17:29:53,964 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:54,206 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:55,280 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:56,436 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:58,077 WARNING: modinfo for module wl failed: 
2010-02-09 17:29:58,078 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:29:58,089 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:58,222 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:58,232 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:29:58,359 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:30:02,473 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:30:04,416 WARNING: modinfo for module wl failed: 
2010-02-09 17:30:04,416 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:30:04,430 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:30:04,563 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:30:04,574 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:30:04,703 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:39:45,095 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:39:45,462 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:05,445 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:06,958 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:08,735 WARNING: modinfo for module wl failed: 
2010-02-09 17:41:08,736 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-09 17:41:08,781 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:13,780 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:13,790 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2010-02-09 17:41:13,938 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```

---

### Post by altjx on 2010-02-09
It seems like it's blacklisted, does anyone know how to unblacklist a driver?

---

### Post by hansdown on 2010-02-09
Hi altjx.

Not sure about the blacklisting, but you can install the broadcom driver here.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Be sure to match the correct one, and have a wired internet working.

---

### Post by altjx on 2010-02-09
I'm a little confused but I have a "0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)"

I'm following the docs but, I think it does say that mines is supported. Gonna continue, eh

EDIT: I really don't want to mess anything up because before I formatted, I've tried this also and it didn't work. I just need to find out why I can't enable the STA Broadcom wireless driver... if i can enable that, i'd get it to work =\

Actually, after going to the bottom and doing what they say in terminal, I go to Hardware Drivers again and I get the same error I got before..

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

---

### Post by andlinux on 2010-02-10
I've almost the same problem but here it is the driver from Nvidia. 
Yesterday I upgraded the backports and after the restart my GUI was gone.

Then I tried to install the nvidia driver again and when it's downloading I get a message that I can see the log in jockey.

```
2010-02-10 12:24:22,184 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518>
2010-02-10 12:24:22,185 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-10 12:24:22,340 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-10 12:24:22,349 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-10 12:24:22,382 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-10 12:24:22,391 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-10 12:24:22,407 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-10 12:24:22,419 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-10 12:24:22,430 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-10 12:24:22,440 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-10 12:24:22,466 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-10 12:24:22,468 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-10 12:24:22,842 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-10 12:24:22,843 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-10 12:24:22,886 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-10 12:24:22,888 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-10 12:24:22,889 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-10 12:24:22,889 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-10 12:24:22,893 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-10 12:24:22,972 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-10 12:24:22,972 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-10 12:24:22,972 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-10 12:24:23,033 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-10 12:24:23,078 DEBUG: Software modem not available
2010-02-10 12:24:23,078 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-10 12:24:23,203 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-10 12:24:23,203 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-10 12:24:23,224 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-10 12:24:23,225 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-10 12:24:23,225 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-10 12:24:23,296 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-10 12:24:23,296 DEBUG: Firmware for DVB cards not available
2010-02-10 12:24:23,296 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-10 12:24:23,310 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-10 12:24:23,311 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-10 12:24:23,311 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-10 12:24:23,311 DEBUG: all custom handlers loaded
2010-02-10 12:24:23,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-10 12:24:23,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-10 12:24:23,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:23,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-10 12:24:23,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:ENE0100:')
2010-02-10 12:24:23,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002937sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:23,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-10 12:24:23,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-10 12:24:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-10 12:24:23,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-10 12:24:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'platform:regulatory')
2010-02-10 12:24:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'platform:coretemp')
2010-02-10 12:24:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002A40sv000014C0sd00000031bc06sc00i00')
2010-02-10 12:24:23,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:23,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v0000168Cd00000024sv000010E9sd00001026bc02sc80i00')
2010-02-10 12:24:23,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:23,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-10 12:24:23,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002929sv000014C0sd00000031bc01sc06i01')
2010-02-10 12:24:23,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-10 12:24:23,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v000010DEd00000649sv000014C0sd00000031bc03sc00i00')
2010-02-10 12:24:24,008 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,011 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-10 12:24:24,084 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-10 12:24:24,087 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-10 12:24:24,118 DEBUG: got handler xorg:nvidia-185([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-10 12:24:24,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d0000293Esv000014C0sd00000031bc04sc03i00')
2010-02-10 12:24:24,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-10 12:24:24,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002930sv000014C0sd00000031bc0Csc05i00')
2010-02-10 12:24:24,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002935sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v0000197Bd00002383sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-10 12:24:24,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'usb:v064EpA115d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-02-10 12:24:24,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0003v064EpA115e0100-e0,1,kD4,ramlsfw')
2010-02-10 12:24:24,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-10 12:24:24,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:SYN070B:SYN0700:SYN0002:PNP0F13:')
2010-02-10 12:24:24,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v0000197Bd00002381sv000014C0sd00000031bc08sc05i01')
2010-02-10 12:24:24,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-10 12:24:24,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:CPL0002:')
2010-02-10 12:24:24,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'dmi:bvnCOMPAL:bvr1.13:bd04/03/2009:svnCOMPAL:pn:pvr:rvnCOMPAL:rnJHL90:rvrREFERENCE:cvnCOMPAL:ct1:cvrN/A:')
2010-02-10 12:24:24,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002936sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-10 12:24:24,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v0000197Bd00002384sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-10 12:24:24,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-10 12:24:24,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'usb:v147Ep1000d0033dc00dsc00dp00icFFisc00ip00')
2010-02-10 12:24:24,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002919sv000014C0sd00000031bc06sc01i00')
2010-02-10 12:24:24,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002939sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d0000293Asv000014C0sd00000031bc0Csc03i20')
2010-02-10 12:24:24,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-02-10 12:24:24,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-10 12:24:24,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002938sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-10 12:24:24,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-10 12:24:24,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-10 12:24:24,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'usb:v064EpA115d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-02-10 12:24:24,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'platform:pcspkr')
2010-02-10 12:24:24,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d00002934sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v00008086d0000293Csv000014C0sd00000031bc0Csc03i20')
2010-02-10 12:24:24,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v0000197Bd00002382sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-10 12:24:24,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-10 12:24:24,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'pci:v000010ECd00008168sv000014C0sd00000031bc02sc00i00')
2010-02-10 12:24:24,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-02-10 12:24:24,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b86518> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:ENE0100:')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002937sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'platform:regulatory')
2010-02-10 12:24:24,174 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'platform:coretemp')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002A40sv000014C0sd00000031bc06sc00i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v0000168Cd00000024sv000010E9sd00001026bc02sc80i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002929sv000014C0sd00000031bc01sc06i01')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v000010DEd00000649sv000014C0sd00000031bc03sc00i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d0000293Esv000014C0sd00000031bc04sc03i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002930sv000014C0sd00000031bc0Csc05i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002935sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v0000197Bd00002383sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'usb:v064EpA115d0100dcEFdsc02dp01ic0Eisc02ip00')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0003v064EpA115e0100-e0,1,kD4,ramlsfw')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:SYN070B:SYN0700:SYN0002:PNP0F13:')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v0000197Bd00002381sv000014C0sd00000031bc08sc05i01')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:CPL0002:')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'dmi:bvnCOMPAL:bvr1.13:bd04/03/2009:svnCOMPAL:pn:pvr:rvnCOMPAL:rnJHL90:rvrREFERENCE:cvnCOMPAL:ct1:cvrN/A:')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002936sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v0000197Bd00002384sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'usb:v147Ep1000d0033dc00dsc00dp00icFFisc00ip00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002919sv000014C0sd00000031bc06sc01i00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002939sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d0000293Asv000014C0sd00000031bc0Csc03i20')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002938sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-10 12:24:24,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'usb:v064EpA115d0100dcEFdsc02dp01ic0Eisc01ip00')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'platform:pcspkr')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d00002934sv000014C0sd00000031bc0Csc03i00')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v00008086d0000293Csv000014C0sd00000031bc0Csc03i20')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v0000197Bd00002382sv000014C0sd00000031bc08sc80i00')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'pci:v000010ECd00008168sv000014C0sd00000031bc02sc00i00')
2010-02-10 12:24:24,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x320aea8> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-10 12:24:33,912 DEBUG: Installing package: linux-headers-2.6.31-20-generic
2010-02-10 12:25:48,316 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-10 12:26:07,213 DEBUG: install progress statusChange linux-headers-2.6.31-20 0.000000
2010-02-10 12:26:07,213 DEBUG: install progress statusChange linux-headers-2.6.31-20 10.000000
2010-02-10 12:26:08,983 DEBUG: install progress statusChange linux-headers-2.6.31-20 20.000000
2010-02-10 12:26:09,072 DEBUG: install progress statusChange linux-headers-2.6.31-20 30.000000
2010-02-10 12:26:09,202 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 30.000000
2010-02-10 12:26:09,204 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 40.000000
2010-02-10 12:26:10,103 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 50.000000
2010-02-10 12:26:10,179 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 60.000000
2010-02-10 12:26:10,398 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-02-10 12:26:10,510 DEBUG: install progress statusChange linux-headers-2.6.31-20 60.000000
2010-02-10 12:26:10,576 DEBUG: install progress statusChange linux-headers-2.6.31-20 70.000000
2010-02-10 12:26:10,646 DEBUG: install progress statusChange linux-headers-2.6.31-20 80.000000
2010-02-10 12:26:10,736 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 80.000000
2010-02-10 12:26:10,806 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 90.000000
2010-02-10 12:26:11,316 DEBUG: install progress statusChange linux-headers-2.6.31-20-generic 100.000000
2010-02-10 12:26:11,730 DEBUG: Selecting previously deselected package linux-headers-2.6.31-20.
(Reading database ... 255927 files and directories currently installed.)
Unpacking linux-headers-2.6.31-20 (from .../linux-headers-2.6.31-20_2.6.31-20.57_all.deb) ...
Selecting previously deselected package linux-headers-2.6.31-20-generic.
Unpacking linux-headers-2.6.31-20-generic (from .../linux-headers-2.6.31-20-generic_2.6.31-20.57_amd64.deb) ...
Setting up linux-headers-2.6.31-20 (2.6.31-20.57) ...
Setting up linux-headers-2.6.31-20-generic (2.6.31-20.57) ...


2010-02-10 12:26:11,731 ERROR: Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

2010-02-10 12:26:12,080 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-10 12:26:12,080 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-02-10 12:26:36,779 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-10 12:26:36,779 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
```

---

### Post by altjx on 2010-02-28
Lol, 2 weeks later I'm back at the same problem again. I should've posted my damn resolution here! Damnit!

---

