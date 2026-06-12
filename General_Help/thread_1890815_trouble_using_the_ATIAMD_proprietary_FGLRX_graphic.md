---
title: "trouble using the ATI/AMD proprietary FGLRX graphics driver"
date: 2011-12-04
forum: General Help
---

### Post by cyberjar09 on 2011-12-04
The graphics card on my laptop is Mobility Radeon HD 4500. I just installed ubuntu 11.10 and the proprietary drivers list has two items 
1. ATI/AMD proprietary FGLRX grpahics driver (post-release updates)
2. ATI/AMD proprietary FGLRX grpahics driver 

I can activate the second one but everytime I try to update the post-release upadtes, I get an error .. please refer to the text pasted below from my jockey.log file 

Thanks.

=====================================================
```

2011-12-04 22:15:45,861 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c>
2011-12-04 22:15:47,498 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-04 22:15:47,600 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-04 22:15:47,605 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-04 22:15:47,640 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-04 22:15:47,655 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-04 22:15:47,688 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-04 22:15:47,712 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-04 22:15:47,712 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-04 22:15:47,712 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-04 22:15:47,728 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-04 22:15:47,743 DEBUG: Software modem not available
2011-12-04 22:15:47,743 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-04 22:15:47,748 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-04 22:15:47,748 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-04 22:15:47,768 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-04 22:15:47,768 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-04 22:15:47,828 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-04 22:15:47,829 DEBUG: Firmware for DVB cards not available
2011-12-04 22:15:47,830 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-04 22:15:47,859 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-04 22:15:47,865 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-04 22:15:47,865 DEBUG: fglrx.available: falling back to default
2011-12-04 22:15:48,022 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-04 22:15:48,033 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-04 22:15:48,033 DEBUG: fglrx.available: falling back to default
2011-12-04 22:15:48,084 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-04 22:15:48,085 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-04 22:15:48,089 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-04 22:15:48,090 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-04 22:15:48,090 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-04 22:15:48,090 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-04 22:15:48,096 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-04 22:15:48,101 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-04 22:15:48,101 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,144 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-04 22:15:48,147 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-04 22:15:48,153 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-04 22:15:48,153 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,194 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-04 22:15:48,200 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-04 22:15:48,206 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-04 22:15:48,207 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,251 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-04 22:15:48,251 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-04 22:15:48,269 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-04 22:15:48,273 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-04 22:15:48,274 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,324 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-04 22:15:48,329 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-04 22:15:48,333 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-04 22:15:48,334 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,390 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-04 22:15:48,396 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-04 22:15:48,402 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-04 22:15:48,403 DEBUG: nvidia.available: falling back to default
2011-12-04 22:15:48,459 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-04 22:15:48,460 DEBUG: all custom handlers loaded
2011-12-04 22:15:48,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-12-04 22:15:48,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:48,558 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B03sv00001028sd000002BDbc06sc01i00')
2011-12-04 22:15:48,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-04 22:15:48,828 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA9sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:regulatory')
2011-12-04 22:15:48,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-04 22:15:48,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:48,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2011-12-04 22:15:48,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-04 22:15:48,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-04 22:15:48,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-04 22:15:48,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd000002BDbc0Csc03i20')
2011-12-04 22:15:48,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00004235sv00008086sd00001121bc02sc80i00')
2011-12-04 22:15:48,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-12-04 22:15:48,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd000002BDbc04sc03i00')
2011-12-04 22:15:48,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-04 22:15:48,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CAAsv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-04 22:15:48,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA8sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd000002BDbc0Csc03i20')
2011-12-04 22:15:48,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-04 22:15:48,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:48,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C52sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA06:bd05/27/2010:svnDellInc.:pnStudio1557:pvrA06:rvnDellInc.:rn0KM426:rvrA06:cvnDellInc.:ct8:cvrA06:')
2011-12-04 22:15:48,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-12-04 22:15:48,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-12-04 22:15:48,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA3sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2011-12-04 22:15:48,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-04 22:15:48,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2011-12-04 22:15:48,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA0sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2011-12-04 22:15:48,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-04 22:15:48,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA2sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:dcdbas')
2011-12-04 22:15:48,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-04 22:15:48,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:48,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C90sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,924 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2011-12-04 22:15:48,924 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D158sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:48,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-12-04 22:15:48,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C81sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CA1sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-04 22:15:48,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D155sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:48,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002BDbc06sc04i01')
2011-12-04 22:15:48,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:eisa')
2011-12-04 22:15:48,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-04 22:15:48,947 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-04 22:15:48,947 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,947 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-04 22:15:48,947 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:48,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v0C45p6417dA112dcEFdsc02dp01ic0Eisc01ip00')
2011-12-04 22:15:48,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-04 22:15:48,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:48,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C9Csv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:48,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-12-04 22:15:48,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001028sd000002BDbc04sc03i00')
2011-12-04 22:15:49,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-04 22:15:49,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-04 22:15:49,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0003v0C45p6417eA112-e0,1,kD4,ramlsfw')
2011-12-04 22:15:49,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D150sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:49,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-04 22:15:49,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-04 22:15:49,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,310 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-04 22:15:49,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-04 22:15:49,310 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002CABsv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:49,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2011-12-04 22:15:49,313 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-04 22:15:49,313 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-04 22:15:49,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-04 22:15:49,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001180d0000E852sv00001028sd000002BDbc08sc80i00')
2011-12-04 22:15:49,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000002BDbc02sc00i00')
2011-12-04 22:15:49,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-12-04 22:15:49,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D157sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:49,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001180d0000E822sv00001028sd000002BDbc08sc05i00')
2011-12-04 22:15:49,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2011-12-04 22:15:49,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2011-12-04 22:15:49,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-04 22:15:49,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2011-12-04 22:15:49,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C98sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:49,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-12-04 22:15:49,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001180d0000E230sv00001028sd000002BDbc08sc80i00')
2011-12-04 22:15:49,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-04 22:15:49,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-04 22:15:49,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-04 22:15:49,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:49,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-12-04 22:15:49,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C91sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:49,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00002C99sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:49,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-04 22:15:49,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-04 22:15:49,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd000002BDbc0Csc05i00')
2011-12-04 22:15:49,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-04 22:15:49,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-04 22:15:49,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd000002BDbc01sc06i01')
2011-12-04 22:15:49,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-04 22:15:49,346 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-04 22:15:49,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:49,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D132sv00001028sd000002BDbc06sc00i00')
2011-12-04 22:15:49,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-04 22:15:49,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001180d0000E832sv00001028sd000002BDbc0Csc00i10')
2011-12-04 22:15:49,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-04 22:15:49,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-12-04 22:15:49,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'platform:dell-laptop')
2011-12-04 22:15:49,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-12-04 22:15:49,351 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-12-04 22:15:49,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:49,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-04 22:15:49,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-04 22:15:49,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-04 22:15:49,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-04 22:15:49,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-04 22:15:49,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D151sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:49,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00001002d00009553sv00001028sd000002BDbc03sc00i00')
2011-12-04 22:15:49,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-04 22:15:49,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:49,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-12-04 22:15:49,731 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:49,731 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:49,359 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-04 22:15:49,822 DEBUG: fglrx.available: falling back to default
2011-12-04 22:15:49,866 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:49,866 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:49,848 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-04 22:15:49,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-04 22:15:49,952 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:49,952 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:49,932 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-04 22:15:49,954 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-04 22:15:49,957 DEBUG: fglrx.available: falling back to default
2011-12-04 22:15:49,990 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:49,990 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:49,972 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-04 22:15:49,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-04 22:15:50,009 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,009 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:49,990 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-04 22:15:50,076 DEBUG: fglrx.available: falling back to default
2011-12-04 22:15:50,108 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,109 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:50,090 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-04 22:15:50,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-04 22:15:50,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2011-12-04 22:15:50,185 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-04 22:15:50,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:50,185 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-04 22:15:50,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:50,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-04 22:15:50,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'pci:v00008086d0000D156sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-04 22:15:50,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'usb:v0C45p6417dA112dcEFdsc02dp01ic0Eisc02ip00')
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb730b64c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-12-04 22:15:50,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-04 22:15:50,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B03sv00001028sd000002BDbc06sc01i00')
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA9sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:regulatory')
2011-12-04 22:15:50,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd000002BDbc0Csc03i20')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00004235sv00008086sd00001121bc02sc80i00')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd000002BDbc04sc03i00')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CAAsv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-04 22:15:50,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA8sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd000002BDbc0Csc03i20')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C52sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA06:bd05/27/2010:svnDellInc.:pnStudio1557:pvrA06:rvnDellInc.:rn0KM426:rvrA06:cvnDellInc.:ct8:cvrA06:')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA3sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2011-12-04 22:15:50,192 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA0sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA2sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:dcdbas')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C90sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D158sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C81sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CA1sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,193 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D155sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002BDbc06sc04i01')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:eisa')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:pcspkr')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v0C45p6417dA112dcEFdsc02dp01ic0Eisc01ip00')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C9Csv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-12-04 22:15:50,194 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001028sd000002BDbc04sc03i00')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0003v0C45p6417eA112-e0,1,kD4,ramlsfw')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D150sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002CABsv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-04 22:15:50,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001180d0000E852sv00001028sd000002BDbc08sc80i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000002BDbc02sc00i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D157sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001180d0000E822sv00001028sd000002BDbc08sc05i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C98sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:SMO8800:')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001180d0000E230sv00001028sd000002BDbc08sc80i00')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-04 22:15:50,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C91sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00002C99sv00008086sd00008086bc06sc00i00')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd000002BDbc0Csc05i00')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-04 22:15:50,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd000002BDbc01sc06i01')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D132sv00001028sd000002BDbc06sc00i00')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001180d0000E832sv00001028sd000002BDbc0Csc00i10')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'platform:dell-laptop')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-04 22:15:50,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D151sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00001002d00009553sv00001028sd000002BDbc03sc00i00')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'pci:v00008086d0000D156sv00000000sd00000000bc08sc80i00')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'usb:v0C45p6417dA112dcEFdsc02dp01ic0Eisc02ip00')
2011-12-04 22:15:50,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69fc6cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-12-04 22:15:50,271 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,271 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:50,339 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,340 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:50,571 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,571 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:50,678 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,679 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:50,748 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:50,749 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:15:57,284 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:15:57,284 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:15:59,882 DEBUG: Installing package: fglrx-updates
2011-12-04 22:16:01,026 DEBUG: install progress dpkg-exec 0.000000
2011-12-04 22:16:03,361 DEBUG: install progress fglrx-amdcccle 0.000000
2011-12-04 22:16:03,416 DEBUG: install progress fglrx-amdcccle 6.250000
2011-12-04 22:16:03,417 DEBUG: install progress fglrx-amdcccle 12.500000
2011-12-04 22:16:03,625 DEBUG: install progress fglrx-amdcccle 18.750000
2011-12-04 22:16:03,947 DEBUG: install progress fglrx 18.750000
2011-12-04 22:16:04,048 DEBUG: install progress fglrx 25.000000
2011-12-04 22:16:14,286 DEBUG: install progress fglrx 31.250000
2011-12-04 22:16:14,997 DEBUG: install progress fglrx 37.500000
2011-12-04 22:16:15,114 DEBUG: install progress bamfdaemon 37.500000
2011-12-04 22:16:15,272 DEBUG: install progress gnome-menus 37.500000
2011-12-04 22:16:15,405 DEBUG: install progress ureadahead 37.500000
2011-12-04 22:16:15,530 DEBUG: install progress initramfs-tools 37.500000
2011-12-04 22:16:27,220 DEBUG: install progress libc-bin 37.500000
2011-12-04 22:16:27,534 DEBUG: install progress dpkg-exec 37.500000
2011-12-04 22:16:28,006 DEBUG: install progress fglrx-updates 37.500000
2011-12-04 22:16:28,006 DEBUG: install progress fglrx-updates 43.750000
2011-12-04 22:16:30,082 DEBUG: install progress fglrx-updates 50.000000
2011-12-04 22:16:30,133 DEBUG: install progress fglrx-updates 56.250000
2011-12-04 22:16:30,297 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-12-04 22:16:30,398 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-12-04 22:16:30,875 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-12-04 22:16:30,922 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-12-04 22:16:30,967 DEBUG: install progress ureadahead 75.000000
2011-12-04 22:16:31,210 DEBUG: install progress dpkg-exec 75.000000
2011-12-04 22:16:31,244 DEBUG: install progress fglrx-updates 75.000000
2011-12-04 22:16:31,507 DEBUG: install progress fglrx-updates 81.250000
2011-12-04 22:17:02,020 DEBUG: install progress fglrx-updates 87.500000
2011-12-04 22:17:02,453 DEBUG: install progress bamfdaemon 87.500000
2011-12-04 22:17:02,596 DEBUG: install progress gnome-menus 87.500000
2011-12-04 22:17:02,778 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-12-04 22:17:02,837 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-12-04 22:17:02,895 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-12-04 22:17:02,953 DEBUG: install progress initramfs-tools 100.000000
2011-12-04 22:17:14,141 DEBUG: install progress libc-bin 100.000000
2011-12-04 22:17:15,144 DEBUG: (Reading database ... 168325 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 168105 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.902-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Loading new fglrx-updates-8.902 DKMS files...
Building only for 3.0.0-13-generic-pae
Building for architecture i686
Building initial module for 3.0.0-13-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.902-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-12-04 22:17:15,461 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-12-04 22:17:15,545 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-12-04 22:17:15,676 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:15,677 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:15,721 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:15,722 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,417 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,418 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,446 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,447 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,501 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,501 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:17:19,732 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,732 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,761 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,761 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,887 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,888 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:19,940 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:19,941 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:17:20,027 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:20,028 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:17:22,566 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:22,567 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:17:24,109 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:17:24,109 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:17:24,465 DEBUG: Installing package: fglrx
2011-12-04 22:17:25,053 DEBUG: install progress dpkg-exec 0.000000
2011-12-04 22:17:25,291 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2011-12-04 22:17:25,344 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2011-12-04 22:17:25,344 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2011-12-04 22:17:25,470 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2011-12-04 22:17:25,790 DEBUG: install progress fglrx-updates 18.750000
2011-12-04 22:17:25,891 DEBUG: install progress fglrx-updates 25.000000
2011-12-04 22:17:29,715 DEBUG: install progress fglrx-updates 31.250000
2011-12-04 22:17:30,186 DEBUG: install progress fglrx-updates 37.500000
2011-12-04 22:17:30,286 DEBUG: install progress bamfdaemon 37.500000
2011-12-04 22:17:30,396 DEBUG: install progress gnome-menus 37.500000
2011-12-04 22:17:30,488 DEBUG: install progress ureadahead 37.500000
2011-12-04 22:17:30,580 DEBUG: install progress initramfs-tools 37.500000
2011-12-04 22:17:41,481 DEBUG: install progress libc-bin 37.500000
2011-12-04 22:17:41,786 DEBUG: install progress dpkg-exec 37.500000
2011-12-04 22:17:42,261 DEBUG: install progress fglrx 37.500000
2011-12-04 22:17:42,361 DEBUG: install progress fglrx 43.750000
2011-12-04 22:17:44,302 DEBUG: install progress fglrx 50.000000
2011-12-04 22:17:44,361 DEBUG: install progress fglrx 56.250000
2011-12-04 22:17:44,531 DEBUG: install progress fglrx-amdcccle 56.250000
2011-12-04 22:17:44,632 DEBUG: install progress fglrx-amdcccle 62.500000
2011-12-04 22:17:45,044 DEBUG: install progress fglrx-amdcccle 68.750000
2011-12-04 22:17:45,116 DEBUG: install progress fglrx-amdcccle 75.000000
2011-12-04 22:17:45,178 DEBUG: install progress ureadahead 75.000000
2011-12-04 22:17:45,447 DEBUG: install progress dpkg-exec 75.000000
2011-12-04 22:17:45,482 DEBUG: install progress fglrx 75.000000
2011-12-04 22:17:45,800 DEBUG: install progress fglrx 81.250000
2011-12-04 22:18:12,665 DEBUG: install progress fglrx 87.500000
2011-12-04 22:18:13,073 DEBUG: install progress bamfdaemon 87.500000
2011-12-04 22:18:13,198 DEBUG: install progress gnome-menus 87.500000
2011-12-04 22:18:13,373 DEBUG: install progress fglrx-amdcccle 87.500000
2011-12-04 22:18:13,439 DEBUG: install progress fglrx-amdcccle 93.750000
2011-12-04 22:18:13,499 DEBUG: install progress fglrx-amdcccle 100.000000
2011-12-04 22:18:13,557 DEBUG: install progress initramfs-tools 100.000000
2011-12-04 22:18:24,494 DEBUG: install progress libc-bin 100.000000
2011-12-04 22:18:25,497 DEBUG: (Reading database ... 168325 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 168105 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Loading new fglrx-8.881 DKMS files...
Building only for 3.0.0-13-generic-pae
Building for architecture i686
Building initial module for 3.0.0-13-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-12-04 22:18:25,639 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:02:00.0
2011-12-04 22:18:46,600 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:46,600 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:46,695 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:46,696 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:46,867 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:46,867 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:18:46,914 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:46,915 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:18:47,029 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,029 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:47,132 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,133 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:47,355 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,355 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:47,465 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,466 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:47,645 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,645 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:18:47,676 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,676 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:18:47,728 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,729 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:47,836 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:47,836 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-04 22:18:51,712 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:51,713 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:18:51,769 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-04 22:18:51,769 DEBUG: fglrx_updates is not the alternative in use
2011-12-04 22:30:18,095 DEBUG: Shutting down


```

