---
title: "ATI graphics driver not installing"
date: 2011-11-05
forum: General Help
---

### Post by xly15 on 2011-11-05
I am using Ubuntu 11.10 and I can not get the proprietary ATI drivers to install from the restricted drivers panel. I ever time I try I get this error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

If you want the text of that file I am willing to post it.

---

### Post by go2dell on 2011-11-05
Posting the log file is likely the only way that anybody will be able to figure out how to help.  Please post the jockey log file, and also please tell a little bit about your system (make and model of video card, computer make and model, etc.).

---

### Post by techvish81 on 2011-11-05
actually that driver if installed,  will cause weird display problems . I think u dont need that driver,  I've the same display card and the default driver,  and I dont see any degradation in display,  there are some people who managed to install that driver but results were different and unexpected.

---

### Post by xly15 on 2011-11-05
My system is:
Asus M5A97 AM3+ motherboard
AMD Phenom II 945 3.o GHz cpu
G.Skill 8Gb ddr3 1600 ram
Xfx ATi radeon 4870

The reason I want to install the proprietary drivers is because my graphics card is hitting pretty high temps in my opinion and I want to be able to control the fan speed. 

here is my Jockey.log
```
2011-11-05 08:02:20,928 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908>
2011-11-05 08:02:22,273 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-11-05 08:02:22,333 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-05 08:02:22,334 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-05 08:02:22,358 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-05 08:02:22,390 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-05 08:02:22,435 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-05 08:02:22,436 DEBUG: Firmware for DVB cards not available
2011-11-05 08:02:22,436 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-05 08:02:22,448 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 08:02:22,456 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-05 08:02:22,457 DEBUG: fglrx.available: falling back to default
2011-11-05 08:02:22,592 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 08:02:22,598 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 08:02:22,606 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-05 08:02:22,607 DEBUG: fglrx.available: falling back to default
2011-11-05 08:02:22,692 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-05 08:02:22,692 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-05 08:02:22,700 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-05 08:02:22,709 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-05 08:02:22,710 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:22,776 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 08:02:22,784 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-05 08:02:22,793 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-05 08:02:22,793 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:22,866 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 08:02:22,873 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-05 08:02:22,882 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-05 08:02:22,883 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:22,954 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 08:02:22,955 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-05 08:02:22,962 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-05 08:02:22,971 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-05 08:02:22,971 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:23,044 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 08:02:23,051 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-05 08:02:23,060 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-05 08:02:23,060 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:23,132 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-05 08:02:23,139 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-05 08:02:23,148 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-05 08:02:23,148 DEBUG: nvidia.available: falling back to default
2011-11-05 08:02:23,222 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-05 08:02:23,222 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-05 08:02:23,230 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-05 08:02:23,230 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-05 08:02:23,267 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-05 08:02:23,267 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-05 08:02:23,275 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-11-05 08:02:23,313 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-05 08:02:23,314 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-05 08:02:23,314 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-05 08:02:23,322 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-05 08:02:23,323 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-05 08:02:23,323 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-05 08:02:23,323 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-05 08:02:23,363 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-05 08:02:23,379 DEBUG: Software modem not available
2011-11-05 08:02:23,379 DEBUG: all custom handlers loaded
2011-11-05 08:02:23,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 08:02:23,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 08:02:23,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:23,459 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 08:02:23,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 08:02:23,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001682sd0000AA30bc04sc03i00')
2011-11-05 08:02:23,652 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 08:02:23,652 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,652 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 08:02:23,652 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-05 08:02:23,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-05 08:02:23,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,D4,E3,EE,F0,F4,212,215,216,217,218,219,21A,ram4,lsfw')
2011-11-05 08:02:23,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:23,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 08:02:23,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 08:02:23,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 08:02:23,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 08:02:23,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-05 08:02:23,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-05 08:02:23,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-05 08:02:23,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2011-11-05 08:02:23,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:23,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00005A14sv00001002sd00005A14bc06sc00i00')
2011-11-05 08:02:23,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-05 08:02:23,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-05 08:02:23,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 08:02:23,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 08:02:23,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00009440sv00001682sd00002445bc03sc00i00')
2011-11-05 08:02:23,674 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-05 08:02:23,730 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:23,730 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:23,674 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 08:02:23,737 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-05 08:02:23,746 DEBUG: fglrx.available: falling back to default
2011-11-05 08:02:23,847 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:23,847 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:23,790 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-05 08:02:23,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-05 08:02:23,899 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:23,899 DEBUG: fglrx is not the alternative in use
2011-11-05 08:02:23,848 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 08:02:23,905 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-05 08:02:23,912 DEBUG: fglrx.available: falling back to default
2011-11-05 08:02:24,010 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,010 DEBUG: fglrx is not the alternative in use
2011-11-05 08:02:23,953 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-05 08:02:24,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-05 08:02:24,011 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00004391sv00001043sd000084DDbc01sc06i01')
2011-11-05 08:02:24,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-05 08:02:24,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-05 08:02:24,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 08:02:24,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2011-11-05 08:02:24,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-05 08:02:24,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic01isc01ip00')
2011-11-05 08:02:24,059 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2011-11-05 08:02:24,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2011-11-05 08:02:24,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 08:02:24,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-11-05 08:02:24,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0003v046Dp0A0Ce0100-e0,1,4,k72,73,ram4,lsfw')
2011-11-05 08:02:24,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:24,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 08:02:24,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-05 08:02:24,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 08:02:24,063 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:24,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0705:bd08/22/2011:svnTobefilledbyO.E.M.:pnTobefilledbyO.E.M.:pvrTobefilledbyO.E.M.:rvnASUSTeKComputerINC.:rnM5A97:rvrRev1.xx:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2011-11-05 08:02:24,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-05 08:02:24,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 08:02:24,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-11-05 08:02:24,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:24,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic03isc00ip00')
2011-11-05 08:02:24,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 08:02:24,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-05 08:02:24,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 08:02:24,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2011-11-05 08:02:24,078 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-11-05 08:02:24,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-05 08:02:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-05 08:02:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 08:02:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic01isc02ip00')
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 08:02:24,080 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:24,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'usb:v051Dp0002d0106dc00dsc00dp00ic03isc00ip00')
2011-11-05 08:02:24,080 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-11-05 08:02:24,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-05 08:02:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-05 08:02:24,081 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-05 08:02:24,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008444bc04sc03i00')
2011-11-05 08:02:24,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 08:02:24,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-05 08:02:24,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 08:02:24,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-05 08:02:24,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-05 08:02:24,086 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-05 08:02:24,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,086 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-05 08:02:24,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b08908> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d0000AA30sv00001682sd0000AA30bc04sc03i00')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,D4,E3,EE,F0,F4,212,215,216,217,218,219,21A,ram4,lsfw')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-05 08:02:24,086 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'platform:pcspkr')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00005A14sv00001002sd00005A14bc06sc00i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00009440sv00001682sd00002445bc03sc00i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00004391sv00001043sd000084DDbc01sc06i01')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic01isc01ip00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0003v046Dp0A0Ce0100-e0,1,4,k72,73,ram4,lsfw')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0705:bd08/22/2011:svnTobefilledbyO.E.M.:pnTobefilledbyO.E.M.:pvrTobefilledbyO.E.M.:rvnASUSTeKComputerINC.:rnM5A97:rvrRev1.xx:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,087 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic03isc00ip00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0501:')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v046Dp0A0Cd1013dc00dsc00dp00ic01isc02ip00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'usb:v051Dp0002d0106dc00dsc00dp00ic03isc00ip00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008444bc04sc03i00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-05 08:02:24,088 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d10e60> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-05 08:02:24,186 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,187 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:24,289 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,289 DEBUG: fglrx is not the alternative in use
2011-11-05 08:02:24,352 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,353 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:24,452 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,453 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:24,536 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:24,537 DEBUG: fglrx is not the alternative in use
2011-11-05 08:02:27,573 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-05 08:02:27,573 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:02:32,686 DEBUG: Installing package: fglrx-updates
2011-11-05 08:02:33,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 08:02:33,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 08:02:33,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 08:02:33,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-11-05 08:02:33,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.006175
2011-11-05 08:02:33,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.127375
2011-11-05 08:02:34,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.570621
2011-11-05 08:02:34,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.138531
2011-11-05 08:02:35,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.886509
2011-11-05 08:02:35,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.565230
2011-11-05 08:02:36,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.309745
2011-11-05 08:02:36,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.998854
2011-11-05 08:02:37,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.847255
2011-11-05 08:02:37,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.803005
2011-11-05 08:02:38,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.873029
2011-11-05 08:02:38,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.510196
2011-11-05 08:02:39,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.275488
2011-11-05 08:02:39,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.912655
2011-11-05 08:02:40,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.688336
2011-11-05 08:02:40,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.311651
2011-11-05 08:02:41,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.080406
2011-11-05 08:02:41,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.755664
2011-11-05 08:02:42,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.503642
2011-11-05 08:02:42,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.210066
2011-11-05 08:02:43,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.902638
2011-11-05 08:02:43,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.595211
2011-11-05 08:02:44,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.308560
2011-11-05 08:02:44,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.042687
2011-11-05 08:02:45,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.711019
2011-11-05 08:02:45,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.313557
2011-11-05 08:02:46,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.047684
2011-11-05 08:02:46,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.761033
2011-11-05 08:02:47,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.515937
2011-11-05 08:02:47,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.194658
2011-11-05 08:02:48,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.953024
2011-11-05 08:02:48,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.676763
2011-11-05 08:02:49,372 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.317392
2011-11-05 08:02:49,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.023816
2011-11-05 08:02:50,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.719851
2011-11-05 08:02:50,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.502458
2011-11-05 08:02:51,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.156938
2011-11-05 08:02:51,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.884139
2011-11-05 08:02:52,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.594026
2011-11-05 08:02:52,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.314301
2011-11-05 08:02:53,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.065742
2011-11-05 08:02:53,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.734074
2011-11-05 08:02:54,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.468201
2011-11-05 08:02:54,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.133071
2011-11-05 08:02:55,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.870660
2011-11-05 08:02:55,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.538992
2011-11-05 08:02:56,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.293896
2011-11-05 08:02:56,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.052263
2011-11-05 08:02:57,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.831407
2011-11-05 08:02:57,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.496276
2011-11-05 08:02:58,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.251180
2011-11-05 08:02:58,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.964529
2011-11-05 08:02:59,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.653639
2011-11-05 08:02:59,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.415468
2011-11-05 08:03:00,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.059561
2011-11-05 08:03:00,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.838704
2011-11-05 08:03:01,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.482797
2011-11-05 08:03:01,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.237701
2011-11-05 08:03:02,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.937199
2011-11-05 08:03:02,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.737120
2011-11-05 08:03:03,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.412378
2011-11-05 08:03:03,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.201910
2011-11-05 08:03:04,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.894482
2011-11-05 08:03:04,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.652849
2011-11-05 08:03:05,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.380050
2011-11-05 08:03:05,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.141880
2011-11-05 08:03:06,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.879469
2011-11-05 08:03:06,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.599744
2011-11-05 08:03:07,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.323482
2011-11-05 08:03:07,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.988352
2011-11-05 08:03:08,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.746718
2011-11-05 08:03:08,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.473919
2011-11-05 08:03:09,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.190732
2011-11-05 08:03:09,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.921396
2011-11-05 08:03:10,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.558562
2011-11-05 08:03:10,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.330780
2011-11-05 08:03:11,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.089147
2011-11-05 08:03:11,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.712462
2011-11-05 08:03:12,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.491606
2011-11-05 08:03:12,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.135698
2011-11-05 08:03:13,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.894065
2011-11-05 08:03:13,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.558934
2011-11-05 08:03:14,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.317301
2011-11-05 08:03:14,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.075668
2011-11-05 08:03:15,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.754388
2011-11-05 08:03:15,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.498904
2011-11-05 08:03:16,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.219179
2011-11-05 08:03:16,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.880585
2011-11-05 08:03:17,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.659729
2011-11-05 08:03:17,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.328062
2011-11-05 08:03:18,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.062188
2011-11-05 08:03:18,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.772075
2011-11-05 08:03:19,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.481961
2011-11-05 08:03:19,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.264568
2011-11-05 08:03:20,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.022935
2011-11-05 08:03:20,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.691267
2011-11-05 08:03:21,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.425394
2011-11-05 08:03:21,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.104115
2011-11-05 08:03:22,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.827853
2011-11-05 08:03:22,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.451168
2011-11-05 08:03:23,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.230312
2011-11-05 08:03:23,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.960975
2011-11-05 08:03:24,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.670862
2011-11-05 08:03:24,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.432692
2011-11-05 08:03:25,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.059470
2011-11-05 08:03:25,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.835151
2011-11-05 08:03:26,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.593517
2011-11-05 08:03:26,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.244535
2011-11-05 08:03:27,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.995976
2011-11-05 08:03:27,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.640068
2011-11-05 08:03:28,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.398435
2011-11-05 08:03:28,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.066767
2011-11-05 08:03:29,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.800894
2011-11-05 08:03:29,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.441523
2011-11-05 08:03:30,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.224130
2011-11-05 08:03:30,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.982497
2011-11-05 08:03:31,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.605812
2011-11-05 08:03:31,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.384956
2011-11-05 08:03:32,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.029048
2011-11-05 08:03:32,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.804729
2011-11-05 08:03:33,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.473061
2011-11-05 08:03:33,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.210651
2011-11-05 08:03:34,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.543002
2011-11-05 08:03:34,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.552733
2011-11-05 08:03:34,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.238379
2011-11-05 08:03:35,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.924026
2011-11-05 08:03:35,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.682393
2011-11-05 08:03:36,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.347262
2011-11-05 08:03:36,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.105629
2011-11-05 08:03:37,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.753184
2011-11-05 08:03:37,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.487311
2011-11-05 08:03:38,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.266454
2011-11-05 08:03:38,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.934787
2011-11-05 08:03:39,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.668913
2011-11-05 08:03:39,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.448057
2011-11-05 08:03:40,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.088687
2011-11-05 08:03:40,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.871293
2011-11-05 08:03:41,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.567328
2011-11-05 08:03:41,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.273752
2011-11-05 08:03:42,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.032119
2011-11-05 08:03:42,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.693525
2011-11-05 08:03:43,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.455355
2011-11-05 08:03:43,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2011-11-05 08:03:43,778 DEBUG: install progress dpkg-exec 0.000000
2011-11-05 08:03:43,973 DEBUG: install progress fglrx-updates 0.000000
2011-11-05 08:03:43,973 DEBUG: install progress fglrx-updates 10.000000
2011-11-05 08:03:45,408 DEBUG: install progress fglrx-updates 20.000000
2011-11-05 08:03:45,411 DEBUG: install progress fglrx-updates 30.000000
2011-11-05 08:03:45,455 DEBUG: install progress fglrx-amdcccle-updates 30.000000
2011-11-05 08:03:45,556 DEBUG: install progress fglrx-amdcccle-updates 40.000000
2011-11-05 08:03:45,631 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2011-11-05 08:03:45,633 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2011-11-05 08:03:45,642 DEBUG: install progress ureadahead 60.000000
2011-11-05 08:03:45,699 DEBUG: install progress dpkg-exec 60.000000
2011-11-05 08:03:45,743 DEBUG: install progress fglrx-updates 60.000000
2011-11-05 08:03:45,753 DEBUG: install progress fglrx-updates 70.000000
2011-11-05 08:04:02,023 DEBUG: install progress fglrx-updates 80.000000
2011-11-05 08:04:02,040 DEBUG: install progress bamfdaemon 80.000000
2011-11-05 08:04:02,063 DEBUG: install progress gnome-menus 80.000000
2011-11-05 08:04:02,070 DEBUG: install progress fglrx-amdcccle-updates 80.000000
2011-11-05 08:04:02,072 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2011-11-05 08:04:02,074 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-11-05 08:04:02,077 DEBUG: install progress initramfs-tools 100.000000
2011-11-05 08:04:12,241 DEBUG: install progress libc-bin 100.000000
2011-11-05 08:04:12,844 DEBUG: Selecting previously deselected package fglrx-updates.
(Reading database ... 154666 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.881-0ubuntu6.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
First Installation: checking all kernels...
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
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-11-05 08:04:13,035 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-05 08:04:13,119 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-05 08:04:13,239 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:13,239 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:13,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:13,307 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:23,540 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,540 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:23,604 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,605 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:23,704 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,705 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-05 08:04:23,798 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,798 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:23,844 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,844 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:23,966 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:23,967 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:24,034 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:24,035 DEBUG: fglrx_updates is not the alternative in use
2011-11-05 08:04:24,108 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-05 08:04:24,108 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-05 08:04:25,160 DEBUG: Shutting down
```

---

### Post by fredric_ on 2011-11-05
I have successfully installed ATI driver using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Maybe you can try that.
Don't forget to remove all previous ATI driver installation before installing the new driver, and generate a new /etc/X11/xorg.conf file. I used the generic config.

---

### Post by Mark Phelps on 2011-11-05
> **xly15 said:**
> My system is:
Asus M5A97 AM3+ motherboard
AMD Phenom II 945 3.o GHz cpu
G.Skill 8Gb ddr3 1600 ram
Xfx ATi radeon 4870

The reason I want to install the proprietary drivers is because my graphics card is hitting pretty high temps in my opinion and I want to be able to control the fan speed. 
If by that, you mean you want to slow the fan down, then don't do that.  That's a surefire way to burn out your graphics card.

---

### Post by xly15 on 2011-11-05
Nope I actually need to be able to ramp up the fan speed.

---

