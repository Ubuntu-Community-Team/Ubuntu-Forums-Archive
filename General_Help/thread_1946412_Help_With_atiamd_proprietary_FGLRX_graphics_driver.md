---
title: "Help With ati/amd proprietary FGLRX graphics driver"
date: 2012-03-24
forum: General Help
---

### Post by morlando on 2012-03-24
--------------------
SYSTEM INFORMATION
--------------------
Memory: 3.6Gib
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ × 2
Graphics: VESA: RS780
OS Type: Ubuntu 11.10 64-bit

------
ISSUE
------

When I try and install the "ati/amd proprietary FGLRX graphics driver" from additional software the following error appears -

"sorry the installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"

Below is the log file. Please can anyone help! I am a newbie! :-(

[PHP]
2012-03-24 21:26:31,801 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:31,802 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:31,839 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:31,840 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:31,902 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:31,902 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:26:32,044 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:32,044 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:32,076 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:32,077 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:32,153 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:32,153 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:32,199 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:32,200 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:26:32,272 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:26:32,273 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:27:07,029 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:07,030 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:07,068 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:07,069 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:07,269 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:07,269 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:07,322 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:07,322 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:08,128 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:08,129 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:08,202 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:08,202 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:08,916 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:08,917 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:08,969 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:08,970 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:09,073 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:09,074 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:09,120 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:09,120 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:09,694 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:09,694 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:09,742 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:27:09,742 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:27:59,943 DEBUG: Shutting down
2012-03-24 21:36:19,966 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0>
2012-03-24 21:36:22,682 DEBUG: reading modalias file /lib/modules/3.0.0-16-generic/modules.alias
2012-03-24 21:36:22,806 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-03-24 21:36:22,806 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-03-24 21:36:22,874 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-03-24 21:36:22,914 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-03-24 21:36:22,925 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-03-24 21:36:22,925 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-03-24 21:36:22,957 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-03-24 21:36:22,958 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-03-24 21:36:22,975 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-03-24 21:36:22,985 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-03-24 21:36:22,987 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,123 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-24 21:36:23,137 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-03-24 21:36:23,146 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-03-24 21:36:23,147 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,226 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-24 21:36:23,234 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-03-24 21:36:23,243 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-03-24 21:36:23,244 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,307 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-24 21:36:23,308 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-03-24 21:36:23,319 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-03-24 21:36:23,327 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-03-24 21:36:23,328 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,394 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-24 21:36:23,400 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-03-24 21:36:23,407 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-03-24 21:36:23,408 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,474 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-24 21:36:23,480 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-03-24 21:36:23,487 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-03-24 21:36:23,493 DEBUG: nvidia.available: falling back to default
2012-03-24 21:36:23,560 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-24 21:36:23,560 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-03-24 21:36:23,602 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-03-24 21:36:23,603 DEBUG: Firmware for DVB cards not available
2012-03-24 21:36:23,603 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-03-24 21:36:23,635 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-03-24 21:36:23,651 DEBUG: Software modem not available
2012-03-24 21:36:23,652 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-03-24 21:36:23,660 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-03-24 21:36:23,688 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-03-24 21:36:23,688 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-03-24 21:36:23,688 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-03-24 21:36:23,708 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-03-24 21:36:23,708 DEBUG: fglrx.available: falling back to default
2012-03-24 21:36:23,788 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-24 21:36:23,795 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-24 21:36:23,802 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-03-24 21:36:23,802 DEBUG: fglrx.available: falling back to default
2012-03-24 21:36:23,889 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-03-24 21:36:23,890 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-03-24 21:36:23,896 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-03-24 21:36:23,897 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-03-24 21:36:23,897 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-03-24 21:36:23,897 DEBUG: all custom handlers loaded
2012-03-24 21:36:23,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-24 21:36:23,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0400:')
2012-03-24 21:36:23,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-24 21:36:23,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00009610sv00001458sd0000D000bc03sc00i00')
2012-03-24 21:36:24,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-03-24 21:36:24,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-03-24 21:36:24,493 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,493 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:24,444 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-24 21:36:24,501 DEBUG: fglrx.available: falling back to default
2012-03-24 21:36:24,603 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,603 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:24,547 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-24 21:36:24,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-03-24 21:36:24,644 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,645 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:24,604 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-24 21:36:24,658 DEBUG: fglrx.available: falling back to default
2012-03-24 21:36:24,745 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,745 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:24,708 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-24 21:36:24,746 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-03-24 21:36:24,798 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,799 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:36:24,746 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-24 21:36:24,805 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-24 21:36:24,812 DEBUG: fglrx.available: falling back to default
2012-03-24 21:36:24,896 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:24,897 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:36:24,843 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-24 21:36:24,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-24 21:36:24,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-03-24 21:36:24,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-24 21:36:24,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-24 21:36:24,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01icFFisc42ip01')
2012-03-24 21:36:24,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic02isc02ip01')
2012-03-24 21:36:24,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cdc_acm'}
2012-03-24 21:36:24,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cdc_acm', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-24 21:36:24,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'platform:pcspkr')
2012-03-24 21:36:24,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-03-24 21:36:24,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-03-24 21:36:24,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-03-24 21:36:24,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00009600sv00001022sd00009600bc06sc00i00')
2012-03-24 21:36:24,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic0Aisc00ip00')
2012-03-24 21:36:24,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-24 21:36:24,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-24 21:36:24,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-03-24 21:36:24,963 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-03-24 21:36:24,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:24,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-03-24 21:36:24,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-24 21:36:24,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:24,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-24 21:36:24,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic0Eisc02ip00')
2012-03-24 21:36:25,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic08isc06ip50')
2012-03-24 21:36:25,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-03-24 21:36:25,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2012-03-24 21:36:25,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0700:')
2012-03-24 21:36:25,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2012-03-24 21:36:25,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'input:b0003v046Dp09A4e0006-e0,1,kD4,ramlsfw')
2012-03-24 21:36:25,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-24 21:36:25,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-24 21:36:25,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF2:bd04/03/2008:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA78G-DS3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA78G-DS3H:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-03-24 21:36:25,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-03-24 21:36:25,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-24 21:36:25,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-03-24 21:36:25,064 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-03-24 21:36:25,065 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-03-24 21:36:25,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-03-24 21:36:25,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-03-24 21:36:25,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic01isc02ip00')
2012-03-24 21:36:25,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v192Fp0716d0000dc00dsc00dp00ic03isc01ip02')
2012-03-24 21:36:25,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-03-24 21:36:25,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-03-24 21:36:25,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-24 21:36:25,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-03-24 21:36:25,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-03-24 21:36:25,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k8temp'}
2012-03-24 21:36:25,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-24 21:36:25,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d0000960Fsv00001002sd0000960Fbc04sc03i00')
2012-03-24 21:36:25,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-24 21:36:25,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-24 21:36:25,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-24 21:36:25,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic01isc01ip00')
2012-03-24 21:36:25,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-03-24 21:36:25,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-24 21:36:25,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-24 21:36:25,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-24 21:36:25,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic0Eisc01ip00')
2012-03-24 21:36:25,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-03-24 21:36:25,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-24 21:36:25,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-03-24 21:36:25,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-24 21:36:25,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-24 21:36:25,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-03-24 21:36:25,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-24 21:36:25,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-24 21:36:25,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'input:b0003v192Fp0716e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2012-03-24 21:36:25,104 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-24 21:36:25,104 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-03-24 21:36:25,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-03-24 21:36:25,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17cd8c0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0400:')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00009610sv00001458sd0000D000bc03sc00i00')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01icFFisc42ip01')
2012-03-24 21:36:25,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic02isc02ip01')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'platform:pcspkr')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00009600sv00001022sd00009600bc06sc00i00')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic0Aisc00ip00')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic0Eisc02ip00')
2012-03-24 21:36:25,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v04E8p685Ed0400dcEFdsc02dp01ic08isc06ip50')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0700:')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd00004383bc06sc01i00')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'input:b0003v046Dp09A4e0006-e0,1,kD4,ramlsfw')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF2:bd04/03/2008:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA78G-DS3H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA78G-DS3H:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic01isc02ip00')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v192Fp0716d0000dc00dsc00dp00ic03isc01ip02')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-24 21:36:25,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-03-24 21:36:25,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0800:')
2012-03-24 21:36:25,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d0000960Fsv00001002sd0000960Fbc04sc03i00')
2012-03-24 21:36:25,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic01isc01ip00')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'usb:v046Dp09A4d0006dcEFdsc02dp01ic0Eisc01ip00')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-03-24 21:36:25,117 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-03-24 21:36:25,118 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'input:b0003v192Fp0716e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2012-03-24 21:36:25,118 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-03-24 21:36:25,118 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x19ed248> about HardwareID('modalias', 'acpi:PNP0501:')
2012-03-24 21:36:25,254 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,254 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:25,314 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,314 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:25,396 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,397 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:36:25,557 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,558 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:36:25,737 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,738 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:25,797 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,797 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:25,923 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,924 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:25,979 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:25,979 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:36:26,068 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:26,069 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:36:26,248 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:36:26,249 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:38:36,692 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:36,692 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:36,785 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:36,785 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:38:36,935 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:36,935 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:37,007 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,007 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:37,072 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,072 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:37,115 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,116 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:38:37,264 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,264 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:38:37,403 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,403 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:37,514 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,515 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:38:37,588 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:38:37,588 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:42:12,322 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:42:12,322 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:42:19,222 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-03-24 21:42:19,342 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-03-24 21:42:19,445 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:42:19,446 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:42:19,488 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:42:19,488 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:34,898 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:34,898 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:34,959 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:34,960 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:35,040 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,041 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-24 21:43:35,218 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,218 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:35,266 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,266 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:35,350 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,350 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:35,399 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,399 DEBUG: fglrx_updates is not the alternative in use
2012-03-24 21:43:35,487 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-24 21:43:35,487 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
[/PHP]

---

### Post by morlando on 2012-03-24
I forgot to mention that my graphics card is a radeon based card built into my motherboard.

---