---

### Post by FallenUnia on 2011-12-04
I never used Jockey precisely because of that I don't exactly know what it does so the errors are harder to fix.

When I install Catalyst, I always do it myself. Here's some short instructions you can follow to do the same:

  1. Go to amd.com and download your driver
  2. Run: sudo apt-get --purge remove fglrx*
  3. Run: sudo apt-get install dh-make execstack dh-modaliases dkms lib32gcc1 libc6-i386
  4. Go to the directory you downloaded the driver in (usually ~Downloads)
      Run: sudo chmod +x ati-driver-installer-11-10-x86.x86_64.run
      Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric
      Here I assume you are using Ubuntu 11.10. If you're using another version, use that version's name, for example Ubuntu/maverick
  5. Run: sudo dpkg -i *.deb
  6. Run: sudo aticonfig --initial -f

Now reboot and it should be working. Please do note that I am not responsible for any damage you might do, although these instructions have always worked for me!

---

### Post by quadproc on 2011-12-04
> **FallenUnia said:**
> I never used Jockey precisely because of that I don't exactly know what it does so the errors are harder to fix.

+1.

The additional drivers utility does not allow you to choose which version of the fglrx driver you wish to load so you are stuck with whatever it thinks is right.  That utility also does not correctly report the driver in use.

Before changing drivers I always do some web searching, check the release notes, and ask a few acquaintances if they can suggest anything related to the driver before I install it.  Then I download a fresh copy of the version that I want from the ATI site. Before I install it (this is _very_ important) I remove the old driver.  Failing to remove the old driver first can cause problems ranging from odd behavior to a black screen; if you get the later then you may have to ssh into the system to fix it.  Then I install the new driver.  Sometimes I have to go in to the configuration file later to set up certain things.

