---
title: "Proprietary Drivers wth?"
date: 2011-03-03
forum: General Help
---

### Post by Jeaux on 2011-03-03
I installed a new video card.

Computer = Dimension E510
Video card = Sapphire 100252HDMI Radeon HD 4550 

If I go to System > Administration > Hardware Drivers.  I get an interface that has a button called "activate"  So I choose it.  I enter the password and then get this error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

Here's what's in the log.

```
2011-03-03 00:12:26,066 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c>
2011-03-03 00:12:26,068 DEBUG: reading modalias file /lib/modules/2.6.32-29-generic/modules.alias
2011-03-03 00:12:26,334 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-03 00:12:26,341 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-03 00:12:26,400 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-03 00:12:26,413 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-03 00:12:26,418 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-03 00:12:26,423 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-03 00:12:26,429 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-03 00:12:26,846 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-03 00:12:26,942 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 00:12:26,943 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-03 00:12:26,970 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-03 00:12:26,970 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-03 00:12:27,032 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-03 00:12:27,033 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-03 00:12:27,065 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-03 00:12:27,066 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-03 00:12:27,066 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-03 00:12:27,103 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-03 00:12:27,104 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-03 00:12:27,115 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 00:12:27,120 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-03 00:12:27,121 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-03 00:12:27,135 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 00:12:27,135 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-03 00:12:27,158 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-03 00:12:27,158 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-03 00:12:27,170 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 00:12:27,170 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-03 00:12:27,186 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-03 00:12:27,238 DEBUG: Software modem not available
2011-03-03 00:12:27,238 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-03 00:12:27,244 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-03 00:12:27,245 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-03 00:12:27,245 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-03 00:12:27,246 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-03 00:12:27,251 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-03 00:12:27,263 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-03 00:12:27,263 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-03 00:12:27,263 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-03 00:12:27,318 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-03 00:12:27,319 DEBUG: Firmware for DVB cards not available
2011-03-03 00:12:27,319 DEBUG: all custom handlers loaded
2011-03-03 00:12:27,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2011-03-03 00:12:28,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0003v045Ep007De0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-03-03 00:12:28,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-03 00:12:28,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 00:12:28,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001D2bc04sc03i00')
2011-03-03 00:12:28,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'platform:eisa')
2011-03-03 00:12:28,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 00:12:28,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 00:12:28,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 00:12:28,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 00:12:28,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027DCsv00001028sd000001ABbc02sc00i00')
2011-03-03 00:12:28,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e100', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'platform:dcdbas')
2011-03-03 00:12:28,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d00002770sv00001028sd000001D2bc06sc00i00')
2011-03-03 00:12:28,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:28,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:device:')
2011-03-03 00:12:28,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E106bc03sc00i00')
2011-03-03 00:12:28,785 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:28,790 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 00:12:29,634 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:12:28,790 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-03-03 00:12:29,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-03 00:12:29,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 00:12:29,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 00:12:29,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-03-03 00:12:29,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-03-03 00:12:29,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2011-03-03 00:12:29,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd03/31/2006:svnDellInc.:pnDellDM051:pvr:rvnDellInc.:rn0HJ054:rvr:cvnDellInc.:ct6:cvr:')
2011-03-03 00:12:29,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 00:12:29,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0003v413Cp2003e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 00:12:29,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'usb:v413Cp2003d0301dc00dsc00dp00ic03isc01ip01')
2011-03-03 00:12:29,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'usb:v045Ep007Dd0200dc00dsc00dp00ic03isc01ip02')
2011-03-03 00:12:29,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 00:12:29,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 00:12:29,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00001002d00004D53sv00001028sd0000A503bc04sc80i00')
2011-03-03 00:12:29,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001D2bc0Csc05i00')
2011-03-03 00:12:29,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001D2bc0Csc03i20')
2011-03-03 00:12:29,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-03-03 00:12:29,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 00:12:29,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 00:12:29,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01')
2011-03-03 00:12:29,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 00:12:29,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 00:12:29,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00000000sd00000000bc06sc01i00')
2011-03-03 00:12:29,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-03-03 00:12:29,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 00:12:29,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d86a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 00:12:29,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2011-03-03 00:12:29,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0003v045Ep007De0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-03-03 00:12:29,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-03 00:12:29,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 00:12:29,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001D2bc04sc03i00')
2011-03-03 00:12:29,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'platform:eisa')
2011-03-03 00:12:29,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027DCsv00001028sd000001ABbc02sc00i00')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'platform:dcdbas')
2011-03-03 00:12:29,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d00002770sv00001028sd000001D2bc06sc00i00')
2011-03-03 00:12:29,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:device:')
2011-03-03 00:12:29,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E106bc03sc00i00')
2011-03-03 00:12:29,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-03 00:12:29,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-03-03 00:12:29,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001D2bc0Csc03i00')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd03/31/2006:svnDellInc.:pnDellDM051:pvr:rvnDellInc.:rn0HJ054:rvr:cvnDellInc.:ct6:cvr:')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0003v413Cp2003e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'usb:v413Cp2003d0301dc00dsc00dp00ic03isc01ip01')
2011-03-03 00:12:29,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'usb:v045Ep007Dd0200dc00dsc00dp00ic03isc01ip02')
2011-03-03 00:12:29,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 00:12:29,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 00:12:29,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00001002d00004D53sv00001028sd0000A503bc04sc80i00')
2011-03-03 00:12:29,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001D2bc0Csc05i00')
2011-03-03 00:12:29,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001D2bc0Csc03i20')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 00:12:29,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 00:12:29,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00000000sd00000000bc06sc01i00')
2011-03-03 00:12:29,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-03-03 00:12:29,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x91aff2c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 00:12:30,140 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:12:30,405 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:12:30,647 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:17:04,896 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:17:11,267 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 00:17:11,268 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-03-03 00:17:11,268 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-03-03 00:17:22,319 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 00:17:22,491 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

```






Can someone plz tell me what is going on? and how to correct this error.

Many thx,
Joe

---

