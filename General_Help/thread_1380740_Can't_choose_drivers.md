---
title: "Can't choose drivers"
date: 2010-01-14
forum: General Help
---

### Post by MarcusA on 2010-01-14
Hello..

I upgraded to 9.10 KK, and when I go to 'hardware drivers' and try to activate the recommended drivers (which is named: 'NVIDIA accelerated graphics driver (version current)) I get this error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log


This is in the log file:


[PHP]2010-01-14 06:33:33,135 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac>
2010-01-14 06:33:33,137 DEBUG: reading modalias file /lib/modules/2.6.32-10-generic/modules.alias
2010-01-14 06:33:33,415 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-14 06:33:33,424 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-14 06:33:33,462 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-14 06:33:33,471 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-14 06:33:33,506 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-14 06:33:33,539 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-01-14 06:33:33,565 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-14 06:33:33,693 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:33:33,697 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-14 06:33:33,697 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-14 06:33:33,697 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-14 06:33:33,705 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-14 06:33:33,729 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-14 06:33:33,729 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-14 06:33:33,730 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-14 06:33:33,738 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-14 06:33:33,740 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-14 06:33:33,740 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-14 06:33:33,743 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-14 06:33:33,768 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-14 06:33:33,847 DEBUG: Software modem not available
2010-01-14 06:33:33,847 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-14 06:33:33,945 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-14 06:33:33,946 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-14 06:33:33,972 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-14 06:33:33,973 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-14 06:33:33,973 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-14 06:33:34,012 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-14 06:33:34,032 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-14 06:33:34,050 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-14 06:33:34,051 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-14 06:33:34,118 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-14 06:33:34,119 DEBUG: Firmware for DVB cards not available
2010-01-14 06:33:34,119 DEBUG: all custom handlers loaded
2010-01-14 06:33:34,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 06:33:34,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:34,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:device:')
2010-01-14 06:33:34,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 06:33:34,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:33:34,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'platform:eisa')
2010-01-14 06:33:34,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:33:34,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 06:33:34,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 06:33:34,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 06:33:34,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 06:33:34,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 06:33:34,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:34,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:33:34,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 06:33:34,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 06:33:34,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 06:33:34,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 06:33:34,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 06:33:34,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 06:33:34,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 06:33:34,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:33:34,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 06:33:34,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath5k', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 06:33:34,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:34,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 06:33:34,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:34,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 06:33:35,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 06:33:35,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 06:33:35,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 06:33:35,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 06:33:35,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 06:33:35,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 06:33:35,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tuner', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:33:35,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 06:33:35,238 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 06:33:35,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 06:33:35,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:35,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:33:35,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 06:33:35,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 06:33:35,249 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:33:35,257 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 06:33:35,259 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:33:35,267 DEBUG: got handler xorg:nvidia-current([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 06:33:35,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,275 DEBUG: got handler kmod:nvidia_current([KernelModuleHandler, nonfree, enabled] nvidia_current)
2010-01-14 06:33:35,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 06:33:35,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 06:33:35,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 06:33:35,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 06:33:35,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 06:33:35,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 06:33:35,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 06:33:35,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 06:33:35,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 06:33:35,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:33:35,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa1c36ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 06:33:35,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:device:')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'platform:eisa')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 06:33:35,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:33:35,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 06:33:35,325 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 06:33:35,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 06:33:35,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5483ec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 06:33:47,737 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:33:47,738 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 06:34:16,836 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:34:16,837 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 06:41:35,800 DEBUG: Installing package: nvidia-173
2010-01-14 06:41:47,196 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-01-14 06:42:02,996 DEBUG: install progress statusChange nvidia-173 0.000000
2010-01-14 06:42:02,996 DEBUG: install progress statusChange nvidia-173 20.000000
2010-01-14 06:42:05,323 DEBUG: install progress statusChange nvidia-173 40.000000
2010-01-14 06:42:05,328 DEBUG: install progress statusChange nvidia-173 60.000000
2010-01-14 06:42:05,335 DEBUG: install progress statusChange man-db 60.000000
2010-01-14 06:42:07,270 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-01-14 06:42:07,387 DEBUG: install progress statusChange nvidia-173 60.000000
2010-01-14 06:42:07,536 DEBUG: install progress statusChange nvidia-173 80.000000
2010-01-14 06:42:34,907 DEBUG: install progress statusChange nvidia-173 100.000000
2010-01-14 06:42:34,922 DEBUG: install progress statusChange libc-bin 100.000000
2010-01-14 06:42:35,624 DEBUG: Selecting previously deselected package nvidia-173.
(Reading database ... 246957 files and directories currently installed.)
Unpacking nvidia-173 (from .../nvidia-173_173.14.22-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-173 (173.14.22-0ubuntu3) ...
Loading new nvidia-173-173.14.22 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-10-generic
Building for architecture i686
Building initial module for 2.6.32-10-generic
Done.

nvidia-173.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-10-generic/updates/dkms/

depmod.....

DKMS: install Completed.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2010-01-14 06:42:36,047 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:42:36,047 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 06:42:55,174 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver
2010-01-14 06:45:31,215 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:45:31,216 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 06:48:39,331 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:48:39,331 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 06:55:21,361 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac>
2010-01-14 06:55:21,384 DEBUG: reading modalias file /lib/modules/2.6.32-10-generic/modules.alias
2010-01-14 06:55:21,678 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-14 06:55:21,706 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-14 06:55:21,817 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-14 06:55:21,846 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-14 06:55:22,064 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-14 06:55:22,114 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-01-14 06:55:22,203 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-14 06:55:22,531 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:55:22,536 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-14 06:55:22,537 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-14 06:55:22,537 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-14 06:55:22,561 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-14 06:55:23,257 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-14 06:55:23,257 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-14 06:55:23,258 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-14 06:55:23,376 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-14 06:55:23,378 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-14 06:55:23,378 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-14 06:55:23,378 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-14 06:55:23,522 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-14 06:55:23,603 DEBUG: Software modem not available
2010-01-14 06:55:23,604 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-14 06:55:23,877 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-14 06:55:23,877 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-14 06:55:23,910 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-14 06:55:23,910 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-14 06:55:23,911 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-14 06:55:23,926 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-14 06:55:23,930 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-14 06:55:24,030 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-14 06:55:24,031 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-14 06:55:24,123 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-14 06:55:24,123 DEBUG: Firmware for DVB cards not available
2010-01-14 06:55:24,123 DEBUG: all custom handlers loaded
2010-01-14 06:55:24,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 06:55:24,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:24,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:device:')
2010-01-14 06:55:24,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 06:55:24,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:55:24,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'platform:eisa')
2010-01-14 06:55:24,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:55:24,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 06:55:24,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 06:55:24,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 06:55:24,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 06:55:24,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 06:55:24,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:24,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:55:24,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 06:55:24,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 06:55:24,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 06:55:24,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 06:55:24,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 06:55:24,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 06:55:24,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 06:55:24,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:55:24,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 06:55:24,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath5k', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 06:55:24,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:24,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 06:55:24,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 06:55:24,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 06:55:24,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 06:55:24,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 06:55:24,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 06:55:24,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 06:55:24,874 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 06:55:24,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tuner', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:55:24,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 06:55:24,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:24,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 06:55:24,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 06:55:24,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:24,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:55:24,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 06:55:24,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 06:55:24,918 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:55:25,005 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 06:55:25,016 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:55:25,181 DEBUG: got handler xorg:nvidia-current([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 06:55:25,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,188 DEBUG: got handler kmod:nvidia_173([KernelModuleHandler, nonfree, enabled] nvidia_173)
2010-01-14 06:55:25,195 DEBUG: got handler kmod:nvidia_current([KernelModuleHandler, nonfree, enabled] nvidia_current)
2010-01-14 06:55:25,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 06:55:25,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 06:55:25,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 06:55:25,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 06:55:25,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 06:55:25,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 06:55:25,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 06:55:25,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 06:55:25,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 06:55:25,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 06:55:25,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9b096ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 06:55:25,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 06:55:25,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:25,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:device:')
2010-01-14 06:55:25,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 06:55:25,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:55:25,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'platform:eisa')
2010-01-14 06:55:25,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:55:25,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 06:55:25,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 06:55:25,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 06:55:25,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 06:55:25,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 06:55:25,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:25,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 06:55:25,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 06:55:25,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 06:55:25,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 06:55:25,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 06:55:25,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 06:55:25,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 06:55:25,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 06:55:25,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:55:25,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 06:55:25,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 06:55:25,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:25,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 06:55:25,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 06:55:25,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 06:55:25,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 06:55:25,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 06:55:25,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 06:55:25,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 06:55:25,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 06:55:25,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 06:55:25,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 06:55:25,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 06:55:25,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 06:55:25,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 06:55:25,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 06:55:25,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 06:55:25,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 06:55:25,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 06:55:25,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 06:55:25,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 06:55:25,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 06:55:25,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 06:55:25,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 06:55:25,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 06:55:25,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 06:55:25,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 06:55:25,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9e8e44c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 06:55:42,886 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 06:55:42,887 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-01-14 07:15:47,129 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac>
2010-01-14 07:15:47,130 DEBUG: reading modalias file /lib/modules/2.6.32-10-generic/modules.alias
2010-01-14 07:15:47,331 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-14 07:15:47,331 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-14 07:15:47,365 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-14 07:15:47,366 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-14 07:15:47,368 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-14 07:15:47,370 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-01-14 07:15:47,373 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-14 07:15:47,378 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 07:15:47,379 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-14 07:15:47,379 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-14 07:15:47,380 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-14 07:15:47,382 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-14 07:15:47,389 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-14 07:15:47,389 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-14 07:15:47,389 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-14 07:15:47,393 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-14 07:15:47,393 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-14 07:15:47,393 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-14 07:15:47,393 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-14 07:15:47,401 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-14 07:15:47,408 DEBUG: Software modem not available
2010-01-14 07:15:47,408 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-14 07:15:47,418 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-14 07:15:47,418 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-14 07:15:47,422 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-14 07:15:47,422 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-14 07:15:47,422 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-14 07:15:47,426 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-14 07:15:47,428 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-14 07:15:47,435 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-14 07:15:47,435 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-14 07:15:47,446 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-14 07:15:47,446 DEBUG: Firmware for DVB cards not available
2010-01-14 07:15:47,447 DEBUG: all custom handlers loaded
2010-01-14 07:15:47,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 07:15:47,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:47,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:47,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:device:')
2010-01-14 07:15:47,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 07:15:47,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 07:15:47,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'platform:eisa')
2010-01-14 07:15:47,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 07:15:47,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 07:15:47,952 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:47,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 07:15:47,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 07:15:47,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 07:15:47,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:47,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 07:15:47,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:47,957 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:47,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 07:15:47,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 07:15:47,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 07:15:47,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 07:15:47,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 07:15:47,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 07:15:47,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 07:15:47,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 07:15:47,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 07:15:47,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:47,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 07:15:48,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath5k', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 07:15:48,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 07:15:48,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 07:15:48,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 07:15:48,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 07:15:48,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'saa7134', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 07:15:48,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 07:15:48,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 07:15:48,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 07:15:48,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tuner', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 07:15:48,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 07:15:48,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 07:15:48,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 07:15:48,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 07:15:48,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 07:15:48,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 07:15:48,257 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 07:15:48,265 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 07:15:48,268 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 07:15:48,275 DEBUG: got handler xorg:nvidia-current([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-01-14 07:15:48,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,279 DEBUG: got handler kmod:nvidia_173([KernelModuleHandler, nonfree, enabled] nvidia_173)
2010-01-14 07:15:48,281 DEBUG: got handler kmod:nvidia_current([KernelModuleHandler, nonfree, disabled] nvidia_current)
2010-01-14 07:15:48,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 07:15:48,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,315 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 07:15:48,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 07:15:48,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 07:15:48,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 07:15:48,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 07:15:48,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 07:15:48,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 07:15:48,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a956ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A61bc0Csc05i00')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:device:')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A61bc05sc00i00')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'platform:eisa')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 07:15:48,326 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A61bc06sc80i00')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'platform:regulatory')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A61bc05sc00i00')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A61bc06sc01i00')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00000000sd00000000bc06sc04i01')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-14 07:15:48,327 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip02')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v0000168Cd0000001Bsv000011ADsd00005001bc02sc00i00')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,2,4,14,k71,72,73,74,8E,8F,D3,D6,D7,D9,DA,110,111,112,r0,1,8,am4,lsfw')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v0BDAp0111d1122dc00dsc00dp00ic08isc06ip50')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0003v03F0p0F0Ce0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001131d00007133sv00001043sd00004871bc04sc80i00')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.16:bd08/14/2007:svnHP-Pavilion:pnGJ382AA-B14m8150.be:pvr:rvnECS:rnNettle2:rvr1.0:cvnHewlett-Packard:ct3:cvr:')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2010-01-14 07:15:48,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'i2c:tuner')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A61bc0Csc03i20')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd00000421sv00001043sd0000034Fbc03sc00i00')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v00001106d00003044sv0000103Csd00002A61bc0Csc00i10')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-01-14 07:15:48,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'usb:v03F0p0F0Cd0130dc00dsc00dp00ic03isc01ip01')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A61bc04sc03i00')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'platform:pcspkr')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A61bc01sc01i85')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2010-01-14 07:15:48,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e1a44c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-14 07:16:16,994 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-14 07:16:16,994 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting[/PHP]