quadproc

---

### Post by Goupit on 2011-12-04
I have an ACER ASPIRE with an ATI mobility radeon 4330. I have the switchable graphics option. I followed FallenUnia's instructions. > **FallenUnia said:**
> 
  1. Go to amd.com and download your driver
  2. Run: sudo apt-get --purge remove fglrx*
  3. Run: sudo apt-get install dh-make execstack dh-modaliases dkms lib32gcc1 libc6-i386
  4. Go to the directory you downloaded the driver in (usually ~Downloads)
      Run: sudo chmod +x ati-driver-installer-11-10-x86.x86_64.run
      Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric
      Here I assume you are using Ubuntu 11.10. If you're using another version, use that version's name, for example Ubuntu/maverick
  5. Run: sudo dpkg -i *.deb
  6. Run: sudo aticonfig --initial -f

Now reboot and it should be working. Please do note that I am not responsible for any damage you might do, although these instructions have always worked for me!

except that the last command "sudo aticonfig --initial -f" didn't work. Even so, i rebooted. After rebooting what happened is that my system stuck in some prompt where it did some checks. I recall the last one was Checking battery and went no further. I pressed Alt+F2 and got a terminal. Logged in and fortunately it had kept my last commands. What i did was execute "sudo apt-get --purge remove fglrx*" wishing that it would undo any changes that might have caused the problem. But now the problem remains. Now, when rebooting it shows the Ubuntu loading bar only for a moment and then the screen shows nothing. Can't get a terminal or anything. I tried changing the switchable option from BIOS to Discrete but still i don't get any login screen. This state that the system comes in, is the same as when i installed the drivers by the additional drivers application. What i'm asking is if there's a way to undo these changes made by the above instructions and reverting the system to as it was before, without having to reinstall Ubuntu. Thanks in advance.

