---
title: "Can't Resize Windows anymore?"
date: 2010-04-10
forum: General Help
---

### Post by fragzem on 2010-04-10
:::Edit:: I kinda got it working again..

However, I can not get the NVIDIA drivers working like they used to.

I dunno if "General" is the right spot for this post anymore... Someone plz help?  The failed install of the nvidia drivers says to look at Jockey.log, so here it is below:
```


2010-04-10 03:28:37,399 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128>
2010-04-10 03:28:37,401 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-10 03:28:37,651 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-10 03:28:37,665 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-10 03:28:37,703 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-10 03:28:37,717 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-10 03:28:37,728 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-10 03:28:37,736 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-10 03:28:38,051 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-10 03:28:38,117 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-10 03:28:38,118 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-10 03:28:38,142 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-10 03:28:38,143 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-10 03:28:38,143 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-10 03:28:38,180 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-10 03:28:38,185 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-10 03:28:38,203 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-10 03:28:38,203 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-10 03:28:38,225 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-10 03:28:38,242 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-10 03:28:38,243 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-10 03:28:38,243 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-10 03:28:38,291 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-10 03:28:38,292 DEBUG: Firmware for DVB cards not available
2010-04-10 03:28:38,293 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-10 03:28:38,304 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-10 03:28:38,305 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-10 03:28:38,305 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-10 03:28:38,306 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-10 03:28:38,328 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-10 03:28:38,331 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-10 03:28:38,349 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 03:28:38,361 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-10 03:28:38,378 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 03:28:38,379 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-10 03:28:38,435 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-10 03:28:38,452 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 03:28:38,453 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-10 03:28:38,478 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-10 03:28:38,532 DEBUG: Software modem not available
2010-04-10 03:28:38,532 DEBUG: all custom handlers loaded
2010-04-10 03:28:38,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0400:')
2010-04-10 03:28:38,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0003v046DpC049e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-10 03:28:38,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:38,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0510:')
2010-04-10 03:28:38,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:device:')
2010-04-10 03:28:38,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000368sv00001462sd00007250bc0Csc05i00')
2010-04-10 03:28:38,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:38,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP170;DES:Canon MP170;CMD:BJL,BJRaster3,BSCCe;')
2010-04-10 03:28:38,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 03:28:38,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:38,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:38,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic08isc06ip50')
2010-04-10 03:28:39,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0003v0000p0000e0004-e0,1,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,ramlsfw')
2010-04-10 03:28:39,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v0846p6A00d0100dc00dsc00dp00ic00isc00ip00')
2010-04-10 03:28:39,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 03:28:39,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 03:28:39,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'platform:regulatory')
2010-04-10 03:28:39,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 03:28:39,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000369sv00001462sd00007250bc05sc00i00')
2010-04-10 03:28:39,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 03:28:39,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 03:28:39,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000360sv00001462sd00007250bc06sc01i00')
2010-04-10 03:28:39,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000370sv00000000sd00000000bc06sc04i01')
2010-04-10 03:28:39,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 03:28:39,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000373sv00001462sd00007250bc06sc80i00')
2010-04-10 03:28:39,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc01ip01')
2010-04-10 03:28:39,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02')
2010-04-10 03:28:39,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 03:28:39,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-10 03:28:39,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 03:28:39,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000371sv00001462sd00007250bc04sc03i00')
2010-04-10 03:28:39,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-10 03:28:39,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 03:28:39,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd08/02/2006:svnMSI:pnMS-7250:pvr1.1:rvnMSI:rnMS-7250:rvr1.1:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-04-10 03:28:39,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 03:28:39,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic07isc01ip02')
2010-04-10 03:28:39,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd00000193sv000010DEsd00000421bc03sc00i00')
2010-04-10 03:28:39,203 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 03:28:39,112 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 03:28:39,207 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-10 03:28:39,208 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 03:28:39,315 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 03:28:39,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,434 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 03:28:39,630 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 03:28:39,535 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 03:28:39,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,k71,72,73,A3,A4,A5,A6,ram4,lsfw')
2010-04-10 03:28:39,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC227d0020dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc01ip00')
2010-04-10 03:28:39,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc02ip00')
2010-04-10 03:28:39,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd0000036Esv00001462sd00007250bc01sc01i8a')
2010-04-10 03:28:39,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2010-04-10 03:28:39,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-10 03:28:39,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd0000036Dsv00001462sd00007250bc0Csc03i20')
2010-04-10 03:28:39,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00icFFisc00ipFF')
2010-04-10 03:28:39,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 03:28:39,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 03:28:39,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 03:28:39,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-10 03:28:39,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'usb:v046DpC223d0020dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000010DEd0000037Fsv00001462sd00007250bc01sc01i85')
2010-04-10 03:28:39,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v00001106d00003044sv00001462sd0000250Dbc0Csc00i10')
2010-04-10 03:28:39,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 03:28:39,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 03:28:39,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 03:28:39,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x28d8128> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0400:')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0003v046DpC049e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0510:')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:device:')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000368sv00001462sd00007250bc0Csc05i00')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP170;DES:Canon MP170;CMD:BJL,BJRaster3,BSCCe;')
2010-04-10 03:28:39,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic08isc06ip50')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0003v0000p0000e0004-e0,1,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,ramlsfw')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v0846p6A00d0100dc00dsc00dp00ic00isc00ip00')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'platform:regulatory')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000369sv00001462sd00007250bc05sc00i00')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 03:28:39,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000360sv00001462sd00007250bc06sc01i00')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000370sv00000000sd00000000bc06sc04i01')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000373sv00001462sd00007250bc06sc80i00')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc01ip01')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000371sv00001462sd00007250bc04sc03i00')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-10 03:28:39,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd08/02/2006:svnMSI:pnMS-7250:pvr1.1:rvnMSI:rnMS-7250:rvr1.1:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic07isc01ip02')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd00000193sv000010DEsd00000421bc03sc00i00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,k71,72,73,A3,A4,A5,A6,ram4,lsfw')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC227d0020dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc01ip00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc02ip00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd0000036Esv00001462sd00007250bc01sc01i8a')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2010-04-10 03:28:39,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd0000036Dsv00001462sd00007250bc0Csc03i20')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00icFFisc00ipFF')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc00ip00')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'usb:v046DpC223d0020dc09dsc00dp00ic09isc00ip00')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000010DEd0000037Fsv00001462sd00007250bc01sc01i85')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v00001106d00003044sv00001462sd0000250Dbc0Csc00i10')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 03:28:39,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 03:28:39,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-04-10 03:28:39,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2eaaab8> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 03:28:39,715 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 03:28:39,716 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 03:28:39,716 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:34:29,739 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20>
2010-04-10 15:34:29,760 DEBUG: reading modalias file /lib/modules/2.6.32-19-generic/modules.alias
2010-04-10 15:34:29,984 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-10 15:34:29,989 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-10 15:34:30,032 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-10 15:34:30,047 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-10 15:34:30,054 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-10 15:34:30,062 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-10 15:34:30,358 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-10 15:34:30,455 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-10 15:34:30,456 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-10 15:34:30,476 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-10 15:34:30,477 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-10 15:34:30,477 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-10 15:34:30,537 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-10 15:34:30,539 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-10 15:34:30,555 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-10 15:34:30,556 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-10 15:34:30,573 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-10 15:34:30,589 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-10 15:34:30,590 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-10 15:34:30,590 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-10 15:34:30,657 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-10 15:34:30,658 DEBUG: Firmware for DVB cards not available
2010-04-10 15:34:30,658 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-10 15:34:30,669 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-10 15:34:30,670 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-10 15:34:30,670 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-10 15:34:30,671 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-10 15:34:30,694 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-10 15:34:30,695 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-10 15:34:30,710 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 15:34:30,720 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-10 15:34:30,736 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 15:34:30,737 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-10 15:34:30,790 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-10 15:34:30,807 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-10 15:34:30,807 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-10 15:34:30,842 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-10 15:34:30,889 DEBUG: Software modem not available
2010-04-10 15:34:30,889 DEBUG: all custom handlers loaded
2010-04-10 15:34:30,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0400:')
2010-04-10 15:34:30,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0003v046DpC049e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-10 15:34:31,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0510:')
2010-04-10 15:34:31,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:device:')
2010-04-10 15:34:31,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000368sv00001462sd00007250bc0Csc05i00')
2010-04-10 15:34:31,622 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,622 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP170;DES:Canon MP170;CMD:BJL,BJRaster3,BSCCe;')
2010-04-10 15:34:31,622 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 15:34:31,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:31,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic08isc06ip50')
2010-04-10 15:34:31,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0003v0000p0000e0004-e0,1,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,ramlsfw')
2010-04-10 15:34:31,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v0846p6A00d0100dc00dsc00dp00ic00isc00ip00')
2010-04-10 15:34:31,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8187', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:31,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 15:34:31,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 15:34:31,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'platform:regulatory')
2010-04-10 15:34:31,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 15:34:31,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000369sv00001462sd00007250bc05sc00i00')
2010-04-10 15:34:31,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:31,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 15:34:31,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 15:34:31,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000360sv00001462sd00007250bc06sc01i00')
2010-04-10 15:34:31,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000370sv00000000sd00000000bc06sc04i01')
2010-04-10 15:34:31,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 15:34:31,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:31,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000373sv00001462sd00007250bc06sc80i00')
2010-04-10 15:34:31,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc01ip01')
2010-04-10 15:34:31,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02')
2010-04-10 15:34:31,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 15:34:31,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-10 15:34:31,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 15:34:31,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000371sv00001462sd00007250bc04sc03i00')
2010-04-10 15:34:31,719 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-10 15:34:31,719 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 15:34:31,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd08/02/2006:svnMSI:pnMS-7250:pvr1.1:rvnMSI:rnMS-7250:rvr1.1:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-04-10 15:34:31,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:31,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 15:34:31,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic07isc01ip02')
2010-04-10 15:34:31,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:31,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd00000193sv000010DEsd00000421bc03sc00i00')
2010-04-10 15:34:32,902 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:34:31,735 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 15:34:32,906 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-10 15:34:32,906 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 15:34:33,005 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 15:34:33,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,101 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 15:34:33,286 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:34:33,195 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-04-10 15:34:33,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,k71,72,73,A3,A4,A5,A6,ram4,lsfw')
2010-04-10 15:34:33,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC227d0020dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:33,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc01ip00')
2010-04-10 15:34:33,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc02ip00')
2010-04-10 15:34:33,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd0000036Esv00001462sd00007250bc01sc01i8a')
2010-04-10 15:34:33,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2010-04-10 15:34:33,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-10 15:34:33,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd0000036Dsv00001462sd00007250bc0Csc03i20')
2010-04-10 15:34:33,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00icFFisc00ipFF')
2010-04-10 15:34:33,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 15:34:33,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:33,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 15:34:33,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 15:34:33,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-10 15:34:33,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'usb:v046DpC223d0020dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:33,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000010DEd0000037Fsv00001462sd00007250bc01sc01i85')
2010-04-10 15:34:33,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v00001106d00003044sv00001462sd0000250Dbc0Csc00i10')
2010-04-10 15:34:33,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 15:34:33,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 15:34:33,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-10 15:34:33,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd5c20> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0400:')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0003v046DpC049e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0510:')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:device:')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000368sv00001462sd00007250bc0Csc05i00')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP170;DES:Canon MP170;CMD:BJL,BJRaster3,BSCCe;')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'platform:pcspkr')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:33,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic08isc06ip50')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0003v0000p0000e0004-e0,1,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,ramlsfw')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v0846p6A00d0100dc00dsc00dp00ic00isc00ip00')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'platform:regulatory')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000369sv00001462sd00007250bc05sc00i00')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-04-10 15:34:33,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000360sv00001462sd00007250bc06sc01i00')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000370sv00000000sd00000000bc06sc04i01')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000373sv00001462sd00007250bc06sc80i00')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc01ip01')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000371sv00001462sd00007250bc04sc03i00')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-10 15:34:33,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080014:bd08/02/2006:svnMSI:pnMS-7250:pvr1.1:rvnMSI:rnMS-7250:rvr1.1:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00ic07isc01ip02')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd00000193sv000010DEsd00000421bc03sc00i00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0003v046DpC226e0110-e0,1,4,k71,72,73,A3,A4,A5,A6,ram4,lsfw')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC227d0020dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc01ip00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v0556p0001d0001dc00dsc00dp00ic01isc02ip00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd0000036Esv00001462sd00007250bc01sc01i8a')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0001v10ECp0883e0001-e0,12,kramls1,2,fw')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-04-10 15:34:33,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd0000036Dsv00001462sd00007250bc0Csc03i20')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v04A9p170Ad0103dc00dsc00dp00icFFisc00ipFF')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC226d0100dc00dsc00dp00ic03isc00ip00')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'usb:v046DpC223d0020dc09dsc00dp00ic09isc00ip00')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000010DEd0000037Fsv00001462sd00007250bc01sc01i85')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v00001106d00003044sv00001462sd0000250Dbc0Csc00i10')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-10 15:34:33,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-10 15:34:33,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-04-10 15:34:33,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x31777a0> about HardwareID('modalias', 'acpi:PNP0501:')
2010-04-10 15:34:33,383 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:34:33,383 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:34:33,383 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:35:11,865 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:35:11,865 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:35:11,865 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2010-04-10 15:37:13,812 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:14,837 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:15,129 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:29,086 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
2010-04-10 15:37:44,440 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:45,482 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:53,157 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:54,861 DEBUG: nvidia_173 is not the alternative in use
2010-04-10 15:37:55,596 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
2010-04-10 15:38:07,917 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:08,046 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:14,830 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:14,941 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:15,221 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:15,367 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:15,642 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:15,792 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:16,075 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:16,223 DEBUG: nvidia_current is not the alternative in use
2010-04-10 15:38:18,779 DEBUG: Shutting down
```

---

