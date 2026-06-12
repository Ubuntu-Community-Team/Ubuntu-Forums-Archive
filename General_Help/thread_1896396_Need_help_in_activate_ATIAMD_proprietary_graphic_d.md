---
title: "Need help in activate ATI/AMD proprietary graphic driver"
date: 2011-12-16
forum: General Help
---

### Post by mjsilverstri on 2011-12-16
Hi,

I have installed ubuntu 11.10. And I would like to upgrade the ATI/AMD proprietary FGLAX graphics driver. 

I go to Hardware->Additional Drivers and I tried to activate 'ATI/AMD proprietary FGLAX graphics driver'. It failed and asked me to look at var/log/jockey.log.

Attached is my jockey.log but I can't figure out my problem.
```

2011-12-16 18:06:52,887 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320>
2011-12-16 18:06:54,470 DEBUG: reading modalias file /lib/modules/3.0.0-14-generic/modules.alias
2011-12-16 18:06:54,535 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-16 18:06:54,535 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-16 18:06:54,576 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-16 18:06:54,587 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-16 18:06:54,592 DEBUG: Software modem not available
2011-12-16 18:06:54,592 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-16 18:06:54,604 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-16 18:06:54,605 DEBUG: Firmware for DVB cards not available
2011-12-16 18:06:54,605 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-16 18:06:54,607 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-16 18:06:54,608 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-16 18:06:54,608 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-16 18:06:54,608 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-16 18:06:54,615 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-16 18:06:54,615 DEBUG: fglrx.available: falling back to default
2011-12-16 18:06:54,676 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-16 18:06:54,678 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-16 18:06:54,682 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-16 18:06:54,682 DEBUG: fglrx.available: falling back to default
2011-12-16 18:06:54,707 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-16 18:06:54,707 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-16 18:06:54,709 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-16 18:06:54,710 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-16 18:06:54,728 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-16 18:06:54,728 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-16 18:06:54,735 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-16 18:06:54,753 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-16 18:06:54,754 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-16 18:06:54,754 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-16 18:06:54,758 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-16 18:06:54,761 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-16 18:06:54,761 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,785 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-16 18:06:54,787 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-16 18:06:54,792 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-16 18:06:54,792 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,829 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-16 18:06:54,832 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-16 18:06:54,835 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-16 18:06:54,835 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,878 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-16 18:06:54,878 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-16 18:06:54,884 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-16 18:06:54,888 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-16 18:06:54,888 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,925 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-16 18:06:54,928 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-16 18:06:54,931 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-16 18:06:54,932 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,952 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-16 18:06:54,955 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-16 18:06:54,958 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-16 18:06:54,959 DEBUG: nvidia.available: falling back to default
2011-12-16 18:06:54,984 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-16 18:06:54,985 DEBUG: all custom handlers loaded
2011-12-16 18:06:54,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-16 18:06:54,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2011-12-16 18:06:55,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp921Bd0115dc00dsc00dp00ic03isc00ip00')
2011-12-16 18:06:55,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-16 18:06:55,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-16 18:06:55,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A34sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00001309bc0Csc00i10')
2011-12-16 18:06:55,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-16 18:06:55,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-12-16 18:06:55,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2011-12-16 18:06:55,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr786G3v03.15:bd10/29/2010:svnHewlett-Packard:pnHPZ400Workstation:pvr:rvnHewlett-Packard:rn0B4Ch:rvrD:cvnHewlett-Packard:ct6:cvr:')
2011-12-16 18:06:55,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp911Bd0101dc09dsc00dp02ic09isc00ip02')
2011-12-16 18:06:55,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-16 18:06:55,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C28sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0700:')
2011-12-16 18:06:55,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-12-16 18:06:55,271 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:41227C2D-80E1-423F-8B8E-87E32755A0EB')
2011-12-16 18:06:55,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A37sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-16 18:06:55,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-16 18:06:55,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-16 18:06:55,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C2Asv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-16 18:06:55,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C1Csv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d0000244Esv0000103Csd00001309bc06sc04i01')
2011-12-16 18:06:55,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C33sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'platform:pcspkr')
2011-12-16 18:06:55,287 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-16 18:06:55,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,287 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-16 18:06:55,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2011-12-16 18:06:55,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-16 18:06:55,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:ABBC0F5B-8EA1-11D1-00A0-C90629100000')
2011-12-16 18:06:55,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C11sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A16sv0000103Csd00001309bc06sc01i00')
2011-12-16 18:06:55,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-16 18:06:55,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A3Csv0000103Csd00001309bc0Csc03i20')
2011-12-16 18:06:55,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8232DE3F-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-16 18:06:55,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-16 18:06:55,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-16 18:06:55,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C21sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v000014E4d00001684sv0000103Csd00001309bc02sc00i00')
2011-12-16 18:06:55,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2011-12-16 18:06:55,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A3Esv0000103Csd00001309bc04sc03i00')
2011-12-16 18:06:55,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-16 18:06:55,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp0304d0110dc00dsc00dp00ic03isc01ip02')
2011-12-16 18:06:55,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-16 18:06:55,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-16 18:06:55,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-16 18:06:55,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002822sv0000103Csd00001309bc01sc04i00')
2011-12-16 18:06:55,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-16 18:06:55,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2011-12-16 18:06:55,339 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-16 18:06:55,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,339 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-16 18:06:55,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2011-12-16 18:06:55,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-16 18:06:55,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C41sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-16 18:06:55,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8232DE3E-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C19sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C30sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00001002d0000AA60sv0000103Csd0000AA60bc04sc03i00')
2011-12-16 18:06:55,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-16 18:06:55,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'platform:hp-wmi')
2011-12-16 18:06:55,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C31sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2011-12-16 18:06:55,575 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-16 18:06:55,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8232DE3C-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C18sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00001002d000068C9sv0000103Csd0000210Abc03sc00i00')
2011-12-16 18:06:55,580 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-16 18:06:55,611 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,611 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:55,580 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-16 18:06:55,620 DEBUG: fglrx.available: falling back to default
2011-12-16 18:06:55,667 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,667 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:55,635 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-16 18:06:55,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-16 18:06:55,699 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,699 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:55,667 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-16 18:06:55,702 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-16 18:06:55,708 DEBUG: fglrx.available: falling back to default
2011-12-16 18:06:55,756 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,756 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:55,728 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-16 18:06:55,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-16 18:06:55,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2011-12-16 18:06:55,787 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,787 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:55,757 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-16 18:06:55,795 DEBUG: fglrx.available: falling back to default
2011-12-16 18:06:55,839 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:55,839 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:55,811 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-16 18:06:55,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A36sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-16 18:06:55,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2011-12-16 18:06:55,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-16 18:06:55,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0003v05ACp0304e0110-e0,1,2,4,14,k110,111,112,113,r0,1,6,8,am4,lsfw')
2011-12-16 18:06:55,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0F13:PNP0F0E:')
2011-12-16 18:06:55,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-16 18:06:55,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2011-12-16 18:06:55,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C10sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C32sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-16 18:06:55,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C20sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:6FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-12-16 18:06:55,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-16 18:06:55,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:C9B590D8-E7E4-4DC5-BB0F-CB8A3522027E')
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0003:')
2011-12-16 18:06:55,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A3Asv0000103Csd00001309bc0Csc03i20')
2011-12-16 18:06:55,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C29sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A35sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C01sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-16 18:06:55,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v0BDAp0181d8197dc00dsc00dp00ic08isc06ip50')
2011-12-16 18:06:55,887 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2011-12-16 18:06:55,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2011-12-16 18:06:55,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C22sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003405sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A39sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2011-12-16 18:06:55,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2011-12-16 18:06:55,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-16 18:06:55,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00002C23sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-12-16 18:06:55,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-16 18:06:55,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-16 18:06:55,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-16 18:06:55,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25dc320> about HardwareID('modalias', 'pci:v00008086d00003A38sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-16 18:06:55,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2011-12-16 18:06:55,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp921Bd0115dc00dsc00dp00ic03isc00ip00')
2011-12-16 18:06:55,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-16 18:06:55,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A34sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00001309bc0Csc00i10')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr786G3v03.15:bd10/29/2010:svnHewlett-Packard:pnHPZ400Workstation:pvr:rvnHewlett-Packard:rn0B4Ch:rvrD:cvnHewlett-Packard:ct6:cvr:')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp911Bd0101dc09dsc00dp02ic09isc00ip02')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C28sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0700:')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:41227C2D-80E1-423F-8B8E-87E32755A0EB')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A37sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C2Asv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C1Csv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d0000244Esv0000103Csd00001309bc06sc04i01')
2011-12-16 18:06:55,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C33sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'platform:pcspkr')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:ABBC0F5B-8EA1-11D1-00A0-C90629100000')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C11sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A16sv0000103Csd00001309bc06sc01i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A3Csv0000103Csd00001309bc0Csc03i20')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8232DE3F-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C21sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v000014E4d00001684sv0000103Csd00001309bc02sc00i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A3Esv0000103Csd00001309bc04sc03i00')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp0304d0110dc00dsc00dp00ic03isc01ip02')
2011-12-16 18:06:55,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002822sv0000103Csd00001309bc01sc04i00')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,902 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C41sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,904 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-16 18:06:55,904 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8232DE3E-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,904 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C19sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C30sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00001002d0000AA60sv0000103Csd0000AA60bc04sc03i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'platform:hp-wmi')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C31sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8232DE3C-663D-4327-A8F4-E293ADB9BF05')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C18sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00001002d000068C9sv0000103Csd0000210Abc03sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A36sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0003v05ACp0304e0110-e0,1,2,4,14,k110,111,112,113,r0,1,6,8,am4,lsfw')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0F13:PNP0F0E:')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-16 18:06:55,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C10sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C32sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C20sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:6FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:C9B590D8-E7E4-4DC5-BB0F-CB8A3522027E')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0003:')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A3Asv0000103Csd00001309bc0Csc03i20')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C29sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A35sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C01sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v0BDAp0181d8197dc00dsc00dp00ic08isc06ip50')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C22sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003405sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A39sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00002C23sv0000103Csd00001309bc06sc00i00')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-16 18:06:55,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x27e7638> about HardwareID('modalias', 'pci:v00008086d00003A38sv0000103Csd00001309bc0Csc03i00')
2011-12-16 18:06:56,003 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,003 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,051 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,051 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,080 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,080 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:56,203 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,203 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:56,321 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,321 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,371 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,371 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,439 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,439 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,501 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,501 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:06:56,532 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,532 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:56,723 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:56,724 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:06:59,372 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:06:59,372 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:04,667 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-12-16 18:07:04,767 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-12-16 18:07:04,826 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:04,826 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:04,859 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:04,859 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,455 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,455 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,491 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,491 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,533 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,533 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-16 18:07:06,642 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,642 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,666 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,666 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,708 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,709 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,730 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,730 DEBUG: fglrx_updates is not the alternative in use
2011-12-16 18:07:06,766 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-16 18:07:06,766 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking


```