---

### Post by FallenUnia on 2011-12-05
> **Goupit said:**
> I have an ACER ASPIRE with an ATI mobility radeon 4330. I have the switchable graphics option. I followed FallenUnia's instructions. 

except that the last command "sudo aticonfig --initial -f" didn't work. Even so, i rebooted. After rebooting what happened is that my system stuck in some prompt where it did some checks. I recall the last one was Checking battery and went no further. I pressed Alt+F2 and got a terminal. Logged in and fortunately it had kept my last commands. What i did was execute "sudo apt-get --purge remove fglrx*" wishing that it would undo any changes that might have caused the problem. But now the problem remains. Now, when rebooting it shows the Ubuntu loading bar only for a moment and then the screen shows nothing. Can't get a terminal or anything. I tried changing the switchable option from BIOS to Discrete but still i don't get any login screen. This state that the system comes in, is the same as when i installed the drivers by the additional drivers application. What i'm asking is if there's a way to undo these changes made by the above instructions and reverting the system to as it was before, without having to reinstall Ubuntu. Thanks in advance.

Instead of just rebooting, you should've looked as for WHY it was failing. Now X won't start since you NEED the xorg.conf file that the last step creates.

If you can, boot to CLI. Log in as root / your user and navigate to the folder in which you build the Catalyst .debs. Reinstall those, and try to figure out why the last step fails. If it throws error messages again, report them here.

