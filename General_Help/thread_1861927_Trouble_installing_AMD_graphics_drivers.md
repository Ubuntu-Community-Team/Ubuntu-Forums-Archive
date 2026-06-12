---
title: "Trouble installing AMD graphics drivers"
date: 2011-10-16
forum: General Help
---

### Post by Raven777 on 2011-10-16
Hello, I am new to Ubuntu and I'm having trouble installing my proprietary graphics drivers on version 11.10 - It basically tells me that the installation failed and that I should check the jockey.log file.

This is what it says in my jockey.log file:
```
2011-10-15 20:43:30,877 DEBUG: Updating repository indexes...
2011-10-15 20:43:59,722 DEBUG: ... success
2011-10-15 20:44:00,173 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c>
2011-10-15 20:44:03,791 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-10-15 20:44:04,070 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-15 20:44:04,116 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-15 20:44:04,201 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-15 20:44:04,238 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-15 20:44:04,366 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-15 20:44:04,377 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-15 20:44:04,377 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:04,622 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:44:04,632 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-15 20:44:04,643 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-15 20:44:04,644 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:04,718 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:44:04,724 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-15 20:44:04,731 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-15 20:44:04,732 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:04,788 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:44:04,789 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-15 20:44:04,828 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-15 20:44:04,839 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-15 20:44:04,840 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:04,913 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:44:04,919 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-15 20:44:04,926 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-15 20:44:04,926 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:04,996 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:44:05,002 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-15 20:44:05,009 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-15 20:44:05,009 DEBUG: nvidia.available: falling back to default
2011-10-15 20:44:05,098 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:44:05,098 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-15 20:44:05,137 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-15 20:44:05,138 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-15 20:44:05,190 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-15 20:44:05,191 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-15 20:44:05,248 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-15 20:44:05,297 DEBUG: Software modem not available
2011-10-15 20:44:05,298 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-15 20:44:05,310 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-15 20:44:05,363 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-15 20:44:05,364 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-15 20:44:05,364 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-15 20:44:05,379 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 20:44:05,390 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-15 20:44:05,391 DEBUG: fglrx.available: falling back to default
2011-10-15 20:44:05,487 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:44:05,497 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-15 20:44:05,507 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-15 20:44:05,508 DEBUG: fglrx.available: falling back to default
2011-10-15 20:44:05,610 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-15 20:44:05,611 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-15 20:44:05,707 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-15 20:44:05,708 DEBUG: Firmware for DVB cards not available
2011-10-15 20:44:05,709 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-15 20:44:05,718 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-15 20:44:05,720 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-15 20:44:05,720 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-15 20:44:05,721 DEBUG: all custom handlers loaded
2011-10-15 20:44:05,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00001314sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:44:06,360 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:44:06,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2011-10-15 20:44:06,585 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:06,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:06,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:06,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 20:44:06,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 20:44:06,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001969d00001063sv0000104Dsd00009082bc02sc00i00')
2011-10-15 20:44:06,624 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-10-15 20:44:06,624 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 20:44:06,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 20:44:06,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:06,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 20:44:06,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-15 20:44:06,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,628 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-15 20:44:06,628 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:44:06,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:06,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-15 20:44:06,673 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:06,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 20:44:06,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2011-10-15 20:44:06,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 20:44:06,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:06,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-10-15 20:44:06,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 20:44:06,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000104Dsd00009082bc0Csc03i20')
2011-10-15 20:44:06,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:sony-laptop')
2011-10-15 20:44:06,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-10-15 20:44:06,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001510sv0000104Dsd00009082bc06sc00i00')
2011-10-15 20:44:06,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 20:44:06,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v0BDAp0186d8687dc00dsc00dp00ic08isc06ip50')
2011-10-15 20:44:06,713 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-10-15 20:44:06,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-10-15 20:44:06,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:06,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 20:44:06,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 20:44:06,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00009802sv0000104Dsd00009082bc03sc00i00')
2011-10-15 20:44:06,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-15 20:44:07,011 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,011 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:06,723 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:44:07,017 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 20:44:07,024 DEBUG: fglrx.available: falling back to default
2011-10-15 20:44:07,091 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,092 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:07,055 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:44:07,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-15 20:44:07,134 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,134 DEBUG: fglrx is not the alternative in use
2011-10-15 20:44:07,092 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 20:44:07,144 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-15 20:44:07,153 DEBUG: fglrx.available: falling back to default
2011-10-15 20:44:07,220 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,220 DEBUG: fglrx is not the alternative in use
2011-10-15 20:44:07,183 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 20:44:07,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-15 20:44:07,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 20:44:07,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:SNYSYN0004:SYN0300:SYN0002:PNP0F13:')
2011-10-15 20:44:07,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 20:44:07,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 20:44:07,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFEisc01ip01')
2011-10-15 20:44:07,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:44:07,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2011-10-15 20:44:07,248 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2011-10-15 20:44:07,248 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-15 20:44:07,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 20:44:07,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 20:44:07,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 20:44:07,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 20:44:07,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 20:44:07,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-10-15 20:44:07,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:SNY5001:')
2011-10-15 20:44:07,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrR0160Z7:bd12/22/2010:svnSonyCorporation:pnVPCYB1S1E:pvrC9005MB6:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2011-10-15 20:44:07,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2011-10-15 20:44:07,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 20:44:07,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2011-10-15 20:44:07,295 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2011-10-15 20:44:07,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 20:44:07,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:44:07,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icE0isc01ip01')
2011-10-15 20:44:07,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:44:07,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 20:44:07,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 20:44:07,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 20:44:07,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000104Dsd00009082bc06sc01i00')
2011-10-15 20:44:07,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc01ip00')
2011-10-15 20:44:07,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-15 20:44:07,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2011-10-15 20:44:07,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2011-10-15 20:44:07,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:44:07,319 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:44:07,319 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,319 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:44:07,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000104Dsd00009082bc01sc06i01')
2011-10-15 20:44:07,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 20:44:07,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 20:44:07,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 20:44:07,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2011-10-15 20:44:07,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 20:44:07,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:44:07,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:44:07,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:44:07,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 20:44:07,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFFiscFFipFF')
2011-10-15 20:44:07,338 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:44:07,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-10-15 20:44:07,339 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2011-10-15 20:44:07,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'platform:eisa')
2011-10-15 20:44:07,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 20:44:07,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 20:44:07,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 20:44:07,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0003v04F2pB211e2630-e0,1,kD4,ramlsfw')
2011-10-15 20:44:07,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 20:44:07,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000104Dsd00009082bc0Csc05i00')
2011-10-15 20:44:07,372 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-10-15 20:44:07,372 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,373 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-10-15 20:44:07,373 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2011-10-15 20:44:07,373 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,374 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 20:44:07,374 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:44:07,374 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:44:07,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72ff36c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00001314sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 20:44:07,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001969d00001063sv0000104Dsd00009082bc02sc00i00')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:44:07,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 20:44:07,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00004396sv0000104Dsd00009082bc0Csc03i20')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:sony-laptop')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001510sv0000104Dsd00009082bc06sc00i00')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v0BDAp0186d8687dc00dsc00dp00ic08isc06ip50')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 20:44:07,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00009802sv0000104Dsd00009082bc03sc00i00')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:SNYSYN0004:SYN0300:SYN0002:PNP0F13:')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFEisc01ip01')
2011-10-15 20:44:07,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 20:44:07,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:SNY5001:')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrR0160Z7:bd12/22/2010:svnSonyCorporation:pnVPCYB1S1E:pvrC9005MB6:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 20:44:07,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icE0isc01ip01')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 20:44:07,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000104Dsd00009082bc06sc01i00')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc01ip00')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00004383sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00004391sv0000104Dsd00009082bc01sc06i01')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFFiscFFipFF')
2011-10-15 20:44:07,384 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'platform:eisa')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0003v04F2pB211e2630-e0,1,kD4,ramlsfw')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'pci:v00001002d00004385sv0000104Dsd00009082bc0Csc05i00')
2011-10-15 20:44:07,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2011-10-15 20:44:07,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 20:44:07,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb72ff7ac> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 20:44:07,570 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,571 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:07,751 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,751 DEBUG: fglrx is not the alternative in use
2011-10-15 20:44:07,832 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,832 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:07,940 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:07,940 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:08,010 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:08,011 DEBUG: fglrx is not the alternative in use
2011-10-15 20:44:15,923 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-15 20:44:15,924 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:44:20,415 DEBUG: Installing package: fglrx-updates
2011-10-15 20:44:21,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-10-15 20:44:21,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-10-15 20:44:21,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-10-15 20:44:21,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-10-15 20:44:21,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-10-15 20:44:21,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.300630
2011-10-15 20:44:21,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.301784
2011-10-15 20:44:21,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.551914
2011-10-15 20:44:21,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.561221
2011-10-15 20:44:21,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.835409
2011-10-15 20:44:21,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.840032
2011-10-15 20:44:22,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.378936
2011-10-15 20:44:22,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 4.380959
2011-10-15 20:44:23,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 6.932936
2011-10-15 20:44:23,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 9.629637
2011-10-15 20:44:24,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 10.338787
2011-10-15 20:44:24,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 11.704022
2011-10-15 20:44:25,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 14.091978
2011-10-15 20:44:25,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 16.798327
2011-10-15 20:44:26,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 19.408193
2011-10-15 20:44:26,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 22.211026
2011-10-15 20:44:27,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 24.314356
2011-10-15 20:44:27,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 26.287434
2011-10-15 20:44:28,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 28.414885
2011-10-15 20:44:28,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 30.624347
2011-10-15 20:44:29,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 32.737326
2011-10-15 20:44:29,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 34.917843
2011-10-15 20:44:30,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 37.209315
2011-10-15 20:44:30,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 39.418777
2011-10-15 20:44:31,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 41.628238
2011-10-15 20:44:31,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 43.914886
2011-10-15 20:44:32,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 46.167765
2011-10-15 20:44:32,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 48.507479
2011-10-15 20:44:33,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 50.774831
2011-10-15 20:44:33,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 53.220676
2011-10-15 20:44:34,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 55.700290
2011-10-15 20:44:34,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 58.334277
2011-10-15 20:44:35,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 60.558211
2011-10-15 20:44:35,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 62.907574
2011-10-15 20:44:36,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 65.396836
2011-10-15 20:44:36,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 67.292728
2011-10-15 20:44:37,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 68.879874
2011-10-15 20:44:37,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 70.640689
2011-10-15 20:44:38,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 72.406329
2011-10-15 20:44:38,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 74.321518
2011-10-15 20:44:39,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 76.227058
2011-10-15 20:44:39,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 78.147070
2011-10-15 20:44:40,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 79.985072
2011-10-15 20:44:40,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.578433
2011-10-15 20:44:40,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.578433
2011-10-15 20:44:40,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.578433
2011-10-15 20:44:40,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 82.550534
2011-10-15 20:44:41,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 84.504316
2011-10-15 20:44:41,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 86.356790
2011-10-15 20:44:42,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 88.262330
2011-10-15 20:44:42,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 90.177519
2011-10-15 20:44:43,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 92.314618
2011-10-15 20:44:43,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 94.659156
2011-10-15 20:44:44,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 96.883090
2011-10-15 20:44:44,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 99.256573
2011-10-15 20:44:45,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 100.000000
2011-10-15 20:44:47,203 DEBUG: install progress dpkg-exec 0.000000
2011-10-15 20:44:48,642 DEBUG: install progress patch 0.000000
2011-10-15 20:44:48,644 DEBUG: install progress patch 4.000000
2011-10-15 20:44:49,288 DEBUG: install progress patch 8.000000
2011-10-15 20:44:49,395 DEBUG: install progress patch 12.000000
2011-10-15 20:44:49,815 DEBUG: install progress dkms 12.000000
2011-10-15 20:44:49,917 DEBUG: install progress dkms 16.000000
2011-10-15 20:44:50,471 DEBUG: install progress dkms 20.000000
2011-10-15 20:44:50,566 DEBUG: install progress dkms 24.000000
2011-10-15 20:44:50,966 DEBUG: install progress fakeroot 24.000000
2011-10-15 20:44:51,068 DEBUG: install progress fakeroot 28.000000
2011-10-15 20:44:51,442 DEBUG: install progress fakeroot 32.000000
2011-10-15 20:44:51,549 DEBUG: install progress fakeroot 36.000000
2011-10-15 20:44:52,077 DEBUG: install progress fglrx-updates 36.000000
2011-10-15 20:44:52,179 DEBUG: install progress fglrx-updates 40.000000
2011-10-15 20:44:55,540 DEBUG: install progress fglrx-updates 44.000000
2011-10-15 20:44:55,647 DEBUG: install progress fglrx-updates 48.000000
2011-10-15 20:44:55,996 DEBUG: install progress fglrx-amdcccle-updates 48.000000
2011-10-15 20:44:56,097 DEBUG: install progress fglrx-amdcccle-updates 52.000000
2011-10-15 20:44:56,649 DEBUG: install progress fglrx-amdcccle-updates 56.000000
2011-10-15 20:44:56,746 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2011-10-15 20:44:56,852 DEBUG: install progress man-db 60.000000
2011-10-15 20:45:01,434 DEBUG: install progress ureadahead 60.000000
2011-10-15 20:45:01,801 DEBUG: install progress dpkg-exec 60.000000
2011-10-15 20:45:01,877 DEBUG: install progress patch 60.000000
2011-10-15 20:45:01,950 DEBUG: install progress patch 64.000000
2011-10-15 20:45:02,029 DEBUG: install progress patch 68.000000
2011-10-15 20:45:02,108 DEBUG: install progress dkms 68.000000
2011-10-15 20:45:03,293 DEBUG: install progress dkms 72.000000
2011-10-15 20:45:03,369 DEBUG: install progress dkms 76.000000
2011-10-15 20:45:03,440 DEBUG: install progress fakeroot 76.000000
2011-10-15 20:45:03,518 DEBUG: install progress fakeroot 80.000000
2011-10-15 20:45:03,642 DEBUG: install progress fakeroot 84.000000
2011-10-15 20:45:03,755 DEBUG: install progress fglrx-updates 84.000000
2011-10-15 20:45:04,093 DEBUG: install progress fglrx-updates 88.000000
2011-10-15 20:45:43,875 DEBUG: install progress fglrx-updates 92.000000
2011-10-15 20:45:44,516 DEBUG: install progress bamfdaemon 92.000000
2011-10-15 20:45:44,719 DEBUG: install progress gnome-menus 92.000000
2011-10-15 20:45:44,931 DEBUG: install progress fglrx-amdcccle-updates 92.000000
2011-10-15 20:45:44,998 DEBUG: install progress fglrx-amdcccle-updates 96.000000
2011-10-15 20:45:45,077 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-10-15 20:45:45,156 DEBUG: install progress initramfs-tools 100.000000
2011-10-15 20:46:08,678 DEBUG: install progress libc-bin 100.000000
2011-10-15 20:46:09,886 DEBUG: Selecting previously deselected package patch.
(Reading database ... 126487 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx-updates (2:8.881-0ubuntu6) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture i686
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-10-15 20:46:10,507 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 20:46:10,648 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 20:46:10,879 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:46:10,880 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:46:10,950 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:46:10,951 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:26,912 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c>
2011-10-15 20:50:31,969 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-10-15 20:50:32,272 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-15 20:50:32,286 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-15 20:50:32,398 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-15 20:50:32,434 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-15 20:50:32,596 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-15 20:50:32,609 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-15 20:50:32,609 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:32,844 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:50:32,866 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-15 20:50:32,876 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-15 20:50:32,876 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:32,943 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:50:32,951 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-15 20:50:32,959 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-15 20:50:32,959 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:33,027 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:50:33,028 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-15 20:50:33,093 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-15 20:50:33,103 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-15 20:50:33,103 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:33,186 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:50:33,193 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-15 20:50:33,202 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-15 20:50:33,203 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:33,264 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 20:50:33,270 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-15 20:50:33,278 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-15 20:50:33,279 DEBUG: nvidia.available: falling back to default
2011-10-15 20:50:33,342 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:50:33,343 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-15 20:50:33,387 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-15 20:50:33,388 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-15 20:50:33,420 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-15 20:50:33,420 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-15 20:50:33,454 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-15 20:50:33,500 DEBUG: Software modem not available
2011-10-15 20:50:33,500 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-15 20:50:33,508 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-15 20:50:33,538 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-15 20:50:33,539 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-15 20:50:33,539 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-15 20:50:33,558 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-15 20:50:33,558 DEBUG: fglrx.available: falling back to default
2011-10-15 20:50:33,618 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 20:50:33,625 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-15 20:50:33,632 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-15 20:50:33,633 DEBUG: fglrx.available: falling back to default
2011-10-15 20:50:33,693 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-15 20:50:33,693 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-15 20:50:33,806 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-15 20:50:33,807 DEBUG: Firmware for DVB cards not available
2011-10-15 20:50:33,807 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-15 20:50:33,826 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-15 20:50:33,827 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-15 20:50:33,828 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-15 20:50:33,828 DEBUG: all custom handlers loaded
2011-10-15 20:50:33,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00001314sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:50:35,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:50:35,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2011-10-15 20:50:35,734 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:35,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:35,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:35,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 20:50:35,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 20:50:35,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001969d00001063sv0000104Dsd00009082bc02sc00i00')
2011-10-15 20:50:35,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-10-15 20:50:35,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 20:50:35,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 20:50:35,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:35,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 20:50:35,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-15 20:50:35,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,896 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-15 20:50:35,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:50:35,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:35,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-15 20:50:35,984 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:35,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 20:50:35,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2011-10-15 20:50:35,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 20:50:35,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:35,987 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-10-15 20:50:35,987 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:35,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:sony-laptop')
2011-10-15 20:50:35,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000104Dsd00009082bc0Csc03i20')
2011-10-15 20:50:35,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 20:50:35,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-10-15 20:50:35,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001510sv0000104Dsd00009082bc06sc00i00')
2011-10-15 20:50:35,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 20:50:35,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v0BDAp0186d8687dc00dsc00dp00ic08isc06ip50')
2011-10-15 20:50:36,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-10-15 20:50:36,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,026 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-10-15 20:50:36,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 20:50:36,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 20:50:36,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00009802sv0000104Dsd00009082bc03sc00i00')
2011-10-15 20:50:36,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-15 20:50:36,438 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,439 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:36,035 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:50:36,463 DEBUG: fglrx.available: falling back to default
2011-10-15 20:50:36,613 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,613 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:36,531 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:50:36,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-15 20:50:36,672 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,672 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 20:50:36,614 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 20:50:36,679 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-15 20:50:36,688 DEBUG: fglrx.available: falling back to default
2011-10-15 20:50:36,769 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,769 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 20:50:36,722 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 20:50:36,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-15 20:50:36,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2011-10-15 20:50:36,813 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,814 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:36,770 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:50:36,822 DEBUG: fglrx.available: falling back to default
2011-10-15 20:50:36,935 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:36,936 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:36,877 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 20:50:36,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 20:50:36,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:SNYSYN0004:SYN0300:SYN0002:PNP0F13:')
2011-10-15 20:50:36,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 20:50:36,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 20:50:36,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFEisc01ip01')
2011-10-15 20:50:36,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:50:36,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:36,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2011-10-15 20:50:36,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2011-10-15 20:50:36,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-15 20:50:36,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 20:50:36,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 20:50:36,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:36,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 20:50:36,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 20:50:36,982 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:36,982 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 20:50:36,982 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:36,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:36,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-10-15 20:50:36,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:SNY5001:')
2011-10-15 20:50:36,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrR0160Z7:bd12/22/2010:svnSonyCorporation:pnVPCYB1S1E:pvrC9005MB6:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2011-10-15 20:50:37,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2011-10-15 20:50:37,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 20:50:37,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2011-10-15 20:50:37,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2011-10-15 20:50:37,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 20:50:37,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:50:37,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icE0isc01ip01')
2011-10-15 20:50:37,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:50:37,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 20:50:37,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 20:50:37,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 20:50:37,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000104Dsd00009082bc06sc01i00')
2011-10-15 20:50:37,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc01ip00')
2011-10-15 20:50:37,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-15 20:50:37,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2011-10-15 20:50:37,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2011-10-15 20:50:37,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:50:37,037 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:50:37,037 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 20:50:37,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000104Dsd00009082bc01sc06i01')
2011-10-15 20:50:37,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 20:50:37,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 20:50:37,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 20:50:37,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2011-10-15 20:50:37,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 20:50:37,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,049 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:50:37,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,049 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:50:37,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,050 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 20:50:37,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 20:50:37,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFFiscFFipFF')
2011-10-15 20:50:37,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-15 20:50:37,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-10-15 20:50:37,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2011-10-15 20:50:37,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'platform:eisa')
2011-10-15 20:50:37,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 20:50:37,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 20:50:37,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 20:50:37,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0003v04F2pB211e2630-e0,1,kD4,ramlsfw')
2011-10-15 20:50:37,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 20:50:37,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000104Dsd00009082bc0Csc05i00')
2011-10-15 20:50:37,081 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-10-15 20:50:37,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,081 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-10-15 20:50:37,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2011-10-15 20:50:37,082 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 20:50:37,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 20:50:37,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 20:50:37,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb774b64c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 20:50:37,083 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00001314sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:50:37,083 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001969d00001063sv0000104Dsd00009082bc02sc00i00')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 20:50:37,084 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2011-10-15 20:50:37,085 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:sony-laptop')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000104Dsd00009082bc0Csc03i20')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001510sv0000104Dsd00009082bc06sc00i00')
2011-10-15 20:50:37,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v0BDAp0186d8687dc00dsc00dp00ic08isc06ip50')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00009802sv0000104Dsd00009082bc03sc00i00')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 20:50:37,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:SNYSYN0004:SYN0300:SYN0002:PNP0F13:')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFEisc01ip01')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2011-10-15 20:50:37,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-10-15 20:50:37,089 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:SNY5001:')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrR0160Z7:bd12/22/2010:svnSonyCorporation:pnVPCYB1S1E:pvrC9005MB6:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 20:50:37,090 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icE0isc01ip01')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000104Dsd00009082bc06sc01i00')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v04F2pB211d2630dcEFdsc02dp01ic0Eisc01ip00')
2011-10-15 20:50:37,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000104Dsd00009082bc04sc03i00')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000104Dsd00009082bc01sc06i01')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2011-10-15 20:50:37,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'usb:v0489pE00Fd0596dcE0dsc01dp01icFFiscFFipFF')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'platform:eisa')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 20:50:37,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0003v04F2pB211e2630-e0,1,kD4,ramlsfw')
2011-10-15 20:50:37,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 20:50:37,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000104Dsd00009082bc0Csc05i00')
2011-10-15 20:50:37,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2011-10-15 20:50:37,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 20:50:37,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb755070c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 20:50:37,209 DEBUG: handler xorg:fglrx_updates previously unseen
2011-10-15 20:50:37,210 DEBUG: handler xorg:fglrx previously unseen
2011-10-15 20:50:37,395 DEBUG: writing back check cache /var/cache/jockey/check
2011-10-15 20:50:37,492 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:37,493 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 20:50:37,562 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:37,563 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 20:50:37,708 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 20:50:37,708 DEBUG: fglrx_updates is not the alternative in use
```Can someone please help me? I couldn't find anything about this using the search option.