So yeah, not sure what to do here. =p

---

### Post by mikewhatever on 2010-01-14
Can you post the output of <uname -r> from a terminal.

---

### Post by MarcusA on 2010-01-14
zoran@zoran-desktop:~$ <uname -r> 
bash: syntax error near unexpected token `newline'



:p not sure if i did that right

---

### Post by Sef on 2010-01-14
> zoran@zoran-desktop:~$ <uname -r> 
bash: syntax error near unexpected token `newline'



:razz: not sure if i did that right

do it without the <>.   just uname -r

---

### Post by MarcusA on 2010-01-14
Sorry, that gives me:

2.6.32-10-generic

---

### Post by mikewhatever on 2010-01-14
> **MarcusA said:**
> Sorry, that gives me:

2.6.32-10-generic

So, how did this kernel end up in an upgrade to Karmic? Karmic's current kernel is 2.6.31-17-generic.

---

### Post by MarcusA on 2010-01-14
Lol I have no clue! I just clicked on alt + f2 and typed update-manager -d then clicked on the 'new' 9.10 version =/

---

### Post by MarcusA on 2010-01-14
I guess I have to install that other kernel using this?

$ sudo apt-get install linux-image-2.6.31-17

I'm still a noob so just checking :p

---

### Post by mikewhatever on 2010-01-14
Funny indeed. It looks like somehow, it got upgraded too far, to the development version of Lucid, perhaps, or I don't know. You can look at **cat /etc/lsb-release** to verify your version.
Anyway, that seems to be the cause of the errors you get from jockey, the Hardware Drivers program in the Admin menu. I honestly don't know how to make it work with newer kernels. You could try downloading a driver from nvidia.com and installing manually.