If that doesn't work, I'll have to google some myself to help you

---

### Post by matt3839 on 2011-12-05
> **quadproc said:**
> +1.

The additional drivers utility does not allow you to choose which version of the fglrx driver you wish to load so you are stuck with whatever it thinks is right.  That utility also does not correctly report the driver in use.

Before changing drivers I always do some web searching, check the release notes, and ask a few acquaintances if they can suggest anything related to the driver before I install it.  Then I download a fresh copy of the version that I want from the ATI site. Before I install it (this is _very_ important) I remove the old driver.  Failing to remove the old driver first can cause problems ranging from odd behavior to a black screen; if you get the later then you may have to ssh into the system to fix it.  Then I install the new driver.  Sometimes I have to go in to the configuration file later to set up certain things.

quadproc
Even if you want to use the prepackaged proprietary drivers, Jockey is a mediocre program for the job. It's far easier and more reliable, in my experience, to just install either the "fglrx" and "fglrx-amdcccle" packages, or the "fglrx-updates" and "fglrx-amdcccle-updates" packages; no muss, no fuss, easy to deal with like any other package, instead of a program with an extremely nebulous user interface.

---

### Post by Goupit on 2011-12-06
> **FallenUnia said:**
> Instead of just ...... I'll have to google some myself to help you