Please help.

---

### Post by zvacet on 2011-12-18
Well, I can not help you reading log file,but in my case I have two choices to install fglrx and second one was right.Check if you have two choices under additional hardware driver and try other one.

---

### Post by Townley89 on 2011-12-29
I've had the same issue. While the second driver can activate, it does not seem to save settings, particularly pertaining to my multi-monitor display (when I try to change it from mirror displays to extend displays, it simply crashes) . Whereas before the post-release driver could apply some settings and request a restart to change the others, this is not the case with the second driver option. 

Any thoughts on what could be the issue with the post release? I'll include my log file from jockey.log as well. Note that I used to have an NVidia card.  


[PHP]
2011-12-28 10:03:29,344 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48>
2011-12-28 10:03:35,091 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-12-28 10:03:35,390 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-28 10:03:35,399 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-28 10:03:35,469 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-28 10:03:35,510 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-28 10:03:35,581 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-28 10:03:35,587 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-28 10:03:35,587 DEBUG: fglrx.available: falling back to default
2011-12-28 10:03:35,817 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:03:35,829 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-28 10:03:35,829 DEBUG: fglrx.available: falling back to default
2011-12-28 10:03:35,891 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-28 10:03:35,892 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-28 10:03:35,954 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-28 10:03:35,955 DEBUG: Firmware for DVB cards not available
2011-12-28 10:03:35,955 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-28 10:03:35,958 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-28 10:03:35,958 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-28 10:03:35,999 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-28 10:03:36,000 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-28 10:03:36,005 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-28 10:03:36,006 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-28 10:03:36,006 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-28 10:03:36,006 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-28 10:03:36,032 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-28 10:03:36,057 DEBUG: Software modem not available
2011-12-28 10:03:36,058 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-28 10:03:36,090 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-28 10:03:36,095 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-28 10:03:36,095 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,141 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:03:36,146 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-28 10:03:36,153 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-28 10:03:36,153 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,197 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:03:36,200 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-28 10:03:36,205 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-28 10:03:36,206 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,250 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:03:36,251 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-28 10:03:36,265 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-28 10:03:36,270 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-28 10:03:36,271 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,325 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:03:36,330 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-28 10:03:36,335 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-28 10:03:36,335 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,384 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:03:36,388 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-28 10:03:36,393 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-28 10:03:36,393 DEBUG: nvidia.available: falling back to default
2011-12-28 10:03:36,443 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:03:36,444 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-28 10:03:36,452 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-28 10:03:36,477 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-28 10:03:36,478 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-28 10:03:36,478 DEBUG: all custom handlers loaded
2011-12-28 10:03:36,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:03:36,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:03:36,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:36,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:03:36,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:03:36,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:03:36,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2011-12-28 10:03:36,828 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:03:36,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-28 10:03:36,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-28 10:03:36,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:36,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:03:36,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:03:36,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:03:36,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:03:36,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:36,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:36,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:03:36,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:36,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:03:36,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:03:36,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:03:36,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:03:36,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:03:37,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:03:37,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-12-28 10:03:37,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:37,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:03:37,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:03:37,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:03:37,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:03:37,892 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-28 10:03:38,294 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:38,294 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:03:37,893 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:03:38,299 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-28 10:03:38,307 DEBUG: fglrx.available: falling back to default
2011-12-28 10:03:38,374 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:38,375 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:03:38,331 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:03:38,375 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-28 10:03:38,404 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:38,405 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:03:38,375 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:03:38,636 DEBUG: fglrx.available: falling back to default
2011-12-28 10:03:38,698 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:38,698 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:03:38,660 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:03:38,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-28 10:03:38,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:38,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-12-28 10:03:38,961 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:38,961 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:03:38,916 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:03:39,185 DEBUG: fglrx.available: falling back to default
2011-12-28 10:03:39,242 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:39,242 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:03:39,206 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:03:39,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:03:39,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:03:39,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:03:39,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:03:39,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:03:39,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,519 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:03:39,519 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:03:39,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:03:39,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:03:39,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:03:39,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:03:39,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:03:39,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:03:39,556 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:03:39,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,557 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:03:39,557 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:03:39,558 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,558 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:03:39,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-12-28 10:03:39,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:03:39,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:03:39,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:03:39,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:03:39,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:03:39,616 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:03:39,616 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:03:39,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:03:39,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:03:39,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,631 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-12-28 10:03:39,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:03:39,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,633 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-28 10:03:39,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:03:39,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-12-28 10:03:39,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:03:39,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-28 10:03:39,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:03:39,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:03:39,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:03:39,662 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:03:39,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:03:39,673 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:03:39,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:03:39,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:03:39,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:03:39,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:03:39,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:03:39,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:03:39,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:03:39,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2011-12-28 10:03:39,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:03:39,700 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:03:39,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,701 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-28 10:03:39,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:03:39,703 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:03:39,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:03:39,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:03:39,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:03:39,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:03:39,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-12-28 10:03:39,716 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,716 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-12-28 10:03:39,716 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:03:39,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x29c5b48> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:03:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:03:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:03:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:03:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:03:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:03:39,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:03:39,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:03:39,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:03:39,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:03:39,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:03:39,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:03:39,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:03:39,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:03:39,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:03:39,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:03:39,722 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:03:39,722 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:03:39,722 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:03:39,722 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:03:39,722 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:03:39,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:03:39,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:03:39,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:03:39,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:03:39,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:03:39,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:03:39,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:03:39,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:03:39,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:03:39,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:03:39,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:03:39,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:03:39,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:03:39,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:03:39,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:03:39,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:03:39,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:03:39,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2bd7680> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:03:39,774 DEBUG: handler xorg:fglrx_updates previously unseen
2011-12-28 10:03:39,774 DEBUG: handler xorg:fglrx previously unseen
2011-12-28 10:03:39,974 DEBUG: handler xorg:fglrx previously unused
2011-12-28 10:03:39,974 DEBUG: writing back check cache /var/cache/jockey/check
2011-12-28 10:03:40,000 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:40,001 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:03:40,047 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:40,047 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:03:40,266 DEBUG: xorg:fglrx is already enabled or not available, not announcing
2011-12-28 10:03:40,322 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:40,322 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:03:40,389 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:03:40,389 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:07:55,344 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:07:55,344 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:07:55,465 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:07:55,466 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:07:56,023 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:07:56,023 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:07:56,104 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:07:56,104 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:07:56,152 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:07:56,152 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:08:06,449 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:08:06,449 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:08:06,957 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:08:06,957 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:08:08,286 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:08:08,286 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:08:10,585 DEBUG: Shutting down
2011-12-28 10:33:57,870 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48>
2011-12-28 10:34:03,138 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-12-28 10:34:03,444 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-28 10:34:03,453 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-28 10:34:03,525 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-28 10:34:03,564 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-28 10:34:03,623 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-28 10:34:03,628 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-28 10:34:03,629 DEBUG: fglrx.available: falling back to default
2011-12-28 10:34:03,789 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:34:03,798 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-28 10:34:03,798 DEBUG: fglrx.available: falling back to default
2011-12-28 10:34:03,866 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-28 10:34:03,866 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-28 10:34:03,903 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-28 10:34:03,903 DEBUG: Firmware for DVB cards not available
2011-12-28 10:34:03,904 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-28 10:34:03,910 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-28 10:34:03,910 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-28 10:34:03,934 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-28 10:34:03,934 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-28 10:34:03,938 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-28 10:34:03,939 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-28 10:34:03,939 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-28 10:34:03,939 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-28 10:34:03,963 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-28 10:34:03,990 DEBUG: Software modem not available
2011-12-28 10:34:03,990 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-28 10:34:04,024 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-28 10:34:04,029 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-28 10:34:04,030 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,073 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:34:04,076 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-28 10:34:04,080 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-28 10:34:04,080 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,129 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:34:04,135 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-28 10:34:04,141 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-28 10:34:04,141 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,190 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:34:04,190 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-28 10:34:04,248 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-28 10:34:04,252 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-28 10:34:04,252 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,291 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:34:04,297 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-28 10:34:04,305 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-28 10:34:04,305 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,341 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:34:04,344 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-28 10:34:04,351 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-28 10:34:04,351 DEBUG: nvidia.available: falling back to default
2011-12-28 10:34:04,394 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:34:04,395 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-28 10:34:04,398 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-28 10:34:04,422 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-28 10:34:04,422 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-28 10:34:04,422 DEBUG: all custom handlers loaded
2011-12-28 10:34:04,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:34:04,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:34:04,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:04,595 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:34:04,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:34:04,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:34:04,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2011-12-28 10:34:04,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:34:04,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-28 10:34:04,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-28 10:34:04,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:04,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:34:04,768 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:34:04,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:34:04,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:34:04,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:04,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:04,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:34:04,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:04,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:34:04,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:34:04,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:34:04,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:34:04,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:34:05,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:34:05,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-12-28 10:34:05,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:05,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:34:05,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:34:05,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:34:05,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:34:05,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-28 10:34:05,990 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:05,990 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:05,693 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:34:05,993 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-28 10:34:05,996 DEBUG: fglrx.available: falling back to default
2011-12-28 10:34:06,059 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:06,059 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:06,025 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:34:06,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-28 10:34:06,103 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:06,103 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:06,060 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:34:06,328 DEBUG: fglrx.available: falling back to default
2011-12-28 10:34:06,389 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:06,390 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:06,356 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:34:06,606 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-28 10:34:06,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:06,607 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-12-28 10:34:06,651 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:06,651 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:06,607 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:34:06,881 DEBUG: fglrx.available: falling back to default
2011-12-28 10:34:06,950 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:06,951 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:06,907 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:34:07,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:34:07,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:34:07,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:34:07,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:34:07,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:34:07,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,212 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:34:07,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:34:07,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:34:07,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:34:07,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:34:07,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:34:07,238 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:34:07,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:34:07,250 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:34:07,250 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,250 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:34:07,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:34:07,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:34:07,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,294 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-12-28 10:34:07,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:34:07,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:34:07,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:34:07,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:34:07,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:34:07,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:34:07,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:34:07,322 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:34:07,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,323 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:34:07,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-12-28 10:34:07,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:34:07,325 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-28 10:34:07,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:34:07,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-12-28 10:34:07,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:34:07,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-28 10:34:07,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:34:07,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:34:07,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:34:07,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:34:07,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:34:07,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:34:07,367 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:34:07,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:34:07,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:34:07,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:34:07,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:34:07,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:34:07,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:34:07,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2011-12-28 10:34:07,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:34:07,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:34:07,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-28 10:34:07,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:34:07,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:34:07,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:34:07,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:34:07,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:34:07,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:34:07,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-12-28 10:34:07,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-12-28 10:34:07,410 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:34:07,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xe10b48> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:34:07,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:34:07,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:34:07,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:34:07,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:34:07,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:34:07,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:34:07,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:34:07,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:34:07,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:34:07,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:34:07,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:34:07,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:34:07,413 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:34:07,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:34:07,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:34:07,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:34:07,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:34:07,414 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:34:07,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:34:07,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:34:07,415 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:34:07,416 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:34:07,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:34:07,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:34:07,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:34:07,417 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:34:07,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:34:07,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:34:07,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:34:07,418 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:34:07,419 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:34:07,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:34:07,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:34:07,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:34:07,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:34:07,420 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:34:07,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:34:07,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:34:07,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:34:07,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:34:07,421 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:34:07,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:34:07,422 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1022680> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:34:07,507 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:07,507 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:07,595 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:07,595 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:08,099 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:08,100 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:08,176 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:08,176 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:08,225 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:08,225 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:34:19,247 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:19,247 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:20,332 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:34:20,332 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:34:25,035 DEBUG: Installing package: fglrx-updates
2011-12-28 10:34:26,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-12-28 10:34:26,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-12-28 10:34:26,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-12-28 10:34:26,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-12-28 10:34:27,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.004323
2011-12-28 10:34:27,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.056291
2011-12-28 10:34:27,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.061285
2011-12-28 10:34:28,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.209636
2011-12-28 10:34:28,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.401058
2011-12-28 10:34:29,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.616407
2011-12-28 10:34:29,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.831756
2011-12-28 10:34:30,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.056676
2011-12-28 10:34:30,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.403627
2011-12-28 10:34:31,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.681188
2011-12-28 10:34:31,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.111886
2011-12-28 10:34:32,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.566512
2011-12-28 10:34:32,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.080957
2011-12-28 10:34:33,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.573867
2011-12-28 10:34:33,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.227093
2011-12-28 10:34:34,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.803749
2011-12-28 10:34:34,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.411512
2011-12-28 10:34:35,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.095844
2011-12-28 10:34:35,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.483472
2011-12-28 10:34:36,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.734712
2011-12-28 10:34:36,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.765818
2011-12-28 10:34:37,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.844780
2011-12-28 10:34:37,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.038594
2011-12-28 10:34:38,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.220444
2011-12-28 10:34:38,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.612858
2011-12-28 10:34:39,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.012450
2011-12-28 10:34:39,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.634570
2011-12-28 10:34:40,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.132265
2011-12-28 10:34:40,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.194477
2011-12-28 10:34:41,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.292581
2011-12-28 10:34:41,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.696958
2011-12-28 10:34:42,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.079801
2011-12-28 10:34:42,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.567925
2011-12-28 10:34:43,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.156546
2011-12-28 10:34:43,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.654242
2011-12-28 10:34:44,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.204578
2011-12-28 10:34:44,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.663989
2011-12-28 10:34:45,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.255003
2011-12-28 10:34:45,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.606740
2011-12-28 10:34:46,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.063758
2011-12-28 10:34:46,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.329355
2011-12-28 10:34:47,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.559061
2011-12-28 10:34:47,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.561454
2011-12-28 10:34:48,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.633237
2011-12-28 10:34:48,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.805516
2011-12-28 10:34:49,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.032829
2011-12-28 10:34:49,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.398922
2011-12-28 10:34:50,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.748266
2011-12-28 10:34:50,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.116752
2011-12-28 10:34:51,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.540272
2011-12-28 10:34:51,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.875260
2011-12-28 10:34:52,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.332278
2011-12-28 10:34:52,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.724692
2011-12-28 10:34:53,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.107535
2011-12-28 10:34:53,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.533447
2011-12-28 10:34:54,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.909112
2011-12-28 10:34:54,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.330239
2011-12-28 10:34:55,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.547981
2011-12-28 10:34:55,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.547981
2011-12-28 10:34:56,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.595836
2011-12-28 10:34:56,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.696332
2011-12-28 10:34:57,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.926038
2011-12-28 10:34:57,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.153351
2011-12-28 10:34:58,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.404591
2011-12-28 10:34:58,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.718044
2011-12-28 10:34:59,090 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.244452
2011-12-28 10:34:59,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.627295
2011-12-28 10:35:00,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.933569
2011-12-28 10:35:00,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.383410
2011-12-28 10:35:01,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.785394
2011-12-28 10:35:01,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.323767
2011-12-28 10:35:02,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.754465
2011-12-28 10:35:02,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.280874
2011-12-28 10:35:03,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.735500
2011-12-28 10:35:03,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.369583
2011-12-28 10:35:04,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.907956
2011-12-28 10:35:04,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.446328
2011-12-28 10:35:05,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.168944
2011-12-28 10:35:05,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.527859
2011-12-28 10:35:06,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.599642
2011-12-28 10:35:06,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.692960
2011-12-28 10:35:07,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.903523
2011-12-28 10:35:07,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.149978
2011-12-28 10:35:08,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.422754
2011-12-28 10:35:08,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.688351
2011-12-28 10:35:09,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.889343
2011-12-28 10:35:09,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.245866
2011-12-28 10:35:10,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.616745
2011-12-28 10:35:10,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.999587
2011-12-28 10:35:11,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.322611
2011-12-28 10:35:11,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.860984
2011-12-28 10:35:12,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.184007
2011-12-28 10:35:12,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.672132
2011-12-28 10:35:13,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.330143
2011-12-28 10:35:13,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.882872
2011-12-28 10:35:14,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.414066
2011-12-28 10:35:14,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.665307
2011-12-28 10:35:15,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.741875
2011-12-28 10:35:15,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.849550
2011-12-28 10:35:16,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.091219
2011-12-28 10:35:16,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.414243
2011-12-28 10:35:17,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.789907
2011-12-28 10:35:17,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.242140
2011-12-28 10:35:18,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.706337
2011-12-28 10:35:18,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.244710
2011-12-28 10:35:19,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.783082
2011-12-28 10:35:19,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.405202
2011-12-28 10:35:20,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.919647
2011-12-28 10:35:20,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.398200
2011-12-28 10:35:21,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.895896
2011-12-28 10:35:21,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.116030
2011-12-28 10:35:22,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.139958
2011-12-28 10:35:22,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.204563
2011-12-28 10:35:23,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.352914
2011-12-28 10:35:23,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.537157
2011-12-28 10:35:24,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.867359
2011-12-28 10:35:24,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.168848
2011-12-28 10:35:25,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.494264
2011-12-28 10:35:25,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.922569
2011-12-28 10:35:26,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.370017
2011-12-28 10:35:26,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.843785
2011-12-28 10:35:27,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.389336
2011-12-28 10:35:27,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.867889
2011-12-28 10:35:28,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.025812
2011-12-28 10:35:28,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.095202
2011-12-28 10:35:29,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.104773
2011-12-28 10:35:29,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.119130
2011-12-28 10:35:30,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.224411
2011-12-28 10:35:30,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.351228
2011-12-28 10:35:31,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.523507
2011-12-28 10:35:31,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.781926
2011-12-28 10:35:32,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.071451
2011-12-28 10:35:32,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.485400
2011-12-28 10:35:33,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.832351
2011-12-28 10:35:33,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.181695
2011-12-28 10:35:34,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.559752
2011-12-28 10:35:34,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.918667
2011-12-28 10:35:35,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.299117
2011-12-28 10:35:35,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.689138
2011-12-28 10:35:36,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.071981
2011-12-28 10:35:36,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.607961
2011-12-28 10:35:37,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.088907
2011-12-28 10:35:37,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.701455
2011-12-28 10:35:38,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.278112
2011-12-28 10:35:38,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.967229
2011-12-28 10:35:39,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.622847
2011-12-28 10:35:39,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.893230
2011-12-28 10:35:40,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.950656
2011-12-28 10:35:40,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.084651
2011-12-28 10:35:41,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.355034
2011-12-28 10:35:41,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.728306
2011-12-28 10:35:42,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.130291
2011-12-28 10:35:42,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.611237
2011-12-28 10:35:43,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.041935
2011-12-28 10:35:43,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.472633
2011-12-28 10:35:44,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.068432
2011-12-28 10:35:44,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.630732
2011-12-28 10:35:45,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.805404
2011-12-28 10:35:45,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.879580
2011-12-28 10:35:46,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.980076
2011-12-28 10:35:46,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.166712
2011-12-28 10:35:47,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.346170
2011-12-28 10:35:47,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.654837
2011-12-28 10:35:48,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.056822
2011-12-28 10:35:48,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.410951
2011-12-28 10:35:49,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.848827
2011-12-28 10:35:49,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.348916
2011-12-28 10:35:50,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.774828
2011-12-28 10:35:50,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.047604
2011-12-28 10:35:51,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.265346
2011-12-28 10:35:51,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.308415
2011-12-28 10:35:52,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.358664
2011-12-28 10:35:52,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.748685
2011-12-28 10:35:53,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.179383
2011-12-28 10:35:53,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.638794
2011-12-28 10:35:54,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.040779
2011-12-28 10:35:54,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.272877
2011-12-28 10:35:55,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.749038
2011-12-28 10:35:55,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.225199
2011-12-28 10:35:56,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.794677
2011-12-28 10:35:56,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.330657
2011-12-28 10:35:57,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.993453
2011-12-28 10:35:57,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.649072
2011-12-28 10:35:58,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.854850
2011-12-28 10:35:58,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.909883
2011-12-28 10:35:59,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.012772
2011-12-28 10:35:59,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.182659
2011-12-28 10:36:00,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.462613
2011-12-28 10:36:00,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.845455
2011-12-28 10:36:01,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.209156
2011-12-28 10:36:01,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.678138
2011-12-28 10:36:02,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.070552
2011-12-28 10:36:02,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.501250
2011-12-28 10:36:03,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.931948
2011-12-28 10:36:03,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.508605
2011-12-28 10:36:04,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.061334
2011-12-28 10:36:04,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.547066
2011-12-28 10:36:05,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.154829
2011-12-28 10:36:05,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.508958
2011-12-28 10:36:06,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.772163
2011-12-28 10:36:06,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.829589
2011-12-28 10:36:07,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.968370
2011-12-28 10:36:07,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.358391
2011-12-28 10:36:08,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.726877
2011-12-28 10:36:08,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.329854
2011-12-28 10:36:09,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.884976
2011-12-28 10:36:09,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.535809
2011-12-28 10:36:10,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.368492
2011-12-28 10:36:10,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.107857
2011-12-28 10:36:11,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.899863
2011-12-28 10:36:11,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.653584
2011-12-28 10:36:12,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.036427
2011-12-28 10:36:12,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.357058
2011-12-28 10:36:13,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.838004
2011-12-28 10:36:13,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.464909
2011-12-28 10:36:14,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.053530
2011-12-28 10:36:14,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.603866
2011-12-28 10:36:15,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.197273
2011-12-28 10:36:15,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.728193
2011-12-28 10:36:16,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.333837
2011-12-28 10:36:16,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.929636
2011-12-28 10:36:17,251 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.508686
2011-12-28 10:36:17,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.073379
2011-12-28 10:36:18,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.709855
2011-12-28 10:36:18,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.406150
2011-12-28 10:36:19,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.138337
2011-12-28 10:36:19,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.882487
2011-12-28 10:36:20,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.169619
2011-12-28 10:36:20,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.631423
2011-12-28 10:36:21,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.098013
2011-12-28 10:36:21,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.581352
2011-12-28 10:36:22,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.067084
2011-12-28 10:36:22,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.512138
2011-12-28 10:36:23,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.036154
2011-12-28 10:36:23,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.485995
2011-12-28 10:36:24,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.957370
2011-12-28 10:36:24,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.419174
2011-12-28 10:36:25,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.885763
2011-12-28 10:36:25,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.236609
2011-12-28 10:36:25,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.239430
2011-12-28 10:36:26,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.835229
2011-12-28 10:36:26,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.373602
2011-12-28 10:36:27,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.911974
2011-12-28 10:36:27,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.610662
2011-12-28 10:36:28,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.455309
2011-12-28 10:36:28,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.008038
2011-12-28 10:36:29,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.039144
2011-12-28 10:36:29,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.072643
2011-12-28 10:36:30,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.113320
2011-12-28 10:36:30,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.211424
2011-12-28 10:36:31,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.414809
2011-12-28 10:36:31,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.792866
2011-12-28 10:36:32,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.283383
2011-12-28 10:36:32,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.958144
2011-12-28 10:36:33,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.556335
2011-12-28 10:36:33,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.312450
2011-12-28 10:36:34,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.008745
2011-12-28 10:36:34,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.659578
2011-12-28 10:36:35,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.358266
2011-12-28 10:36:35,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2011-12-28 10:36:36,093 DEBUG: install progress dpkg-exec 0.000000
2011-12-28 10:36:37,627 DEBUG: install progress ubuntu-minimal 0.000000
2011-12-28 10:36:37,628 DEBUG: install progress ubuntu-minimal 3.030300
2011-12-28 10:36:37,825 DEBUG: install progress ubuntu-minimal 6.060610
2011-12-28 10:36:38,295 DEBUG: install progress ubuntu-minimal 9.090910
2011-12-28 10:36:39,649 DEBUG: install progress ubuntu-desktop 9.090910
2011-12-28 10:36:39,649 DEBUG: install progress ubuntu-desktop 12.121200
2011-12-28 10:36:39,812 DEBUG: install progress ubuntu-desktop 15.151500
2011-12-28 10:36:40,150 DEBUG: install progress ubuntu-desktop 18.181800
2011-12-28 10:36:40,950 DEBUG: install progress file-roller 18.181800
2011-12-28 10:36:40,950 DEBUG: install progress file-roller 21.212100
2011-12-28 10:36:41,068 DEBUG: install progress file-roller 24.242400
2011-12-28 10:36:44,558 DEBUG: install progress file-roller 27.272700
2011-12-28 10:36:44,980 DEBUG: install progress bzip2 27.272700
2011-12-28 10:36:46,298 DEBUG: install progress man-db 27.272700
2011-12-28 10:36:47,877 DEBUG: install progress libglib2.0-0 27.272700
2011-12-28 10:36:49,033 DEBUG: install progress gnome-menus 27.272700
2011-12-28 10:36:49,421 DEBUG: install progress desktop-file-utils 27.272700
2011-12-28 10:36:49,804 DEBUG: install progress bamfdaemon 27.272700
2011-12-28 10:36:50,142 DEBUG: install progress gconf2 27.272700
2011-12-28 10:36:50,517 DEBUG: install progress hicolor-icon-theme 27.272700
2011-12-28 10:36:52,293 DEBUG: install progress dpkg-exec 27.272700
2011-12-28 10:36:53,788 DEBUG: install progress libbz2-1.0 30.303000
2011-12-28 10:36:54,492 DEBUG: install progress libbz2-1.0 33.333300
2011-12-28 10:36:54,671 DEBUG: install progress libbz2-1.0 36.363600
2011-12-28 10:36:55,312 DEBUG: install progress dpkg-exec 36.363600
2011-12-28 10:36:55,423 DEBUG: install progress libbz2-1.0 36.363600
2011-12-28 10:36:55,694 DEBUG: install progress libbz2-1.0 39.393900
2011-12-28 10:36:55,948 DEBUG: install progress libbz2-1.0 42.424200
2011-12-28 10:36:56,309 DEBUG: install progress libc-bin 42.424200
2011-12-28 10:36:57,033 DEBUG: install progress dpkg-exec 42.424200
2011-12-28 10:36:57,473 DEBUG: install progress fglrx-amdcccle 42.424200
2011-12-28 10:36:57,573 DEBUG: install progress fglrx-amdcccle 45.454500
2011-12-28 10:36:57,672 DEBUG: install progress fglrx-amdcccle 48.484800
2011-12-28 10:36:58,131 DEBUG: install progress fglrx-amdcccle 51.515200
2011-12-28 10:36:59,280 DEBUG: install progress fglrx 51.515200
2011-12-28 10:36:59,381 DEBUG: install progress fglrx 54.545500
2011-12-28 10:37:19,303 DEBUG: install progress fglrx 57.575800
2011-12-28 10:37:20,694 DEBUG: install progress fglrx 60.606100
2011-12-28 10:37:21,079 DEBUG: install progress bamfdaemon 60.606100
2011-12-28 10:37:21,513 DEBUG: install progress gnome-menus 60.606100
2011-12-28 10:37:21,898 DEBUG: install progress ureadahead 60.606100
2011-12-28 10:37:22,272 DEBUG: install progress initramfs-tools 60.606100
2011-12-28 10:37:36,822 DEBUG: install progress libc-bin 60.606100
2011-12-28 10:37:38,946 DEBUG: install progress dpkg-exec 60.606100
2011-12-28 10:37:40,206 DEBUG: install progress fglrx-updates 60.606100
2011-12-28 10:37:40,206 DEBUG: install progress fglrx-updates 63.636400
2011-12-28 10:37:46,129 DEBUG: install progress fglrx-updates 66.666700
2011-12-28 10:37:46,334 DEBUG: install progress fglrx-updates 69.697000
2011-12-28 10:37:46,817 DEBUG: install progress fglrx-amdcccle-updates 69.697000
2011-12-28 10:37:46,917 DEBUG: install progress fglrx-amdcccle-updates 72.727300
2011-12-28 10:37:47,986 DEBUG: install progress fglrx-amdcccle-updates 75.757600
2011-12-28 10:37:48,141 DEBUG: install progress fglrx-amdcccle-updates 78.787900
2011-12-28 10:37:48,301 DEBUG: install progress ureadahead 78.787900
2011-12-28 10:37:48,959 DEBUG: install progress dpkg-exec 78.787900
2011-12-28 10:37:49,041 DEBUG: install progress fglrx-updates 78.787900
2011-12-28 10:37:49,757 DEBUG: install progress fglrx-updates 81.818200
2011-12-28 10:38:30,494 DEBUG: install progress fglrx-updates 84.848500
2011-12-28 10:38:31,747 DEBUG: install progress bamfdaemon 84.848500
2011-12-28 10:38:32,072 DEBUG: install progress gnome-menus 84.848500
2011-12-28 10:38:32,578 DEBUG: install progress fglrx-amdcccle-updates 84.848500
2011-12-28 10:38:32,845 DEBUG: install progress fglrx-amdcccle-updates 87.878800
2011-12-28 10:38:33,047 DEBUG: install progress fglrx-amdcccle-updates 90.909100
2011-12-28 10:38:33,266 DEBUG: install progress initramfs-tools 90.909100
2011-12-28 10:38:48,464 DEBUG: install progress libc-bin 90.909100
2011-12-28 10:38:53,173 DEBUG: (Reading database ... 131973 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing ubuntu-desktop ...
Removing file-roller ...
Removing bzip2 ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
(Reading database ... 131671 files and directories currently installed.)
Preparing to replace libbz2-1.0 1.0.5-6ubuntu1 (using .../libbz2-1.0_1.0.5-6ubuntu1_amd64.deb) ...
Unpacking replacement libbz2-1.0 ...
Setting up libbz2-1.0 (1.0.5-6ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 131670 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 131425 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Loading new fglrx-updates-8.911 DKMS files...
First Installation: checking all kernels...
Building for 3.0.0-12-generic and 3.0.0-14-generic
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
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-12-28 10:38:53,716 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-12-28 10:38:53,944 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-12-28 10:38:54,032 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:38:54,032 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:38:54,075 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:38:54,075 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:37,941 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:37,941 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:37,983 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:37,983 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:38,048 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,049 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:40:38,543 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,544 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:38,574 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,575 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:38,654 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,654 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:38,709 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,709 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:38,769 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:38,769 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:40:43,008 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:43,009 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:43,058 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:43,058 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:48,632 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-12-28 10:40:48,863 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-12-28 10:40:48,937 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:48,937 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:48,992 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:48,992 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:51,517 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:51,517 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:51,566 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:51,566 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:51,621 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:51,622 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:40:52,119 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:52,119 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:52,169 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:52,169 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:52,227 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:52,227 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:52,269 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:52,269 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:40:52,327 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:40:52,328 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:41:37,414 DEBUG: Shutting down
2011-12-28 10:42:13,864 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48>
2011-12-28 10:42:19,140 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-12-28 10:42:19,404 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-28 10:42:19,404 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-28 10:42:19,500 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-28 10:42:19,522 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-28 10:42:19,537 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-28 10:42:19,538 DEBUG: fglrx.available: falling back to default
2011-12-28 10:42:19,688 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:42:19,694 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-28 10:42:19,701 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-28 10:42:19,702 DEBUG: fglrx.available: falling back to default
2011-12-28 10:42:19,767 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-28 10:42:19,767 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-28 10:42:19,790 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-28 10:42:19,790 DEBUG: Firmware for DVB cards not available
2011-12-28 10:42:19,790 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-28 10:42:19,794 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-28 10:42:19,794 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-28 10:42:19,817 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-28 10:42:19,817 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-28 10:42:19,823 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-28 10:42:19,823 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-28 10:42:19,823 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-28 10:42:19,823 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-28 10:42:19,849 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-28 10:42:19,855 DEBUG: Software modem not available
2011-12-28 10:42:19,855 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-28 10:42:19,862 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-28 10:42:19,871 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-28 10:42:19,871 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:19,918 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:42:19,921 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-28 10:42:19,925 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-28 10:42:19,926 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:19,965 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:42:19,970 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-28 10:42:19,975 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-28 10:42:19,975 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:20,018 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:42:20,019 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-28 10:42:20,022 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-28 10:42:20,026 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-28 10:42:20,026 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:20,067 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:42:20,069 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-28 10:42:20,073 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-28 10:42:20,073 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:20,123 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-28 10:42:20,126 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-28 10:42:20,131 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-28 10:42:20,131 DEBUG: nvidia.available: falling back to default
2011-12-28 10:42:20,170 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-28 10:42:20,170 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-28 10:42:20,173 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-28 10:42:20,201 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-28 10:42:20,202 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-28 10:42:20,202 DEBUG: all custom handlers loaded
2011-12-28 10:42:20,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:42:20,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:42:20,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:20,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:42:20,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:42:20,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:42:20,379 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2011-12-28 10:42:20,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:42:20,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-28 10:42:20,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-28 10:42:20,382 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:20,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:42:20,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:42:20,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,519 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:42:20,519 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:42:20,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:20,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:20,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:42:20,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:20,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:42:20,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:42:20,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:42:20,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:42:20,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:42:21,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:42:21,446 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-12-28 10:42:21,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:42:21,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:42:21,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:42:21,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:42:21,458 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-28 10:42:21,498 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,498 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:21,458 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:42:21,505 DEBUG: fglrx.available: falling back to default
2011-12-28 10:42:21,565 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,565 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:21,530 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:42:21,565 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-28 10:42:21,610 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,610 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:21,565 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:42:21,615 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-28 10:42:21,623 DEBUG: fglrx.available: falling back to default
2011-12-28 10:42:21,680 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,680 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:21,646 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-28 10:42:21,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-28 10:42:21,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2011-12-28 10:42:21,725 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,725 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:21,680 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:42:21,732 DEBUG: fglrx.available: falling back to default
2011-12-28 10:42:21,805 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:21,805 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:21,756 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-28 10:42:21,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:42:21,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:42:21,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:21,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:42:21,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:21,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:42:21,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:42:21,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:42:21,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:42:21,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:42:21,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:42:21,846 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:21,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:42:21,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:42:21,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:42:21,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:21,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:42:21,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:42:21,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:42:21,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:42:21,883 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:21,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:42:21,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:21,924 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-12-28 10:42:21,924 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:42:21,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:42:21,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:42:21,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:42:21,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:21,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:42:21,939 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:42:21,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:21,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:21,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:42:21,952 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:42:21,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-28 10:42:21,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:21,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-12-28 10:42:21,955 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:42:21,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:21,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-28 10:42:21,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:42:21,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-12-28 10:42:21,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:42:21,982 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-28 10:42:21,982 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:42:21,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:42:21,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:42:21,985 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-28 10:42:21,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:42:21,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-28 10:42:21,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:42:21,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:42:21,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:42:21,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:21,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-28 10:42:21,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:42:22,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:42:22,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:42:22,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2011-12-28 10:42:22,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:42:22,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-28 10:42:22,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-28 10:42:22,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:42:22,027 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-28 10:42:22,027 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-28 10:42:22,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:42:22,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-28 10:42:22,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:42:22,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-12-28 10:42:22,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-12-28 10:42:22,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-12-28 10:42:22,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2766b48> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:42:22,041 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-28 10:42:22,041 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-28 10:42:22,041 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-28 10:42:22,041 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-28 10:42:22,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-28 10:42:22,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'platform:pcspkr')
2011-12-28 10:42:22,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:22,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:42:22,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-28 10:42:22,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-28 10:42:22,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:22,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-28 10:42:22,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'platform:regulatory')
2011-12-28 10:42:22,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-28 10:42:22,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-28 10:42:22,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-28 10:42:22,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-28 10:42:22,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-28 10:42:22,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-28 10:42:22,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:42:22,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-28 10:42:22,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-28 10:42:22,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-28 10:42:22,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-28 10:42:22,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-28 10:42:22,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-28 10:42:22,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-28 10:42:22,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-28 10:42:22,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-28 10:42:22,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-28 10:42:22,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-28 10:42:22,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-28 10:42:22,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-28 10:42:22,050 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-28 10:42:22,050 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-28 10:42:22,050 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-28 10:42:22,050 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-28 10:42:22,050 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-28 10:42:22,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-28 10:42:22,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-28 10:42:22,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-28 10:42:22,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-28 10:42:22,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-28 10:42:22,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-28 10:42:22,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-28 10:42:22,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-28 10:42:22,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-28 10:42:22,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-28 10:42:22,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x297d4d0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-28 10:42:22,127 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:22,127 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:22,199 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:22,199 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:22,476 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:22,477 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:22,557 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:22,557 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:42:22,622 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:22,622 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:24,800 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:24,800 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:26,717 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:42:26,717 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:42:31,481 DEBUG: Installing package: fglrx
2011-12-28 10:42:33,181 DEBUG: install progress dpkg-exec 0.000000
2011-12-28 10:42:33,732 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2011-12-28 10:42:33,833 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2011-12-28 10:42:33,892 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2011-12-28 10:42:34,207 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2011-12-28 10:42:35,172 DEBUG: install progress fglrx-updates 18.750000
2011-12-28 10:42:35,272 DEBUG: install progress fglrx-updates 25.000000
2011-12-28 10:42:39,779 DEBUG: install progress fglrx-updates 31.250000
2011-12-28 10:42:41,062 DEBUG: install progress fglrx-updates 37.500000
2011-12-28 10:42:41,352 DEBUG: install progress bamfdaemon 37.500000
2011-12-28 10:42:41,653 DEBUG: install progress gnome-menus 37.500000
2011-12-28 10:42:41,944 DEBUG: install progress ureadahead 37.500000
2011-12-28 10:42:42,210 DEBUG: install progress initramfs-tools 37.500000
2011-12-28 10:42:57,540 DEBUG: install progress libc-bin 37.500000
2011-12-28 10:42:58,701 DEBUG: install progress dpkg-exec 37.500000
2011-12-28 10:43:00,622 DEBUG: install progress fglrx 37.500000
2011-12-28 10:43:00,623 DEBUG: install progress fglrx 43.750000
2011-12-28 10:43:08,487 DEBUG: install progress fglrx 50.000000
2011-12-28 10:43:08,715 DEBUG: install progress fglrx 56.250000
2011-12-28 10:43:09,248 DEBUG: install progress fglrx-amdcccle 56.250000
2011-12-28 10:43:09,349 DEBUG: install progress fglrx-amdcccle 62.500000
2011-12-28 10:43:10,852 DEBUG: install progress fglrx-amdcccle 68.750000
2011-12-28 10:43:11,110 DEBUG: install progress fglrx-amdcccle 75.000000
2011-12-28 10:43:11,393 DEBUG: install progress ureadahead 75.000000
2011-12-28 10:43:12,687 DEBUG: install progress dpkg-exec 75.000000
2011-12-28 10:43:12,789 DEBUG: install progress fglrx 75.000000
2011-12-28 10:43:13,691 DEBUG: install progress fglrx 81.250000
2011-12-28 10:43:50,751 DEBUG: install progress fglrx 87.500000
2011-12-28 10:43:51,913 DEBUG: install progress bamfdaemon 87.500000
2011-12-28 10:43:52,432 DEBUG: install progress gnome-menus 87.500000
2011-12-28 10:43:53,045 DEBUG: install progress fglrx-amdcccle 87.500000
2011-12-28 10:43:53,238 DEBUG: install progress fglrx-amdcccle 93.750000
2011-12-28 10:43:53,396 DEBUG: install progress fglrx-amdcccle 100.000000
2011-12-28 10:43:53,554 DEBUG: install progress initramfs-tools 100.000000
2011-12-28 10:44:07,734 DEBUG: install progress libc-bin 100.000000
2011-12-28 10:44:12,145 DEBUG: (Reading database ... 131686 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 131426 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Loading new fglrx-8.881 DKMS files...
Building for 3.0.0-12-generic and 3.0.0-14-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-12-28 10:44:12,571 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2011-12-28 10:44:44,562 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:44,562 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:44,809 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:44,809 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:45,091 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:45,091 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:44:45,226 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:45,226 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:45,491 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:45,491 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:45,764 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:45,765 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:46,032 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:46,032 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:46,330 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:46,330 DEBUG: fglrx_updates is not the alternative in use
2011-12-28 10:44:46,384 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:46,385 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-28 10:44:46,652 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-28 10:44:46,652 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-29 13:33:13,305 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20>
2011-12-29 13:33:18,688 DEBUG: reading modalias file /lib/modules/3.0.0-14-generic/modules.alias
2011-12-29 13:33:19,006 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-29 13:33:19,016 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-29 13:33:19,089 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-29 13:33:19,127 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-29 13:33:19,199 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-29 13:33:19,203 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-29 13:33:19,203 DEBUG: fglrx.available: falling back to default
2011-12-29 13:33:19,416 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-29 13:33:19,419 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-29 13:33:19,427 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-29 13:33:19,427 DEBUG: fglrx.available: falling back to default
2011-12-29 13:33:19,482 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-29 13:33:19,483 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-29 13:33:19,527 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-29 13:33:19,528 DEBUG: Firmware for DVB cards not available
2011-12-29 13:33:19,528 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-29 13:33:19,531 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-29 13:33:19,531 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-29 13:33:19,592 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-29 13:33:19,592 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-29 13:33:19,595 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-29 13:33:19,596 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-29 13:33:19,596 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-29 13:33:19,596 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-29 13:33:19,613 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-29 13:33:19,637 DEBUG: Software modem not available
2011-12-29 13:33:19,637 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-29 13:33:19,673 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-29 13:33:19,679 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-29 13:33:19,680 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:19,716 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-29 13:33:19,719 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-29 13:33:19,723 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-29 13:33:19,723 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:19,764 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-29 13:33:19,769 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-29 13:33:19,775 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-29 13:33:19,775 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:19,819 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-29 13:33:19,820 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-29 13:33:19,833 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-29 13:33:19,837 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-29 13:33:19,837 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:19,882 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-29 13:33:19,888 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-29 13:33:19,895 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-29 13:33:19,895 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:19,943 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-29 13:33:19,947 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-29 13:33:19,952 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-29 13:33:19,952 DEBUG: nvidia.available: falling back to default
2011-12-29 13:33:20,000 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-29 13:33:20,000 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-29 13:33:20,004 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-29 13:33:20,023 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-29 13:33:20,024 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-29 13:33:20,024 DEBUG: all custom handlers loaded
2011-12-29 13:33:20,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-29 13:33:20,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-29 13:33:20,034 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:20,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-29 13:33:20,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-29 13:33:20,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-29 13:33:20,252 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2011-12-29 13:33:20,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'platform:pcspkr')
2011-12-29 13:33:20,255 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-29 13:33:20,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,255 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-29 13:33:20,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:20,315 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-29 13:33:20,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-29 13:33:20,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-29 13:33:20,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:20,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:20,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-29 13:33:20,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-29 13:33:20,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:20,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-29 13:33:20,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-29 13:33:20,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'platform:regulatory')
2011-12-29 13:33:20,401 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-29 13:33:20,401 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-29 13:33:21,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-29 13:33:21,278 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-29 13:33:21,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-29 13:33:21,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-29 13:33:21,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-29 13:33:21,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-29 13:33:21,289 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-12-29 13:33:21,652 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:21,652 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:21,290 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-29 13:33:21,655 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-29 13:33:21,659 DEBUG: fglrx.available: falling back to default
2011-12-29 13:33:21,721 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:21,722 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:21,688 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-12-29 13:33:21,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-12-29 13:33:21,765 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:21,765 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-29 13:33:21,722 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-29 13:33:21,770 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-29 13:33:21,777 DEBUG: fglrx.available: falling back to default
2011-12-29 13:33:21,844 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:21,844 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-29 13:33:21,803 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-12-29 13:33:21,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-12-29 13:33:21,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-29 13:33:21,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-29 13:33:21,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:21,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-29 13:33:21,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:21,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:21,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-29 13:33:21,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-29 13:33:21,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-29 13:33:21,892 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:21,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-29 13:33:21,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:21,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-29 13:33:21,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-29 13:33:21,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-29 13:33:21,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-29 13:33:21,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:21,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-29 13:33:21,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-29 13:33:21,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-29 13:33:21,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v636Cp0101e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-29 13:33:21,930 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:21,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:21,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:21,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-29 13:33:21,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-29 13:33:21,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:21,975 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-12-29 13:33:21,975 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-29 13:33:21,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-29 13:33:21,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-29 13:33:21,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:21,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:21,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-29 13:33:21,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-29 13:33:21,991 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:21,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:21,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:21,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,993 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-29 13:33:21,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:21,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v636Cp0101d0110dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:21,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:21,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,996 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-29 13:33:21,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:21,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-29 13:33:22,007 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-29 13:33:22,007 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,007 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-12-29 13:33:22,008 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-12-29 13:33:22,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-29 13:33:22,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:22,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-29 13:33:22,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-12-29 13:33:22,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-29 13:33:22,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-12-29 13:33:22,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-29 13:33:22,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-29 13:33:22,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:22,039 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:22,039 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,039 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-29 13:33:22,039 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-29 13:33:22,050 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-29 13:33:22,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-29 13:33:22,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v636Cp0101d0110dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:22,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-29 13:33:22,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-29 13:33:22,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-29 13:33:22,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-29 13:33:22,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-29 13:33:22,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2011-12-29 13:33:22,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-29 13:33:22,076 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-12-29 13:33:22,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,077 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-12-29 13:33:22,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-29 13:33:22,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-29 13:33:22,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-29 13:33:22,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-29 13:33:22,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-12-29 13:33:22,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-12-29 13:33:22,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-12-29 13:33:22,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x188bc20> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-29 13:33:22,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-29 13:33:22,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2011-12-29 13:33:22,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-12-29 13:33:22,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-29 13:33:22,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00')
2011-12-29 13:33:22,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'platform:pcspkr')
2011-12-29 13:33:22,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:22,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-12-29 13:33:22,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-29 13:33:22,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:22,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFFiscFFipFF')
2011-12-29 13:33:22,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-12-29 13:33:22,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-12-29 13:33:22,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'platform:regulatory')
2011-12-29 13:33:22,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2011-12-29 13:33:22,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2011-12-29 13:33:22,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icFEisc01ip00')
2011-12-29 13:33:22,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00006739sv0000174Bsd0000174Bbc03sc00i00')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-29 13:33:22,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2011-12-29 13:33:22,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:22,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp2148d0818dcE0dsc01dp01icE0isc01ip01')
2011-12-29 13:33:22,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-12-29 13:33:22,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,a20,m4,lsfw')
2011-12-29 13:33:22,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-12-29 13:33:22,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-29 13:33:22,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001462sd00007599bc04sc03i00')
2011-12-29 13:33:22,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v636Cp0101e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-12-29 13:33:22,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:22,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.6:bd02/25/2010:svnMICRO-STARINTERNATIONALCO.,LTD:pnMS-7599:pvr1.0:rvnMICRO-STARINTERNATIONALCO.,LTD:rn770-C45(MS-7599):rvr1.0:cvnMICRO-STARINTERNATIONALCO.,LTD:ct3:cvr1.0:')
2011-12-29 13:33:22,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-29 13:33:22,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00')
2011-12-29 13:33:22,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-12-29 13:33:22,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046DpC52Ed1500dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:22,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-12-29 13:33:22,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:22,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v1A40p0201d0100dc09dsc00dp00ic09isc00ip00')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v636Cp0101d0110dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001462sd00007599bc01sc06i01')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0003v046DpC52Ee0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007599bc02sc00i00')
2011-12-29 13:33:22,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00')
2011-12-29 13:33:22,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0501:')
2011-12-29 13:33:22,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-29 13:33:22,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-12-29 13:33:22,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d0000AA88sv0000174Bsd0000AA88bc04sc03i00')
2011-12-29 13:33:22,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-29 13:33:22,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v636Cp0101d0110dc00dsc00dp00ic03isc01ip02')
2011-12-29 13:33:22,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-29 13:33:22,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-12-29 13:33:22,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001462sd00007599bc0Csc03i20')
2011-12-29 13:33:22,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001462sd00007599bc01sc01i8a')
2011-12-29 13:33:22,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-29 13:33:22,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-12-29 13:33:22,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-12-29 13:33:22,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001462sd00007599bc0Csc05i00')
2011-12-29 13:33:22,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a9a9e0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-29 13:33:22,211 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:22,211 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:22,272 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:22,273 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-29 13:33:22,335 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:22,335 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:22,398 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:22,398 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:22,461 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:22,461 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-12-29 13:33:25,693 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:25,693 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:26,923 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:33:26,923 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:33:30,791 DEBUG: Installing package: fglrx-updates
2011-12-29 13:33:34,464 DEBUG: install progress dpkg-exec 0.000000
2011-12-29 13:33:36,003 DEBUG: install progress fglrx-amdcccle 0.000000
2011-12-29 13:33:36,104 DEBUG: install progress fglrx-amdcccle 6.250000
2011-12-29 13:33:36,400 DEBUG: install progress fglrx-amdcccle 12.500000
2011-12-29 13:33:36,908 DEBUG: install progress fglrx-amdcccle 18.750000
2011-12-29 13:33:38,080 DEBUG: install progress fglrx 18.750000
2011-12-29 13:33:38,080 DEBUG: install progress fglrx 25.000000
2011-12-29 13:34:00,101 DEBUG: install progress fglrx 31.250000
2011-12-29 13:34:02,547 DEBUG: install progress fglrx 37.500000
2011-12-29 13:34:02,910 DEBUG: install progress bamfdaemon 37.500000
2011-12-29 13:34:03,460 DEBUG: install progress gnome-menus 37.500000
2011-12-29 13:34:04,030 DEBUG: install progress ureadahead 37.500000
2011-12-29 13:34:04,584 DEBUG: install progress initramfs-tools 37.500000
2011-12-29 13:34:25,300 DEBUG: install progress libc-bin 37.500000
2011-12-29 13:34:26,061 DEBUG: install progress dpkg-exec 37.500000
2011-12-29 13:34:27,225 DEBUG: install progress fglrx-updates 37.500000
2011-12-29 13:34:27,226 DEBUG: install progress fglrx-updates 43.750000
2011-12-29 13:34:34,778 DEBUG: install progress fglrx-updates 50.000000
2011-12-29 13:34:34,995 DEBUG: install progress fglrx-updates 56.250000
2011-12-29 13:34:35,487 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-12-29 13:34:35,487 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-12-29 13:34:36,649 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-12-29 13:34:36,861 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-12-29 13:34:37,093 DEBUG: install progress ureadahead 75.000000
2011-12-29 13:34:37,758 DEBUG: install progress dpkg-exec 75.000000
2011-12-29 13:34:37,837 DEBUG: install progress fglrx-updates 75.000000
2011-12-29 13:34:38,742 DEBUG: install progress fglrx-updates 81.250000
2011-12-29 13:34:40,385 DEBUG: install progress fglrx-updates 87.500000
2011-12-29 13:34:41,650 DEBUG: install progress bamfdaemon 87.500000
2011-12-29 13:34:42,024 DEBUG: install progress gnome-menus 87.500000
2011-12-29 13:34:42,529 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-12-29 13:34:42,745 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-12-29 13:34:42,988 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-12-29 13:34:43,217 DEBUG: install progress initramfs-tools 100.000000
2011-12-29 13:34:57,562 DEBUG: install progress libc-bin 100.000000
2011-12-29 13:35:03,273 DEBUG: (Reading database ... 131670 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 131426 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
Building only for 3.0.0-14-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-12-29 13:35:03,722 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-29 13:35:03,722 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-12-29 13:35:03,722 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-12-29 13:35:03,732 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-12-29 13:35:03,840 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:35:03,840 DEBUG: fglrx_updates is not the alternative in use
2011-12-29 13:35:03,873 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-12-29 13:35:03,874 DEBUG: fglrx_updates is not the alternative in use
[/PHP]

---