---

### Post by Raven777 on 2011-10-16
Please?:(

---

### Post by Hobart on 2011-10-17
Same problem here.

Asus M4A78LT-M motherboard, onboard graphics.

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc 760G [Radeon 3000] [1002:9616] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: fglrx_updates, radeon

Amongst other errors in jockey.log - 
2011-10-16 22:38:33,658 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver


Suggestions?

---

### Post by weelk on 2011-10-17
I'm joining with the same problem on Ubuntu 11.10 and ATI HD4870X2

```
2011-10-17 08:21:43,314 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8>
2011-10-17 08:21:45,669 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-10-17 08:21:45,753 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 08:21:45,753 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 08:21:45,772 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 08:21:45,782 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 08:21:45,837 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 08:21:45,840 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 08:21:45,840 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:45,906 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:21:45,909 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 08:21:45,911 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 08:21:45,911 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:45,930 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:21:45,932 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 08:21:45,935 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 08:21:45,935 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:45,954 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:21:45,954 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 08:21:45,968 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 08:21:45,971 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 08:21:45,971 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:45,990 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:21:45,992 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 08:21:45,995 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 08:21:45,995 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:46,015 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:21:46,017 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 08:21:46,020 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 08:21:46,020 DEBUG: nvidia.available: falling back to default
2011-10-17 08:21:46,039 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:21:46,039 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 08:21:46,042 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 08:21:46,051 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 08:21:46,052 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 08:21:46,052 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 08:21:46,055 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 08:21:46,057 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 08:21:46,058 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:46,077 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:21:46,082 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 08:21:46,082 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:46,102 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 08:21:46,102 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 08:21:46,113 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 08:21:46,126 DEBUG: Software modem not available
2011-10-17 08:21:46,126 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 08:21:46,151 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 08:21:46,151 DEBUG: Firmware for DVB cards not available
2011-10-17 08:21:46,151 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 08:21:46,154 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 08:21:46,154 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 08:21:46,164 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 08:21:46,164 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 08:21:46,166 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 08:21:46,167 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 08:21:46,167 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 08:21:46,167 DEBUG: all custom handlers loaded
2011-10-17 08:21:46,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 08:21:46,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v046DpC318e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-17 08:21:46,170 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:46,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:21:46,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 08:21:46,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 08:21:46,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001002sd0000AA30bc04sc03i00')
2011-10-17 08:21:46,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 08:21:46,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 08:21:46,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 08:21:46,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:21:46,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic01isc01ip00')
2011-10-17 08:21:46,493 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-10-17 08:21:46,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 08:21:46,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:46,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v147Ep2016d0002dc00dsc00dp00icFFisc00ip00')
2011-10-17 08:21:46,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v2001pF103d0100dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:21:46,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 08:21:46,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 08:21:46,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 08:21:46,502 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 08:21:46,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 08:21:46,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00001002d00009441sv00001002sd00002542bc03sc00i00')
2011-10-17 08:21:46,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-17 08:21:46,688 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:46,688 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:46,505 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-17 08:21:46,690 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 08:21:46,694 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:46,719 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:46,719 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:46,704 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-17 08:21:46,719 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-17 08:21:46,734 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:46,734 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:46,719 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:46,832 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:46,857 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:46,858 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:46,842 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:46,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-17 08:21:46,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:46,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-10-17 08:21:46,926 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:46,927 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:46,911 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:46,983 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:47,008 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,009 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:46,993 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:47,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-17 08:21:47,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 08:21:47,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 08:21:47,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-17 08:21:47,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-17 08:21:47,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-17 08:21:47,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-17 08:21:47,271 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 08:21:47,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046DpC318d5500dc00dsc00dp00ic03isc00ip02')
2011-10-17 08:21:47,271 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:21:47,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v07C4pA600d9321dc00dsc00dp00ic08isc06ip50')
2011-10-17 08:21:47,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-10-17 08:21:47,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-10-17 08:21:47,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v046DpC51Ae0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-17 08:21:47,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:21:47,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-17 08:21:47,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 08:21:47,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v046DpC318e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 08:21:47,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v15C2pFFDCe0000-e0,1,4,14,k71,72,73,74,77,80,A7,A8,AE,CF,D0,D4,E2,160,166,16D,16E,170,171,172,174,179,181,182,185,188,189,18E,18F,190,191,192,193,197,19C,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2011-10-17 08:21:47,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2302:bd04/15/2010:svnSystemmanufacturer:pnMaximusIIFormula:pvrSystemVersion:rvnASUSTeKComputerINC.:rnMaximusIIFormula:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-17 08:21:47,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-17 08:21:47,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 08:21:47,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-17 08:21:47,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 08:21:47,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008334bc04sc03i00')
2011-10-17 08:21:47,301 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 08:21:47,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046DpC51Ad4101dc00dsc00dp00ic03isc00ip00')
2011-10-17 08:21:47,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:21:47,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:21:47,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v15C2pFFDCd0000dc00dsc00dp00ic00isc00ip00')
2011-10-17 08:21:47,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'imon'}
2011-10-17 08:21:47,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'imon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00002822sv00001043sd000082D4bc01sc04i00')
2011-10-17 08:21:47,312 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 08:21:47,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v046DpC51Ae0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-10-17 08:21:47,312 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00001002d00009441sv00001002sd00002042bc03sc80i00')
2011-10-17 08:21:47,315 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-17 08:21:47,330 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,330 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:47,315 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-17 08:21:47,332 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 08:21:47,335 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:47,360 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,360 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:47,345 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-17 08:21:47,360 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-17 08:21:47,375 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,375 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:47,360 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:47,432 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:47,458 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,458 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:47,442 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:47,512 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-17 08:21:47,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,512 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-10-17 08:21:47,527 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,527 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:47,512 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:47,585 DEBUG: fglrx.available: falling back to default
2011-10-17 08:21:47,610 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,611 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:47,595 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-17 08:21:47,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 08:21:47,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 08:21:47,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 08:21:47,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046DpC51Ad4101dc00dsc00dp00ic03isc01ip02')
2011-10-17 08:21:47,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:21:47,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 08:21:47,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 08:21:47,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 08:21:47,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046DpC318d5500dc00dsc00dp00ic03isc01ip01')
2011-10-17 08:21:47,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:21:47,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 08:21:47,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-17 08:21:47,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v000011ABd00006121sv000011ABsd00006121bc01sc01i8f')
2011-10-17 08:21:47,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 08:21:47,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell'}
2011-10-17 08:21:47,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 08:21:47,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 08:21:47,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 08:21:47,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic01isc02ip00')
2011-10-17 08:21:47,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'input:b0003v15C2pFFDCe0000-e0,1,2,14,k71,72,73,80,8B,A4,A8,AE,D0,D4,E2,110,111,161,179,185,188,189,197,19C,r0,1,8,amlsfw')
2011-10-17 08:21:47,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:21:47,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-17 08:21:47,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-10-17 08:21:47,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x23deab8> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v046DpC318e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001002sd0000AA30bc04sc03i00')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic01isc01ip00')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v147Ep2016d0002dc00dsc00dp00icFFisc00ip00')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v2001pF103d0100dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 08:21:47,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00001002d00009441sv00001002sd00002542bc03sc00i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046DpC318d5500dc00dsc00dp00ic03isc00ip02')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v07C4pA600d9321dc00dsc00dp00ic08isc06ip50')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v046DpC51Ae0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v046DpC318e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v15C2pFFDCe0000-e0,1,4,14,k71,72,73,74,77,80,A7,A8,AE,CF,D0,D4,E2,160,166,16D,16E,170,171,172,174,179,181,182,185,188,189,18E,18F,190,191,192,193,197,19C,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2011-10-17 08:21:47,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2302:bd04/15/2010:svnSystemmanufacturer:pnMaximusIIFormula:pvrSystemVersion:rvnASUSTeKComputerINC.:rnMaximusIIFormula:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008334bc04sc03i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046DpC51Ad4101dc00dsc00dp00ic03isc00ip00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v15C2pFFDCd0000dc00dsc00dp00ic00isc00ip00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00002822sv00001043sd000082D4bc01sc04i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v046DpC51Ae0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00001002d00009441sv00001002sd00002042bc03sc80i00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046DpC51Ad4101dc00dsc00dp00ic03isc01ip02')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046DpC318d5500dc00dsc00dp00ic03isc01ip01')
2011-10-17 08:21:47,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v000011ABd00006121sv000011ABsd00006121bc01sc01i8f')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'usb:v046Dp08CAd0005dcEFdsc02dp01ic01isc02ip00')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'input:b0003v15C2pFFDCe0000-e0,1,2,14,k71,72,73,80,8B,A4,A8,AE,D0,D4,E2,110,111,161,179,185,188,189,197,19C,r0,1,8,amlsfw')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-17 08:21:47,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25ec680> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-17 08:21:47,732 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,732 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:47,777 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,777 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:47,919 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,919 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:47,950 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,950 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:47,973 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:47,973 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:21:53,994 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:53,994 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:21:58,464 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:21:58,464 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:22:04,232 DEBUG: Installing package: fglrx-updates
2011-10-17 08:22:05,237 DEBUG: install progress dpkg-exec 0.000000
2011-10-17 08:22:09,478 DEBUG: install progress fglrx-amdcccle 0.000000
2011-10-17 08:22:09,579 DEBUG: install progress fglrx-amdcccle 6.250000
2011-10-17 08:22:10,773 DEBUG: install progress fglrx-amdcccle 12.500000
2011-10-17 08:22:11,055 DEBUG: install progress fglrx-amdcccle 18.750000
2011-10-17 08:22:11,617 DEBUG: install progress fglrx 18.750000
2011-10-17 08:22:11,717 DEBUG: install progress fglrx 25.000000
2011-10-17 08:22:21,973 DEBUG: install progress fglrx 31.250000
2011-10-17 08:22:22,804 DEBUG: install progress fglrx 37.500000
2011-10-17 08:22:22,998 DEBUG: install progress bamfdaemon 37.500000
2011-10-17 08:22:23,217 DEBUG: install progress gnome-menus 37.500000
2011-10-17 08:22:23,423 DEBUG: install progress libc-bin 37.500000
2011-10-17 08:22:23,810 DEBUG: install progress ureadahead 37.500000
2011-10-17 08:22:24,016 DEBUG: install progress initramfs-tools 37.500000
2011-10-17 08:22:30,783 DEBUG: install progress dpkg-exec 37.500000
2011-10-17 08:22:31,751 DEBUG: install progress fglrx-updates 37.500000
2011-10-17 08:22:31,851 DEBUG: install progress fglrx-updates 43.750000
2011-10-17 08:22:38,650 DEBUG: install progress fglrx-updates 50.000000
2011-10-17 08:22:38,741 DEBUG: install progress fglrx-updates 56.250000
2011-10-17 08:22:38,987 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-10-17 08:22:38,988 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-10-17 08:22:39,730 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-10-17 08:22:39,831 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-10-17 08:22:39,931 DEBUG: install progress ureadahead 75.000000
2011-10-17 08:22:40,380 DEBUG: install progress dpkg-exec 75.000000
2011-10-17 08:22:40,414 DEBUG: install progress fglrx-updates 75.000000
2011-10-17 08:22:40,985 DEBUG: install progress fglrx-updates 81.250000
2011-10-17 08:22:58,558 DEBUG: install progress fglrx-updates 87.500000
2011-10-17 08:22:59,268 DEBUG: install progress bamfdaemon 87.500000
2011-10-17 08:22:59,468 DEBUG: install progress gnome-menus 87.500000
2011-10-17 08:22:59,759 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-10-17 08:22:59,856 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-10-17 08:22:59,953 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-10-17 08:23:00,057 DEBUG: install progress initramfs-tools 100.000000
2011-10-17 08:23:06,196 DEBUG: install progress libc-bin 100.000000
2011-10-17 08:23:09,201 DEBUG: (Reading database ... 152604 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Warning: No support for locale: en_GB.utf8
Selecting previously deselected package fglrx-updates.
(Reading database ... 152360 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.881-0ubuntu6) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Warning: No support for locale: en_GB.utf8
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-10-17 08:23:09,453 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-17 08:23:09,518 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-17 08:23:09,597 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:23:09,597 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:23:09,618 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:23:09,618 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,082 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,082 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,103 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,104 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,138 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,138 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:25:03,285 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,286 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,307 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,349 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,349 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,371 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,371 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:03,402 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:03,403 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:25:05,503 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:05,503 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-17 08:25:08,950 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:08,951 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:25:08,972 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:25:08,972 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:27:46,074 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:27:46,074 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:27:46,096 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:27:46,096 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:27:51,752 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-17 08:27:51,816 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-17 08:27:51,891 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:27:51,891 DEBUG: fglrx_updates is not the alternative in use
2011-10-17 08:27:51,913 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-17 08:27:51,913 DEBUG: fglrx_updates is not the alternative in use
```

---

### Post by Raven777 on 2011-10-17
Apparently, it's a bug that hasn't been fixed... At least that's what they say on a German forum.

I thought I needed the graphics drivers to use Compiz - Someone on a different forum said you don't need them to use Compiz... However, whenever I activate an effect in Compizconfig, it never actually changes anything... Is that another bug or what am I doing wrong?

---

### Post by craterib on 2011-10-17
Hi,

I had the same trouble. I went past it using the following steps.

I must warn you, I am a noob too, and at that a very very fresh one. So do it at your own risk.

I manually installed catalyst 11.9 and gnome got fixed and I was able to get past the error.

Follow the steps in this thread: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Do everything as given in this thread.

---

### Post by Raven777 on 2011-10-28
Well, I have decided I'm giving this another try... How do I know what information to provide on the [AMD/ATI Website?]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

Like, how do I know what to select in the "Select the type of system that you have: " section?

My graphics card is "AMD Radeon HD 6310 Graphics"

---

### Post by Vaphell on 2011-10-28
hardware drivers (jockey-gtk) still doesn't let you install the driver? do you have fglrx, fglrx-updates and fglrx-amdcccle-updates installed? you can check that in synaptic (but it's not default in 11.10 so you have to install it first)