Thanks FallenUnia. No need to do that. I managed to do something. Basicaly i -think- reconfigured xorg.conf. I'm not a so advanced user of OS's. I'm searching to find a solution about this problem with my laptop since summer. I found the instructions from [here]("http://askubuntu.com/questions/67065/system-doesnt-boot-after-amd-11-9-driver-install/67169#67169"). I didn't execute all of them though. I thought the best thing to do was to revert to any previous state. What i did was this(Sorry if some of these are unnecessary, more advanced user can tell me what to edit in the post if necessary):
1. loaded recovery mode->mounted all...->root promt with network
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

with the ones up to here i managed to log in to a desctop with no unity abilities. I t was like a windows manager environment. I then did:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo dpkg-reconfigure xserver-xorg
```

rebooted and everything was as before... I think. Its too bad though that there is no solution to my broblem cause i am using ubuntu for five yaers now and there is no other to do the job better but since i'm looking for something quite light for my little one i'm thinking of trying something else, maybe Lubuntu. Anyway, hope i helped somehow.

---

### Post by cyberjar09 on 2012-02-01
Thanks a ton FallenUnia. 
Just did a reinstall of my Ubuntu and came back to these instructions for a refresh. Your instructions worked like a charm. 
Im quite a n00b when it comes to using Linux distros and just to outline the finer tweaks to your outlined steps :

lspci | grep VGA was quite usless in telling me my exact model number 
```
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500/5100 Series]
```
so I installed hwinfo and tried hwinfo | grep Radeon instead which gave me what I needed to download the correct driver 
```
Model: "ATI M92 [Mobility Radeon HD 4500 Series]"
  Device: pci 0x9553 "M92 [Mobility Radeon HD 4500 Series]"
```

Also, in step 3 I got an error on console stating that I must use libc6 instead of lib32gcc1 & libc6-i386 which worked just fine 

And everything else worked like a charm! 
Thanks again, your assistance in the matter has been invaluable.

---

### Post by cyberjar09 on 2012-05-01
> **FallenUnia said:**
> 
      Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/oneiric
      Here I assume you are using Ubuntu 11.10. If you're using another version, use that version's name, for example Ubuntu/maverick
  5. Run: sudo dpkg -i *.deb
  6. Run: sudo aticonfig --initial -f


Hey, so I just upgraded to 12.04

please tell me what im missing here, 

I did run ```
sudo dpkg -i *.deb
``` 

here is my output
```
Selecting previously unselected package fglrx.
(Reading database ... 199017 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.961-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.961-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.961-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev

```

also, there is no command called aticonfig anymore. 

help please?

---

### Post by cyberjar09 on 2012-05-04
*bump* 

kind of lost here. Any help would be appreciated.

---

### Post by meanpt on 2012-05-05
I'm marking this thread because I'm also having the same problem as you do. I'm already in the 10th 12.04 installation with ati driver's experimenting and got nothing so far, not even by forcing amdconfig to use xorg.conf.

---