> **MarcusA said:**
> I guess I have to install that other kernel using this?

$ sudo apt-get install linux-image-2.6.31-17

I'm still a noob so just checking :p

Yeap, wouldn't hurt trying.

---

### Post by MarcusA on 2010-01-14
Holy cow, seems like I have indeed upgraded too far as I have 10.4 :O Well, that explains why I have problems with my ubuntu hahahaha I'm not that good with computers so I don't think I'll try to do anything about it.. :D I guess it's best to wait till the official release of lucid. By then it should all work with all the updates from ubuntu I'd pressume.

---

### Post by Goveynetcom on 2010-01-14
> **MarcusA said:**
> I guess I have to install that other kernel using this?

$ sudo apt-get install linux-image-2.6.31-17

I'm still a noob so just checking :p

So wait, did you upgrade or fresh install? When I upgraded from 9.04 to 9.10 it seemed a little worse then my fresh 9.10 installs (currently all but one working computer in my house is running 9.10).

---

### Post by MarcusA on 2010-01-14
> **Goveynetcom said:**
> So wait, did you upgrade or fresh install? When I upgraded from 9.04 to 9.10 it seemed a little worse then my fresh 9.10 installs (currently all but one working computer in my house is running 9.10).
I did an upgrade from 9.4 (atleast i thought but it is likely that i got confused and actually had 9.10 all along); **cat /etc/lsb-release **verifies that I currently have lucid running instead of 9.10. I know fresh installing ubuntu releases are better then upgrading but that's such a pain to do on every release =(

---

### Post by todak on 2010-01-14
> **MarcusA said:**
> Lol I have no clue! I just clicked on alt + f2 and typed update-manager -d then clicked on the 'new' 9.10 version =/

By typing **-d** after **update-manager**, you told it to look for the next available **distribution**, which, in this case, is 10.04. To use the next distribution before it is officially released, you will quite often have to go to the vendor's website and manually download and install the drivers. Each time there is a kernel update, you will have to install the driver again, until the final release is out and the drivers are available through the  **Hardware Drivers** option. The **-d** option should be used only to upgrade to a newer version of the OS. Without the -d option, you will update only your presently installed system. ;)

---

### Post by MarcusA on 2010-01-14
> **todak said:**
> To use the next distribution before it is officially released, you will quite often have to go to the vendor's website and manually download and install the drivers. Each time there is a kernel update, you will have to install the driver again, until the final release is out and the drivers are available through the  **Hardware Drivers** option. 
:-\" Yeah.. I'll just fiddle around on windows 7 for a few months untill they become available through hardware drivers.. haha It's me own fault :D But thanx for the info, I'll sure remember that for the future!

---