amd site: 6310 is a gfx from fusion apu (cpu+gpu) like e350? desktop graphics > e-series apu > e350

---

### Post by Raven777 on 2011-10-28
Thanks. But every time I try to install the driver the way it says on the website, I get a message saying that a perevious install of the fglrx driver has been detected. It then can't install because of that. How do I uninstall my existing fglrx driver?

> hardware drivers (jockey-gtk) still doesn't let you install the driver?  do you have fglrx, fglrx-updates and fglrx-amdcccle-updates installed?  you can check that in synaptic (but it's not default in 11.10 so you  have to install it first)Yes, I've tried that as well and it doesn't work.

---

### Post by Vaphell on 2011-10-28
try removing all fglrx packages in synaptic

---

### Post by Raven777 on 2011-10-28
Yes, I removed all of them, but it still doesn't work.

---

### Post by Harryo53 on 2011-10-28
The newest Catalyst did not install for me, but the secondary install worked.

Problem is now that it will not save any of my selections.  I have multiple displays, I arrange them.  I choose resolution, and click 'apply'.  The program does change resolution, but never 'comes back'. I have to restart Catalyst.

Setting my multiple displays does not work, and basically the screen layouts are garbage.  One overlaps the other, no matter what I do.

The program makes some changes that stick, but not all.

I don't see a facility for setting the primary display either.  I have a DVI connected HDTV, but that's not my primary.  I use a vga connected smaller monitor as primary.  The system always defaults to a cloned desktop, which is not what I want.  I don't see a facility for designating primary display as well.

Anybody?

---

### Post by Raven777 on 2011-10-29
So I've finally found a way to uninstall fglrx and I installed the driver that I got from the ATI/AMD Website. Now when I try to follow the tutoriial, I can't install those *deb files. Every time I copy and paste the command
```
sudo dpkg -i *.deb
```to my Terminal, it says that it has been locked due to some other process... Please help?

I also tried finding the *deb files on my system but couldn't.

---

