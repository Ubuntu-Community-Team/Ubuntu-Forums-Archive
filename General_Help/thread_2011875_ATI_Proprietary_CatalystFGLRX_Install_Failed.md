---
title: "ATI Proprietary Catalyst/FGLRX Install Failed"
date: 2012-06-28
forum: General Help
---

### Post by weirddan455 on 2012-06-28
This is a fresh install of Xubuntu 12.04.  I would think this part would be the same for all varients though so if anything worked for you please chime in.  All I've done is install, then do the updates, reboot, then try to install ATI drivers.  Here's my jockey.log file it told me to check.  It's pretty long and I'm not quite sure what I'm looking at

```
2012-06-27 20:24:12,488 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0>
2012-06-27 20:24:13,677 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-06-27 20:24:13,763 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-27 20:24:13,770 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-27 20:24:13,796 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-27 20:24:13,818 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-27 20:24:13,818 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-27 20:24:13,825 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-27 20:24:13,825 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-27 20:24:13,828 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-27 20:24:13,829 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-27 20:24:13,919 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-27 20:24:13,919 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-27 20:24:13,953 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-27 20:24:13,954 DEBUG: Firmware for DVB cards not available
2012-06-27 20:24:13,954 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-27 20:24:13,956 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-27 20:24:13,964 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-27 20:24:13,964 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-27 20:24:13,964 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-27 20:24:13,966 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-27 20:24:13,966 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-27 20:24:13,966 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-27 20:24:13,966 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-27 20:24:13,974 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-27 20:24:13,985 DEBUG: Software modem not available
2012-06-27 20:24:13,985 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-27 20:24:14,025 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 20:24:14,027 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-27 20:24:14,027 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,041 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-27 20:24:14,042 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 20:24:14,044 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-27 20:24:14,044 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,058 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-27 20:24:14,058 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-27 20:24:14,062 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-27 20:24:14,064 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-27 20:24:14,064 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,071 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 20:24:14,071 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-27 20:24:14,073 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-27 20:24:14,075 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-27 20:24:14,075 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,089 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-27 20:24:14,090 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-27 20:24:14,092 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-27 20:24:14,093 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,108 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-27 20:24:14,109 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-27 20:24:14,111 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-27 20:24:14,111 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,118 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 20:24:14,118 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-27 20:24:14,120 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-27 20:24:14,122 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-27 20:24:14,122 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,129 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 20:24:14,129 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-27 20:24:14,131 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-27 20:24:14,133 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-27 20:24:14,133 DEBUG: nvidia.available: falling back to default
2012-06-27 20:24:14,140 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 20:24:14,140 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-27 20:24:14,140 DEBUG: all custom handlers loaded
2012-06-27 20:24:14,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-27 20:24:14,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-06-27 20:24:14,143 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-06-27 20:24:14,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-27 20:24:14,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001002sd0000AA50bc04sc03i00')
2012-06-27 20:24:14,379 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 20:24:14,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'platform:pcspkr')
2012-06-27 20:24:14,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-27 20:24:14,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-27 20:24:14,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-27 20:24:14,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icE0isc01ip01')
2012-06-27 20:24:14,388 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 20:24:14,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0011v0001p0001eABAA-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-27 20:24:14,388 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,388 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-06-27 20:24:14,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-06-27 20:24:14,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-27 20:24:14,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'platform:parport_pc')
2012-06-27 20:24:14,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2012-06-27 20:24:14,390 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,390 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-27 20:24:14,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-06-27 20:24:14,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2012-06-27 20:24:14,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002542bc03sc00i00')
2012-06-27 20:24:14,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-27 20:24:14,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-27 20:24:14,453 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,454 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:14,393 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 20:24:14,455 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 20:24:14,457 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,471 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,471 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:14,465 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 20:24:14,471 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-27 20:24:14,477 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,477 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:14,471 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 20:24:14,479 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 20:24:14,481 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,495 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,495 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:14,488 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 20:24:14,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007681bc0Csc03i30')
2012-06-27 20:24:14,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-27 20:24:14,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-27 20:24:14,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2012-06-27 20:24:14,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007681bc04sc03i00')
2012-06-27 20:24:14,640 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 20:24:14,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,640 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 20:24:14,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-27 20:24:14,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007681bc0Csc05i00')
2012-06-27 20:24:14,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-06-27 20:24:14,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007681bc0Csc03i20')
2012-06-27 20:24:14,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic03isc00ip00')
2012-06-27 20:24:14,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 20:24:14,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-06-27 20:24:14,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-06-27 20:24:14,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-27 20:24:14,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-06-27 20:24:14,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-27 20:24:14,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007681bc02sc00i00')
2012-06-27 20:24:14,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-27 20:24:14,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0003v10F5p0242e0111-e0,1,3,4,k72,73,A3,A4,A5,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2012-06-27 20:24:14,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 20:24:14,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 20:24:14,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 20:24:14,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV23.7:bd02/21/2012:svnMSI:pnMS-7681:pvr4.0:rvnMSI:rnZ68A-GD65(G3)(MS-7681):rvr4.0:cvnMSI:ct3:cvr4.0:')
2012-06-27 20:24:14,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-27 20:24:14,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2012-06-27 20:24:14,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 20:24:14,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-27 20:24:14,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001462sd00007681bc06sc01i00')
2012-06-27 20:24:14,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-06-27 20:24:14,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFEisc01ip00')
2012-06-27 20:24:14,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 20:24:14,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-06-27 20:24:14,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 20:24:14,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc00ip00')
2012-06-27 20:24:14,674 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 20:24:14,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-06-27 20:24:14,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc01ip00')
2012-06-27 20:24:14,674 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-06-27 20:24:14,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007681bc07sc80i00')
2012-06-27 20:24:14,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-06-27 20:24:14,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-27 20:24:14,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-27 20:24:14,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002042bc03sc80i00')
2012-06-27 20:24:14,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-27 20:24:14,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-27 20:24:14,684 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,684 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:14,678 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 20:24:14,686 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 20:24:14,687 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,700 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,700 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:14,695 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 20:24:14,700 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-27 20:24:14,706 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,706 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:14,701 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 20:24:14,708 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 20:24:14,709 DEBUG: fglrx.available: falling back to default
2012-06-27 20:24:14,722 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,722 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:14,716 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 20:24:14,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2012-06-27 20:24:14,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 20:24:14,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-06-27 20:24:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-27 20:24:14,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc01ip02')
2012-06-27 20:24:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 20:24:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-27 20:24:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-27 20:24:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-27 20:24:14,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc02ip00')
2012-06-27 20:24:14,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-27 20:24:14,724 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,724 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 20:24:14,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001462sd00007681bc01sc06i01')
2012-06-27 20:24:14,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007681bc0Csc03i20')
2012-06-27 20:24:14,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007681bc06sc04i00')
2012-06-27 20:24:14,728 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-27 20:24:14,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFFiscFFipFF')
2012-06-27 20:24:14,728 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 20:24:14,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-27 20:24:14,728 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 20:24:14,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 20:24:14,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007681bc06sc04i01')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x298a0e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001002sd0000AA50bc04sc03i00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'platform:pcspkr')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icE0isc01ip01')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0011v0001p0001eABAA-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'platform:parport_pc')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002542bc03sc00i00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007681bc0Csc03i30')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007681bc04sc03i00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007681bc0Csc05i00')
2012-06-27 20:24:14,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007681bc0Csc03i20')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic03isc00ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007681bc02sc00i00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0003v10F5p0242e0111-e0,1,3,4,k72,73,A3,A4,A5,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV23.7:bd02/21/2012:svnMSI:pnMS-7681:pvr4.0:rvnMSI:rnZ68A-GD65(G3)(MS-7681):rvr4.0:cvnMSI:ct3:cvr4.0:')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001462sd00007681bc06sc01i00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFEisc01ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc00ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc01ip00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007681bc07sc80i00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002042bc03sc80i00')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc01ip02')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-27 20:24:14,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc02ip00')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001462sd00007681bc01sc06i01')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007681bc0Csc03i20')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007681bc06sc04i00')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFFiscFFipFF')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007681bc06sc04i01')
2012-06-27 20:24:14,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cfa5f0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-27 20:24:14,745 DEBUG: handler xorg:fglrx_updates previously unseen
2012-06-27 20:24:14,745 DEBUG: handler xorg:fglrx previously unseen
2012-06-27 20:24:14,746 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-27 20:24:14,751 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,751 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:14,756 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,757 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:14,768 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:14,768 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:26,718 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:26,718 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:26,753 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:26,753 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:26,766 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:26,766 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:26,782 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:26,782 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:26,793 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:26,793 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:28,731 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:28,731 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:29,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:29,307 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:30,063 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:30,063 DEBUG: fglrx is not the alternative in use
2012-06-27 20:24:30,861 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 20:24:30,861 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 20:24:32,192 DEBUG: Shutting down
2012-06-27 22:42:36,035 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0>
2012-06-27 22:42:37,239 DEBUG: reading modalias file /lib/modules/3.2.0-25-generic/modules.alias
2012-06-27 22:42:37,322 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-27 22:42:37,329 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-27 22:42:37,372 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-06-27 22:42:37,416 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-06-27 22:42:37,416 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-06-27 22:42:37,430 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-06-27 22:42:37,430 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-06-27 22:42:37,436 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-06-27 22:42:37,440 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-06-27 22:42:37,567 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-06-27 22:42:37,567 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-27 22:42:37,623 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-27 22:42:37,623 DEBUG: Firmware for DVB cards not available
2012-06-27 22:42:37,623 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-27 22:42:37,628 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-27 22:42:37,643 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-27 22:42:37,644 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-27 22:42:37,644 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-27 22:42:37,648 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-27 22:42:37,649 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-27 22:42:37,649 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-27 22:42:37,649 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-27 22:42:37,665 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-27 22:42:37,681 DEBUG: Software modem not available
2012-06-27 22:42:37,681 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-27 22:42:37,727 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 22:42:37,731 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-06-27 22:42:37,731 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:37,760 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-27 22:42:37,764 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 22:42:37,767 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-27 22:42:37,768 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:37,796 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-27 22:42:37,797 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-27 22:42:37,804 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-27 22:42:37,808 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-27 22:42:37,809 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,823 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 22:42:37,824 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-27 22:42:37,827 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-06-27 22:42:37,831 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-27 22:42:37,832 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,860 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-27 22:42:37,864 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-06-27 22:42:37,868 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-06-27 22:42:37,868 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,900 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-06-27 22:42:37,903 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-06-27 22:42:37,907 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-06-27 22:42:37,908 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,922 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 22:42:37,922 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-27 22:42:37,926 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-27 22:42:37,930 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-27 22:42:37,930 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,944 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 22:42:37,945 DEBUG: NVIDIA accelerated graphics driver not available
2012-06-27 22:42:37,948 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-06-27 22:42:37,952 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-06-27 22:42:37,953 DEBUG: nvidia.available: falling back to default
2012-06-27 22:42:37,967 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-06-27 22:42:37,967 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-06-27 22:42:37,967 DEBUG: all custom handlers loaded
2012-06-27 22:42:37,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-27 22:42:37,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-06-27 22:42:37,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-06-27 22:42:38,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-27 22:42:38,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001002sd0000AA50bc04sc03i00')
2012-06-27 22:42:38,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 22:42:38,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'platform:pcspkr')
2012-06-27 22:42:38,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-06-27 22:42:38,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-06-27 22:42:38,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-27 22:42:38,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icE0isc01ip01')
2012-06-27 22:42:38,221 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 22:42:38,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0011v0001p0001eABAA-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-27 22:42:38,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-06-27 22:42:38,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-06-27 22:42:38,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-27 22:42:38,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'platform:parport_pc')
2012-06-27 22:42:38,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2012-06-27 22:42:38,224 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,224 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-27 22:42:38,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-06-27 22:42:38,224 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2012-06-27 22:42:38,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002542bc03sc00i00')
2012-06-27 22:42:38,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-27 22:42:38,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-27 22:42:38,257 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,257 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,226 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 22:42:38,260 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 22:42:38,264 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:38,291 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,291 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,279 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 22:42:38,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-27 22:42:38,303 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,303 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:38,291 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 22:42:38,306 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 22:42:38,310 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:38,336 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,337 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:38,325 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 22:42:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007681bc0Csc03i30')
2012-06-27 22:42:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-27 22:42:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-27 22:42:38,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2012-06-27 22:42:38,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007681bc04sc03i00')
2012-06-27 22:42:38,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 22:42:38,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-06-27 22:42:38,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-27 22:42:38,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007681bc0Csc05i00')
2012-06-27 22:42:38,498 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-06-27 22:42:38,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007681bc0Csc03i20')
2012-06-27 22:42:38,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic03isc00ip00')
2012-06-27 22:42:38,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 22:42:38,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-06-27 22:42:38,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-06-27 22:42:38,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-27 22:42:38,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-06-27 22:42:38,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-27 22:42:38,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007681bc02sc00i00')
2012-06-27 22:42:38,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-06-27 22:42:38,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0003v10F5p0242e0111-e0,1,3,4,k72,73,A3,A4,A5,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2012-06-27 22:42:38,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 22:42:38,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 22:42:38,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 22:42:38,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV23.7:bd02/21/2012:svnMSI:pnMS-7681:pvr4.0:rvnMSI:rnZ68A-GD65(G3)(MS-7681):rvr4.0:cvnMSI:ct3:cvr4.0:')
2012-06-27 22:42:38,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-27 22:42:38,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2012-06-27 22:42:38,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 22:42:38,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-27 22:42:38,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001462sd00007681bc06sc01i00')
2012-06-27 22:42:38,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-06-27 22:42:38,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFEisc01ip00')
2012-06-27 22:42:38,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 22:42:38,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-06-27 22:42:38,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-06-27 22:42:38,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc00ip00')
2012-06-27 22:42:38,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 22:42:38,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-06-27 22:42:38,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc01ip00')
2012-06-27 22:42:38,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-06-27 22:42:38,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007681bc07sc80i00')
2012-06-27 22:42:38,532 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-06-27 22:42:38,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-27 22:42:38,533 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,533 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-27 22:42:38,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002042bc03sc80i00')
2012-06-27 22:42:38,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-06-27 22:42:38,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-06-27 22:42:38,544 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,544 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,535 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 22:42:38,547 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-06-27 22:42:38,550 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:38,577 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,577 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,565 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-06-27 22:42:38,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-06-27 22:42:38,589 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,589 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:38,578 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 22:42:38,592 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-27 22:42:38,596 DEBUG: fglrx.available: falling back to default
2012-06-27 22:42:38,622 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,623 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:38,611 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-06-27 22:42:38,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2012-06-27 22:42:38,623 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 22:42:38,624 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,624 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-06-27 22:42:38,624 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-27 22:42:38,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc01ip02')
2012-06-27 22:42:38,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-06-27 22:42:38,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-06-27 22:42:38,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-27 22:42:38,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-27 22:42:38,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc02ip00')
2012-06-27 22:42:38,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-27 22:42:38,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-06-27 22:42:38,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001462sd00007681bc01sc06i01')
2012-06-27 22:42:38,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007681bc0Csc03i20')
2012-06-27 22:42:38,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007681bc06sc04i00')
2012-06-27 22:42:38,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-06-27 22:42:38,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFFiscFFipFF')
2012-06-27 22:42:38,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-06-27 22:42:38,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-27 22:42:38,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-06-27 22:42:38,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-27 22:42:38,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007681bc06sc04i01')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16e10e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001002sd0000AA50bc04sc03i00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'platform:pcspkr')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icE0isc01ip01')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0011v0001p0001eABAA-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'platform:parport_pc')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002542bc03sc00i00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007681bc0Csc03i30')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007681bc04sc03i00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007681bc0Csc05i00')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007681bc0Csc03i20')
2012-06-27 22:42:38,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic03isc00ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007681bc02sc00i00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0003v10F5p0242e0111-e0,1,3,4,k72,73,A3,A4,A5,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV23.7:bd02/21/2012:svnMSI:pnMS-7681:pvr4.0:rvnMSI:rnZ68A-GD65(G3)(MS-7681):rvr4.0:cvnMSI:ct3:cvr4.0:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C44sv00001462sd00007681bc06sc01i00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFEisc01ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0003v046DpC068e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc00ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc01ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007681bc07sc80i00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00001002d0000689Csv00001002sd00002042bc03sc80i00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v046DpC068d5802dc00dsc00dp00ic03isc01ip02')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v10F5p0242d0100dc00dsc00dp00ic01isc02ip00')
2012-06-27 22:42:38,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C02sv00001462sd00007681bc01sc06i01')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007681bc0Csc03i20')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007681bc06sc04i00')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'usb:v0461p4D75d0667dcE0dsc01dp01icFFiscFFipFF')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007681bc06sc04i01')
2012-06-27 22:42:38,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a53290> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-27 22:42:38,686 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,686 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,733 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,733 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:38,759 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,760 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,796 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,796 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:38,820 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:38,820 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:45,063 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:45,064 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:45,819 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:45,820 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:47,496 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:47,497 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:48,251 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:48,251 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:42:49,243 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:49,243 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:49,847 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:49,847 DEBUG: fglrx is not the alternative in use
2012-06-27 22:42:50,805 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:42:50,806 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:44:38,455 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:44:38,455 DEBUG: fglrx is not the alternative in use
2012-06-27 22:44:39,385 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:44:39,385 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:44:41,029 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:44:41,029 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:44:43,915 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:44:43,915 DEBUG: fglrx is not the alternative in use
2012-06-27 22:44:45,487 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:44:45,487 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:51:52,240 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:51:52,241 DEBUG: fglrx is not the alternative in use
2012-06-27 22:51:52,762 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:51:52,762 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:51:54,198 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:51:54,198 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:51:58,224 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-06-27 22:51:58,224 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:52:10,740 DEBUG: Installing package: fglrx-updates
2012-06-27 22:52:11,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-06-27 22:52:11,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-06-27 22:52:11,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-06-27 22:52:11,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-06-27 22:52:11,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.001291
2012-06-27 22:52:12,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.053862
2012-06-27 22:52:12,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.064955
2012-06-27 22:52:12,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.065013
2012-06-27 22:52:12,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.080330
2012-06-27 22:52:12,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.081090
2012-06-27 22:52:12,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.251945
2012-06-27 22:52:13,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.450727
2012-06-27 22:52:13,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.647868
2012-06-27 22:52:14,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.818722
2012-06-27 22:52:14,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.963292
2012-06-27 22:52:15,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.129218
2012-06-27 22:52:15,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.159365
2012-06-27 22:52:15,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.160078
2012-06-27 22:52:15,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.329290
2012-06-27 22:52:16,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.506716
2012-06-27 22:52:16,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.682499
2012-06-27 22:52:17,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.859925
2012-06-27 22:52:17,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.032423
2012-06-27 22:52:18,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.208206
2012-06-27 22:52:18,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.379061
2012-06-27 22:52:19,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.559773
2012-06-27 22:52:19,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.745413
2012-06-27 22:52:20,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.939267
2012-06-27 22:52:20,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.139693
2012-06-27 22:52:21,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.338476
2012-06-27 22:52:21,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.450189
2012-06-27 22:52:21,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.466384
2012-06-27 22:52:21,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.489267
2012-06-27 22:52:22,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.571160
2012-06-27 22:52:22,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.571160
2012-06-27 22:52:22,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.586719
2012-06-27 22:52:22,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.775666
2012-06-27 22:52:22,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.776060
2012-06-27 22:52:23,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.930486
2012-06-27 22:52:23,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.084913
2012-06-27 22:52:24,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.244267
2012-06-27 22:52:24,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.385026
2012-06-27 22:52:24,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.385200
2012-06-27 22:52:24,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.544555
2012-06-27 22:52:25,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.687481
2012-06-27 22:52:25,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.845193
2012-06-27 22:52:26,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.997977
2012-06-27 22:52:26,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.172117
2012-06-27 22:52:27,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.249279
2012-06-27 22:52:27,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.249279
2012-06-27 22:52:27,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.250623
2012-06-27 22:52:27,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.359859
2012-06-27 22:52:27,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.360340
2012-06-27 22:52:28,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.547623
2012-06-27 22:52:28,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.738192
2012-06-27 22:52:29,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.938618
2012-06-27 22:52:29,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.132472
2012-06-27 22:52:30,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.250756
2012-06-27 22:52:30,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.507039
2012-06-27 22:52:30,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.535766
2012-06-27 22:52:30,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.536256
2012-06-27 22:52:31,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.697254
2012-06-27 22:52:31,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.858251
2012-06-27 22:52:32,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.015963
2012-06-27 22:52:32,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.175318
2012-06-27 22:52:33,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.336316
2012-06-27 22:52:33,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.500599
2012-06-27 22:52:34,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.659954
2012-06-27 22:52:34,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.832452
2012-06-27 22:52:35,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.009878
2012-06-27 22:52:35,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.188947
2012-06-27 22:52:36,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.377873
2012-06-27 22:52:36,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.576656
2012-06-27 22:52:37,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.775439
2012-06-27 22:52:37,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.875652
2012-06-27 22:52:38,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.112220
2012-06-27 22:52:38,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.317574
2012-06-27 22:52:39,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.475286
2012-06-27 22:52:39,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.642855
2012-06-27 22:52:40,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.802210
2012-06-27 22:52:40,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.963208
2012-06-27 22:52:41,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.127491
2012-06-27 22:52:41,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.295060
2012-06-27 22:52:42,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.457701
2012-06-27 22:52:42,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.626913
2012-06-27 22:52:43,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.804339
2012-06-27 22:52:43,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.985050
2012-06-27 22:52:44,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.125953
2012-06-27 22:52:44,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.125981
2012-06-27 22:52:44,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.322546
2012-06-27 22:52:45,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.522971
2012-06-27 22:52:45,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.670826
2012-06-27 22:52:46,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.851538
2012-06-27 22:52:46,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.047035
2012-06-27 22:52:47,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.148891
2012-06-27 22:52:47,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.235961
2012-06-27 22:52:48,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.334531
2012-06-27 22:52:48,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.337866
2012-06-27 22:52:48,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.339111
2012-06-27 22:52:48,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.372079
2012-06-27 22:52:48,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.373461
2012-06-27 22:52:48,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.463547
2012-06-27 22:52:48,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.463547
2012-06-27 22:52:48,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.465109
2012-06-27 22:52:49,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.546906
2012-06-27 22:52:49,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.548544
2012-06-27 22:52:49,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.646395
2012-06-27 22:52:49,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.646760
2012-06-27 22:52:50,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.748871
2012-06-27 22:52:50,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.862227
2012-06-27 22:52:51,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.978868
2012-06-27 22:52:51,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.111938
2012-06-27 22:52:52,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.264721
2012-06-27 22:52:52,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.437219
2012-06-27 22:52:53,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.631073
2012-06-27 22:52:53,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.831499
2012-06-27 22:52:54,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.030282
2012-06-27 22:52:54,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.155137
2012-06-27 22:52:55,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.357206
2012-06-27 22:52:55,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.610202
2012-06-27 22:52:56,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.781057
2012-06-27 22:52:56,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.963412
2012-06-27 22:52:57,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.147409
2012-06-27 22:52:57,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.328121
2012-06-27 22:52:58,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.517047
2012-06-27 22:52:58,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.705973
2012-06-27 22:52:59,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.893256
2012-06-27 22:52:59,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.083824
2012-06-27 22:53:00,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.272750
2012-06-27 22:53:00,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.468247
2012-06-27 22:53:01,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.668673
2012-06-27 22:53:01,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.865813
2012-06-27 22:53:02,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.997240
2012-06-27 22:53:02,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.207549
2012-06-27 22:53:02,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.208817
2012-06-27 22:53:02,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.240188
2012-06-27 22:53:02,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.241324
2012-06-27 22:53:02,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.301882
2012-06-27 22:53:02,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.302004
2012-06-27 22:53:03,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.431788
2012-06-27 22:53:03,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.582929
2012-06-27 22:53:04,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.729141
2012-06-27 22:53:04,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.880282
2012-06-27 22:53:05,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.024851
2012-06-27 22:53:05,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.175992
2012-06-27 22:53:06,372 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.327132
2012-06-27 22:53:06,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.484845
2012-06-27 22:53:07,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.644199
2012-06-27 22:53:07,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.813411
2012-06-27 22:53:08,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.003980
2012-06-27 22:53:08,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.201120
2012-06-27 22:53:09,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.347332
2012-06-27 22:53:09,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.572401
2012-06-27 22:53:10,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.762969
2012-06-27 22:53:10,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.920681
2012-06-27 22:53:11,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.089893
2012-06-27 22:53:11,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.257462
2012-06-27 22:53:12,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.425032
2012-06-27 22:53:12,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.584386
2012-06-27 22:53:13,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.743741
2012-06-27 22:53:13,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.911310
2012-06-27 22:53:14,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.077237
2012-06-27 22:53:14,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.243163
2012-06-27 22:53:15,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.427160
2012-06-27 22:53:15,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.621015
2012-06-27 22:53:16,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.819798
2012-06-27 22:53:16,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.002152
2012-06-27 22:53:17,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.215721
2012-06-27 22:53:17,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.391504
2012-06-27 22:53:18,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.578787
2012-06-27 22:53:18,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.770999
2012-06-27 22:53:19,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.969781
2012-06-27 22:53:19,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.168564
2012-06-27 22:53:20,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.365704
2012-06-27 22:53:20,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.566130
2012-06-27 22:53:21,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.759985
2012-06-27 22:53:21,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.957125
2012-06-27 22:53:22,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.155908
2012-06-27 22:53:22,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.356333
2012-06-27 22:53:23,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.555116
2012-06-27 22:53:23,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.714471
2012-06-27 22:53:24,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.898469
2012-06-27 22:53:24,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.033181
2012-06-27 22:53:25,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.172822
2012-06-27 22:53:25,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.309177
2012-06-27 22:53:26,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.450461
2012-06-27 22:53:26,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.588459
2012-06-27 22:53:27,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.713314
2012-06-27 22:53:27,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.861169
2012-06-27 22:53:28,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.009024
2012-06-27 22:53:28,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.170022
2012-06-27 22:53:29,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.337591
2012-06-27 22:53:29,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.516660
2012-06-27 22:53:30,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.705586
2012-06-27 22:53:30,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.904369
2012-06-27 22:53:31,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.022653
2012-06-27 22:53:31,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.144223
2012-06-27 22:53:32,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.449790
2012-06-27 22:53:32,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.602573
2012-06-27 22:53:33,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.748786
2012-06-27 22:53:33,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.896641
2012-06-27 22:53:34,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.054353
2012-06-27 22:53:34,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.208779
2012-06-27 22:53:35,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.369777
2012-06-27 22:53:35,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.535703
2012-06-27 22:53:36,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.663844
2012-06-27 22:53:36,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.864270
2012-06-27 22:53:37,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.044982
2012-06-27 22:53:37,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.233908
2012-06-27 22:53:38,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.432691
2012-06-27 22:53:38,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.631473
2012-06-27 22:53:39,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.743186
2012-06-27 22:53:39,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.978111
2012-06-27 22:53:40,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.176894
2012-06-27 22:53:40,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.329678
2012-06-27 22:53:41,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.497247
2012-06-27 22:53:41,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.664816
2012-06-27 22:53:42,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.825814
2012-06-27 22:53:42,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.981883
2012-06-27 22:53:43,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.151095
2012-06-27 22:53:43,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.318664
2012-06-27 22:53:44,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.492804
2012-06-27 22:53:44,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.670230
2012-06-27 22:53:45,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.854228
2012-06-27 22:53:45,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.043154
2012-06-27 22:53:46,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.241937
2012-06-27 22:53:46,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.442362
2012-06-27 22:53:47,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.547504
2012-06-27 22:53:47,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.687145
2012-06-27 22:53:48,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.899070
2012-06-27 22:53:48,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.997640
2012-06-27 22:53:49,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.117567
2012-06-27 22:53:49,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.235851
2012-06-27 22:53:50,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.347564
2012-06-27 22:53:50,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.455991
2012-06-27 22:53:51,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.575918
2012-06-27 22:53:51,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.685988
2012-06-27 22:53:52,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.812486
2012-06-27 22:53:52,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.942270
2012-06-27 22:53:53,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.098339
2012-06-27 22:53:53,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.269194
2012-06-27 22:53:54,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.458120
2012-06-27 22:53:54,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.656903
2012-06-27 22:53:55,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.786687
2012-06-27 22:53:55,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.957541
2012-06-27 22:53:56,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.220395
2012-06-27 22:53:56,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.389607
2012-06-27 22:53:57,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.557176
2012-06-27 22:53:57,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.732959
2012-06-27 22:53:58,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.904896
2012-06-27 22:53:58,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.077954
2012-06-27 22:53:59,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.255380
2012-06-27 22:53:59,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.424592
2012-06-27 22:54:00,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.600375
2012-06-27 22:54:00,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.786016
2012-06-27 22:54:01,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.974942
2012-06-27 22:54:01,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.170439
2012-06-27 22:54:02,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.369222
2012-06-27 22:54:02,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.569647
2012-06-27 22:54:03,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.704360
2012-06-27 22:54:03,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.931071
2012-06-27 22:54:04,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.062498
2012-06-27 22:54:04,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.210353
2012-06-27 22:54:05,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.358208
2012-06-27 22:54:05,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.506063
2012-06-27 22:54:06,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.653918
2012-06-27 22:54:06,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.798487
2012-06-27 22:54:07,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.951271
2012-06-27 22:54:07,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.100769
2012-06-27 22:54:08,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.266695
2012-06-27 22:54:08,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.437550
2012-06-27 22:54:09,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.616619
2012-06-27 22:54:09,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.813759
2012-06-27 22:54:10,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.012542
2012-06-27 22:54:10,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.212967
2012-06-27 22:54:11,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.354251
2012-06-27 22:54:11,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.590819
2012-06-27 22:54:12,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.766602
2012-06-27 22:54:12,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.947314
2012-06-27 22:54:13,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.129669
2012-06-27 22:54:13,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.315309
2012-06-27 22:54:14,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.494378
2012-06-27 22:54:14,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.680018
2012-06-27 22:54:15,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.865658
2012-06-27 22:54:15,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.051299
2012-06-27 22:54:16,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.241867
2012-06-27 22:54:16,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.430793
2012-06-27 22:54:17,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.624648
2012-06-27 22:54:17,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.823431
2012-06-27 22:54:18,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.023856
2012-06-27 22:54:18,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.191426
2012-06-27 22:54:19,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.395137
2012-06-27 22:54:19,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.564349
2012-06-27 22:54:20,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.751632
2012-06-27 22:54:20,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.942201
2012-06-27 22:54:21,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.137698
2012-06-27 22:54:21,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.328267
2012-06-27 22:54:22,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.518835
2012-06-27 22:54:22,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.714333
2012-06-27 22:54:23,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.909830
2012-06-27 22:54:23,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.105327
2012-06-27 22:54:24,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.302467
2012-06-27 22:54:25,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.501250
2012-06-27 22:54:25,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.700033
2012-06-27 22:54:26,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.900459
2012-06-27 22:54:26,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.023671
2012-06-27 22:54:27,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.271739
2012-06-27 22:54:27,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.427809
2012-06-27 22:54:28,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.588806
2012-06-27 22:54:28,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.751447
2012-06-27 22:54:29,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.914087
2012-06-27 22:54:29,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.065228
2012-06-27 22:54:30,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.221297
2012-06-27 22:54:30,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.387224
2012-06-27 22:54:31,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.554793
2012-06-27 22:54:31,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.717433
2012-06-27 22:54:32,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.896502
2012-06-27 22:54:32,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.083785
2012-06-27 22:54:33,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.280925
2012-06-27 22:54:33,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.481351
2012-06-27 22:54:34,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.680134
2012-06-27 22:54:34,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.752419
2012-06-27 22:54:35,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.046486
2012-06-27 22:54:35,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.184484
2012-06-27 22:54:36,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.332339
2012-06-27 22:54:36,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.468694
2012-06-27 22:54:37,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.608335
2012-06-27 22:54:37,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.761119
2012-06-27 22:54:38,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.908974
2012-06-27 22:54:38,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.056829
2012-06-27 22:54:39,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.207970
2012-06-27 22:54:39,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.367325
2012-06-27 22:54:40,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.536536
2012-06-27 22:54:40,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.717248
2012-06-27 22:54:41,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.914388
2012-06-27 22:54:41,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.113171
2012-06-27 22:54:42,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.310311
2012-06-27 22:54:42,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.418738
2012-06-27 22:54:43,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.694734
2012-06-27 22:54:43,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.872161
2012-06-27 22:54:44,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.054515
2012-06-27 22:54:44,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.246727
2012-06-27 22:54:45,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.435653
2012-06-27 22:54:45,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.629507
2012-06-27 22:54:46,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.816790
2012-06-27 22:54:46,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.005716
2012-06-27 22:54:47,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.194642
2012-06-27 22:54:47,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.386854
2012-06-27 22:54:48,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.580708
2012-06-27 22:54:48,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.779491
2012-06-27 22:54:49,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.978274
2012-06-27 22:54:49,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.158986
2012-06-27 22:54:50,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.278912
2012-06-27 22:54:50,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.543409
2012-06-27 22:54:51,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.696192
2012-06-27 22:54:51,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.848976
2012-06-27 22:54:52,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.019831
2012-06-27 22:54:52,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.184114
2012-06-27 22:54:53,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.345112
2012-06-27 22:54:53,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.504467
2012-06-27 22:54:54,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.670393
2012-06-27 22:54:54,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.842890
2012-06-27 22:54:55,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.018674
2012-06-27 22:54:55,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.199385
2012-06-27 22:54:56,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.391597
2012-06-27 22:54:56,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.588737
2012-06-27 22:54:57,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.789163
2012-06-27 22:54:57,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.984660
2012-06-27 22:54:58,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.165372
2012-06-27 22:54:58,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.339512
2012-06-27 22:54:59,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.525152
2012-06-27 22:54:59,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.715721
2012-06-27 22:55:00,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.912861
2012-06-27 22:55:00,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.103430
2012-06-27 22:55:01,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.293999
2012-06-27 22:55:01,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.487853
2012-06-27 22:55:02,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.681708
2012-06-27 22:55:02,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.877205
2012-06-27 22:55:03,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.072702
2012-06-27 22:55:03,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.271485
2012-06-27 22:55:04,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.470268
2012-06-27 22:55:04,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.670694
2012-06-27 22:55:05,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.800478
2012-06-27 22:55:05,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.017332
2012-06-27 22:55:06,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.166830
2012-06-27 22:55:06,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.313042
2012-06-27 22:55:07,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.464183
2012-06-27 22:55:07,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.615323
2012-06-27 22:55:08,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.764821
2012-06-27 22:55:08,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.912676
2012-06-27 22:55:09,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.060531
2012-06-27 22:55:09,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.224815
2012-06-27 22:55:10,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.384170
2012-06-27 22:55:10,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.561596
2012-06-27 22:55:11,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.743950
2012-06-27 22:55:11,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.941090
2012-06-27 22:55:12,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.064303
2012-06-27 22:55:12,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.305799
2012-06-27 22:55:13,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.491440
2012-06-27 22:55:13,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.632723
2012-06-27 22:55:14,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.777293
2012-06-27 22:55:14,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.923505
2012-06-27 22:55:15,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.071360
2012-06-27 22:55:15,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.219215
2012-06-27 22:55:16,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.368713
2012-06-27 22:55:16,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.503425
2012-06-27 22:55:17,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.662780
2012-06-27 22:55:17,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.815564
2012-06-27 22:55:18,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.986419
2012-06-27 22:55:18,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.173702
2012-06-27 22:55:19,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.370842
2012-06-27 22:55:19,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.571268
2012-06-27 22:55:20,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.696123
2012-06-27 22:55:20,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.888335
2012-06-27 22:55:21,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.142974
2012-06-27 22:55:21,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.292472
2012-06-27 22:55:22,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.466612
2012-06-27 22:55:22,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.637467
2012-06-27 22:55:23,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.809964
2012-06-27 22:55:23,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.977534
2012-06-27 22:55:24,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.148388
2012-06-27 22:55:24,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.322529
2012-06-27 22:55:25,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.498312
2012-06-27 22:55:25,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.677381
2012-06-27 22:55:26,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.864664
2012-06-27 22:55:26,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.056875
2012-06-27 22:55:27,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.255658
2012-06-27 22:55:27,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.456084
2012-06-27 22:55:28,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.645010
2012-06-27 22:55:28,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.833936
2012-06-27 22:55:29,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.029433
2012-06-27 22:55:29,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.228216
2012-06-27 22:55:30,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.426999
2012-06-27 22:55:30,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.627425
2012-06-27 22:55:31,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.826208
2012-06-27 22:55:31,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.024991
2012-06-27 22:55:32,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.225416
2012-06-27 22:55:32,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.424199
2012-06-27 22:55:33,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.622982
2012-06-27 22:55:33,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.772480
2012-06-27 22:55:34,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.982763
2012-06-27 22:55:34,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.138832
2012-06-27 22:55:35,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.293259
2012-06-27 22:55:35,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.447685
2012-06-27 22:55:36,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.613611
2012-06-27 22:55:36,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.763109
2012-06-27 22:55:37,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.920821
2012-06-27 22:55:37,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.080176
2012-06-27 22:55:38,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.242817
2012-06-27 22:55:38,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.410386
2012-06-27 22:55:39,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.584526
2012-06-27 22:55:39,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.763595
2012-06-27 22:55:40,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.947592
2012-06-27 22:55:40,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.093805
2012-06-27 22:55:41,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.310659
2012-06-27 22:55:41,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.432228
2012-06-27 22:55:42,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.580084
2012-06-27 22:55:42,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.719724
2012-06-27 22:55:43,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.847865
2012-06-27 22:55:43,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.990792
2012-06-27 22:55:44,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.127147
2012-06-27 22:55:44,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.276645
2012-06-27 22:55:45,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.429429
2012-06-27 22:55:45,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.585498
2012-06-27 22:55:46,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.748139
2012-06-27 22:55:46,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.923922
2012-06-27 22:55:47,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.117776
2012-06-27 22:55:47,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.316559
2012-06-27 22:55:48,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.462771
2012-06-27 22:55:48,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.653340
2012-06-27 22:55:49,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.834052
2012-06-27 22:55:49,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.950693
2012-06-27 22:55:50,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.065691
2012-06-27 22:55:50,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.175761
2012-06-27 22:55:51,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.295688
2012-06-27 22:55:51,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.417258
2012-06-27 22:55:52,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.533899
2012-06-27 22:55:52,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.647255
2012-06-27 22:55:53,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.773753
2012-06-27 22:55:53,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.918322
2012-06-27 22:55:54,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.062892
2012-06-27 22:55:54,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.227175
2012-06-27 22:55:55,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.416101
2012-06-27 22:55:55,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.613241
2012-06-27 22:55:56,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.813667
2012-06-27 22:55:56,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.907308
2012-06-27 22:55:57,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.145519
2012-06-27 22:55:57,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.362373
2012-06-27 22:55:58,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.529942
2012-06-27 22:55:58,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.700797
2012-06-27 22:55:59,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.871652
2012-06-27 22:55:59,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.040864
2012-06-27 22:56:00,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.210076
2012-06-27 22:56:00,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.385859
2012-06-27 22:56:01,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.555071
2012-06-27 22:56:01,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.729211
2012-06-27 22:56:02,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.916494
2012-06-27 22:56:02,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.105420
2012-06-27 22:56:03,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.304203
2012-06-27 22:56:03,674 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.502986
2012-06-27 22:56:04,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.680412
2012-06-27 22:56:04,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.843053
2012-06-27 22:56:05,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.050050
2012-06-27 22:56:05,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.202833
2012-06-27 22:56:06,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.368760
2012-06-27 22:56:06,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.526472
2012-06-27 22:56:07,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.689112
2012-06-27 22:56:07,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.853396
2012-06-27 22:56:08,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.016036
2012-06-27 22:56:08,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.185248
2012-06-27 22:56:09,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.352817
2012-06-27 22:56:09,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.530243
2012-06-27 22:56:10,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.712598
2012-06-27 22:56:10,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.908095
2012-06-27 22:56:11,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.106878
2012-06-27 22:56:11,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.305661
2012-06-27 22:56:12,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.471587
2012-06-27 22:56:12,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.629299
2012-06-27 22:56:13,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.879010
2012-06-27 22:56:13,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.040008
2012-06-27 22:56:14,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.205934
2012-06-27 22:56:14,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.381717
2012-06-27 22:56:15,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.557501
2012-06-27 22:56:15,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.726712
2012-06-27 22:56:16,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.895924
2012-06-27 22:56:16,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.071708
2012-06-27 22:56:17,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.245848
2012-06-27 22:56:17,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.419988
2012-06-27 22:56:18,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.605629
2012-06-27 22:56:18,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.801126
2012-06-27 22:56:19,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.996623
2012-06-27 22:56:19,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.197049
2012-06-27 22:56:20,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.394189
2012-06-27 22:56:20,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.473045
2012-06-27 22:56:21,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.617614
2012-06-27 22:56:21,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.952753
2012-06-27 22:56:22,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.098965
2012-06-27 22:56:22,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.261605
2012-06-27 22:56:23,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.425889
2012-06-27 22:56:23,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.588529
2012-06-27 22:56:24,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.742956
2012-06-27 22:56:24,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.899025
2012-06-27 22:56:25,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.053451
2012-06-27 22:56:25,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.216092
2012-06-27 22:56:26,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.390232
2012-06-27 22:56:26,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.556159
2012-06-27 22:56:27,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.748370
2012-06-27 22:56:27,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.945510
2012-06-27 22:56:28,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.144293
2012-06-27 22:56:28,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.241220
2012-06-27 22:56:29,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.495860
2012-06-27 22:56:29,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.707785
2012-06-27 22:56:30,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.878640
2012-06-27 22:56:30,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.054423
2012-06-27 22:56:31,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.226921
2012-06-27 22:56:31,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.397775
2012-06-27 22:56:32,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.571916
2012-06-27 22:56:32,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.747699
2012-06-27 22:56:33,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.918554
2012-06-27 22:56:33,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.095980
2012-06-27 22:56:34,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.278335
2012-06-27 22:56:34,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.467260
2012-06-27 22:56:35,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.662758
2012-06-27 22:56:35,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.861541
2012-06-27 22:56:36,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.060324
2012-06-27 22:56:36,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.160536
2012-06-27 22:56:37,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.434890
2012-06-27 22:56:37,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.602459
2012-06-27 22:56:38,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.765099
2012-06-27 22:56:38,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.937597
2012-06-27 22:56:39,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.106809
2012-06-27 22:56:39,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.277664
2012-06-27 22:56:40,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.435376
2012-06-27 22:56:40,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.611159
2012-06-27 22:56:41,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.783656
2012-06-27 22:56:41,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.956154
2012-06-27 22:56:42,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.135223
2012-06-27 22:56:42,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.241622
2012-06-27 22:56:42,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.241653
2012-06-27 22:56:43,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.432222
2012-06-27 22:56:43,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.631005
2012-06-27 22:56:44,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.831431
2012-06-27 22:56:44,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.910287
2012-06-27 22:56:45,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.210926
2012-06-27 22:56:45,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.358781
2012-06-27 22:56:46,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.518136
2012-06-27 22:56:46,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.672562
2012-06-27 22:56:47,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.835202
2012-06-27 22:56:47,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.996200
2012-06-27 22:56:48,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.162126
2012-06-27 22:56:48,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.319839
2012-06-27 22:56:49,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.480836
2012-06-27 22:56:49,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.646762
2012-06-27 22:56:50,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.825831
2012-06-27 22:56:50,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.001615
2012-06-27 22:56:51,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.195469
2012-06-27 22:56:51,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.395895
2012-06-27 22:56:52,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.561821
2012-06-27 22:56:52,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.767175
2012-06-27 22:56:53,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.883817
2012-06-27 22:56:53,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.011958
2012-06-27 22:56:54,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.148313
2012-06-27 22:56:54,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.276454
2012-06-27 22:56:55,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.407881
2012-06-27 22:56:55,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.544236
2012-06-27 22:56:56,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.677305
2012-06-27 22:56:56,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.807089
2012-06-27 22:56:57,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.954944
2012-06-27 22:56:57,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.120871
2012-06-27 22:56:58,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.290082
2012-06-27 22:56:58,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.480651
2012-06-27 22:56:59,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.679434
2012-06-27 22:56:59,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.820718
2012-06-27 22:57:00,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.017858
2012-06-27 22:57:00,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.244569
2012-06-27 22:57:01,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.395710
2012-06-27 22:57:01,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.566564
2012-06-27 22:57:02,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.743991
2012-06-27 22:57:02,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.913202
2012-06-27 22:57:02,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 100.000000
2012-06-27 22:57:03,319 DEBUG: install progress dpkg-exec 0.000000
2012-06-27 22:57:05,162 DEBUG: install progress libaudio2 0.000000
2012-06-27 22:57:05,263 DEBUG: install progress libaudio2 0.952381
2012-06-27 22:57:05,546 DEBUG: install progress libaudio2 1.904760
2012-06-27 22:57:05,596 DEBUG: install progress libaudio2 2.857140
2012-06-27 22:57:05,887 DEBUG: install progress mysql-common 2.857140
2012-06-27 22:57:05,887 DEBUG: install progress mysql-common 3.809520
2012-06-27 22:57:06,274 DEBUG: install progress mysql-common 4.761900
2012-06-27 22:57:06,307 DEBUG: install progress mysql-common 5.714290
2012-06-27 22:57:06,540 DEBUG: install progress libmysqlclient18 5.714290
2012-06-27 22:57:06,641 DEBUG: install progress libmysqlclient18 6.666670
2012-06-27 22:57:06,982 DEBUG: install progress libmysqlclient18 7.619050
2012-06-27 22:57:07,023 DEBUG: install progress libmysqlclient18 8.571430
2012-06-27 22:57:07,448 DEBUG: install progress libqtcore4 8.571430
2012-06-27 22:57:07,549 DEBUG: install progress libqtcore4 9.523810
2012-06-27 22:57:08,198 DEBUG: install progress libqtcore4 10.476200
2012-06-27 22:57:08,231 DEBUG: install progress libqtcore4 11.428600
2012-06-27 22:57:08,628 DEBUG: install progress libqt4-xml 11.428600
2012-06-27 22:57:08,728 DEBUG: install progress libqt4-xml 12.381000
2012-06-27 22:57:09,048 DEBUG: install progress libqt4-xml 13.333300
2012-06-27 22:57:09,089 DEBUG: install progress libqt4-xml 14.285700
2012-06-27 22:57:09,458 DEBUG: install progress libqt4-dbus 14.285700
2012-06-27 22:57:09,558 DEBUG: install progress libqt4-dbus 15.238100
2012-06-27 22:57:09,833 DEBUG: install progress libqt4-dbus 16.190500
2012-06-27 22:57:09,866 DEBUG: install progress libqt4-dbus 17.142900
2012-06-27 22:57:10,125 DEBUG: install progress libqt4-network 17.142900
2012-06-27 22:57:10,226 DEBUG: install progress libqt4-network 18.095200
2012-06-27 22:57:10,636 DEBUG: install progress libqt4-network 19.047600
2012-06-27 22:57:10,688 DEBUG: install progress libqt4-network 20.000000
2012-06-27 22:57:11,087 DEBUG: install progress libqt4-script 20.000000
2012-06-27 22:57:11,188 DEBUG: install progress libqt4-script 20.952400
2012-06-27 22:57:12,213 DEBUG: install progress libqt4-script 21.904800
2012-06-27 22:57:12,278 DEBUG: install progress libqt4-script 22.857100
2012-06-27 22:57:12,519 DEBUG: install progress libqt4-sql 22.857100
2012-06-27 22:57:12,619 DEBUG: install progress libqt4-sql 23.809500
2012-06-27 22:57:12,937 DEBUG: install progress libqt4-sql 24.761900
2012-06-27 22:57:12,971 DEBUG: install progress libqt4-sql 25.714300
2012-06-27 22:57:13,198 DEBUG: install progress libqt4-xmlpatterns 25.714300
2012-06-27 22:57:13,298 DEBUG: install progress libqt4-xmlpatterns 26.666700
2012-06-27 22:57:13,717 DEBUG: install progress libqt4-xmlpatterns 27.619000
2012-06-27 22:57:13,758 DEBUG: install progress libqt4-xmlpatterns 28.571400
2012-06-27 22:57:14,278 DEBUG: install progress libqtgui4 28.571400
2012-06-27 22:57:14,378 DEBUG: install progress libqtgui4 29.523800
2012-06-27 22:57:15,129 DEBUG: install progress libqtgui4 30.476200
2012-06-27 22:57:15,162 DEBUG: install progress libqtgui4 31.428600
2012-06-27 22:57:15,518 DEBUG: install progress libqt4-declarative 31.428600
2012-06-27 22:57:15,618 DEBUG: install progress libqt4-declarative 32.381000
2012-06-27 22:57:16,053 DEBUG: install progress libqt4-declarative 33.333300
2012-06-27 22:57:16,086 DEBUG: install progress libqt4-declarative 34.285700
2012-06-27 22:57:16,247 DEBUG: install progress libqt4-sql-mysql 34.285700
2012-06-27 22:57:16,347 DEBUG: install progress libqt4-sql-mysql 35.238100
2012-06-27 22:57:16,872 DEBUG: install progress libqt4-sql-mysql 36.190500
2012-06-27 22:57:16,905 DEBUG: install progress libqt4-sql-mysql 37.142900
2012-06-27 22:57:17,209 DEBUG: install progress patch 37.142900
2012-06-27 22:57:17,309 DEBUG: install progress patch 38.095200
2012-06-27 22:57:17,779 DEBUG: install progress patch 39.047600
2012-06-27 22:57:17,834 DEBUG: install progress patch 40.000000
2012-06-27 22:57:18,061 DEBUG: install progress dkms 40.000000
2012-06-27 22:57:18,162 DEBUG: install progress dkms 40.952400
2012-06-27 22:57:18,736 DEBUG: install progress dkms 41.904800
2012-06-27 22:57:18,792 DEBUG: install progress dkms 42.857100
2012-06-27 22:57:19,019 DEBUG: install progress fakeroot 42.857100
2012-06-27 22:57:19,119 DEBUG: install progress fakeroot 43.809500
2012-06-27 22:57:19,651 DEBUG: install progress fakeroot 44.761900
2012-06-27 22:57:19,684 DEBUG: install progress fakeroot 45.714300
2012-06-27 22:57:20,076 DEBUG: install progress libc6-i386 45.714300
2012-06-27 22:57:20,176 DEBUG: install progress libc6-i386 46.666700
2012-06-27 22:57:20,863 DEBUG: install progress libc6-i386 47.619000
2012-06-27 22:57:20,942 DEBUG: install progress libc6-i386 48.571400
2012-06-27 22:57:21,103 DEBUG: install progress qdbus 48.571400
2012-06-27 22:57:21,204 DEBUG: install progress qdbus 49.523800
2012-06-27 22:57:21,539 DEBUG: install progress qdbus 50.476200
2012-06-27 22:57:21,624 DEBUG: install progress qdbus 51.428600
2012-06-27 22:57:21,877 DEBUG: install progress lib32gcc1 51.428600
2012-06-27 22:57:21,978 DEBUG: install progress lib32gcc1 52.381000
2012-06-27 22:57:22,186 DEBUG: install progress lib32gcc1 53.333300
2012-06-27 22:57:22,219 DEBUG: install progress lib32gcc1 54.285700
2012-06-27 22:57:22,534 DEBUG: install progress fglrx-updates 54.285700
2012-06-27 22:57:22,634 DEBUG: install progress fglrx-updates 55.238100
2012-06-27 22:57:26,982 DEBUG: install progress fglrx-updates 56.190500
2012-06-27 22:57:27,015 DEBUG: install progress fglrx-updates 57.142900
2012-06-27 22:57:27,205 DEBUG: install progress fglrx-amdcccle-updates 57.142900
2012-06-27 22:57:27,305 DEBUG: install progress fglrx-amdcccle-updates 58.095200
2012-06-27 22:57:27,978 DEBUG: install progress fglrx-amdcccle-updates 59.047600
2012-06-27 22:57:28,030 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-06-27 22:57:28,067 DEBUG: install progress man-db 60.000000
2012-06-27 22:57:30,996 DEBUG: install progress ureadahead 60.000000
2012-06-27 22:57:31,312 DEBUG: install progress dpkg-exec 60.000000
2012-06-27 22:57:31,340 DEBUG: install progress libaudio2 60.000000
2012-06-27 22:57:31,396 DEBUG: install progress libaudio2 60.952400
2012-06-27 22:57:31,482 DEBUG: install progress libaudio2 61.904800
2012-06-27 22:57:31,755 DEBUG: install progress mysql-common 61.904800
2012-06-27 22:57:31,855 DEBUG: install progress mysql-common 62.857100
2012-06-27 22:57:31,898 DEBUG: install progress mysql-common 63.809500
2012-06-27 22:57:31,933 DEBUG: install progress libmysqlclient18 63.809500
2012-06-27 22:57:32,087 DEBUG: install progress libmysqlclient18 64.761900
2012-06-27 22:57:32,196 DEBUG: install progress libmysqlclient18 65.714300
2012-06-27 22:57:32,248 DEBUG: install progress libqtcore4 65.714300
2012-06-27 22:57:32,416 DEBUG: install progress libqtcore4 66.666700
2012-06-27 22:57:32,570 DEBUG: install progress libqtcore4 67.619000
2012-06-27 22:57:32,621 DEBUG: install progress libqt4-xml 67.619000
2012-06-27 22:57:32,656 DEBUG: install progress libqt4-xml 68.571400
2012-06-27 22:57:32,761 DEBUG: install progress libqt4-xml 69.523800
2012-06-27 22:57:32,813 DEBUG: install progress libqt4-dbus 69.523800
2012-06-27 22:57:32,848 DEBUG: install progress libqt4-dbus 70.476200
2012-06-27 22:57:32,978 DEBUG: install progress libqt4-dbus 71.428600
2012-06-27 22:57:33,030 DEBUG: install progress libqt4-network 71.428600
2012-06-27 22:57:33,065 DEBUG: install progress libqt4-network 72.381000
2012-06-27 22:57:33,209 DEBUG: install progress libqt4-network 73.333300
2012-06-27 22:57:33,349 DEBUG: install progress libqt4-script 73.333300
2012-06-27 22:57:33,411 DEBUG: install progress libqt4-script 74.285700
2012-06-27 22:57:33,519 DEBUG: install progress libqt4-script 75.238100
2012-06-27 22:57:33,571 DEBUG: install progress libqt4-sql 75.238100
2012-06-27 22:57:33,606 DEBUG: install progress libqt4-sql 76.190500
2012-06-27 22:57:33,708 DEBUG: install progress libqt4-sql 77.142900
2012-06-27 22:57:33,866 DEBUG: install progress libqt4-xmlpatterns 77.142900
2012-06-27 22:57:33,927 DEBUG: install progress libqt4-xmlpatterns 78.095200
2012-06-27 22:57:34,038 DEBUG: install progress libqt4-xmlpatterns 79.047600
2012-06-27 22:57:34,090 DEBUG: install progress libqt4-sql-mysql 79.047600
2012-06-27 22:57:34,133 DEBUG: install progress libqt4-sql-mysql 80.000000
2012-06-27 22:57:34,263 DEBUG: install progress libqt4-sql-mysql 80.952400
2012-06-27 22:57:34,336 DEBUG: install progress patch 80.952400
2012-06-27 22:57:34,370 DEBUG: install progress patch 81.904800
2012-06-27 22:57:34,405 DEBUG: install progress patch 82.857100
2012-06-27 22:57:34,440 DEBUG: install progress dkms 82.857100
2012-06-27 22:57:35,510 DEBUG: install progress dkms 83.809500
2012-06-27 22:57:35,548 DEBUG: install progress dkms 84.761900
2012-06-27 22:57:35,638 DEBUG: install progress fakeroot 84.761900
2012-06-27 22:57:35,673 DEBUG: install progress fakeroot 85.714300
2012-06-27 22:57:36,172 DEBUG: install progress fakeroot 86.666700
2012-06-27 22:57:36,224 DEBUG: install progress libc6-i386 86.666700
2012-06-27 22:57:36,394 DEBUG: install progress libc6-i386 87.619000
2012-06-27 22:57:36,522 DEBUG: install progress libc6-i386 88.571400
2012-06-27 22:57:36,721 DEBUG: install progress qdbus 88.571400
2012-06-27 22:57:36,793 DEBUG: install progress qdbus 89.523800
2012-06-27 22:57:36,828 DEBUG: install progress qdbus 90.476200
2012-06-27 22:57:36,871 DEBUG: install progress lib32gcc1 90.476200
2012-06-27 22:57:36,906 DEBUG: install progress lib32gcc1 91.428600
2012-06-27 22:57:37,134 DEBUG: install progress lib32gcc1 92.381000
2012-06-27 22:57:37,188 DEBUG: install progress libqt4-declarative 92.381000
2012-06-27 22:57:37,221 DEBUG: install progress libqt4-declarative 93.333300
2012-06-27 22:57:37,332 DEBUG: install progress libqt4-declarative 94.285700
2012-06-27 22:57:37,497 DEBUG: install progress libqtgui4 94.285700
2012-06-27 22:57:37,559 DEBUG: install progress libqtgui4 95.238100
2012-06-27 22:57:37,676 DEBUG: install progress libqtgui4 96.190500
2012-06-27 22:57:37,729 DEBUG: install progress fglrx-updates 96.190500
2012-06-27 22:57:38,069 DEBUG: install progress fglrx-updates 97.142900
2012-06-27 22:58:06,976 DEBUG: install progress fglrx-updates 98.095200
2012-06-27 22:58:07,213 DEBUG: install progress fglrx-amdcccle-updates 98.095200
2012-06-27 22:58:07,287 DEBUG: install progress fglrx-amdcccle-updates 99.047600
2012-06-27 22:58:07,322 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-06-27 22:58:07,366 DEBUG: install progress libc-bin 100.000000
2012-06-27 22:58:07,631 DEBUG: install progress initramfs-tools 100.000000
2012-06-27 22:58:16,949 DEBUG: Selecting previously unselected package libaudio2.
(Reading database ... 154316 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.3-4_amd64.deb) ...
Selecting previously unselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.5.24-0ubuntu0.12.04.1_all.deb) ...
Selecting previously unselected package libmysqlclient18.
Unpacking libmysqlclient18 (from .../libmysqlclient18_5.5.24-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-xmlpatterns.
Unpacking libqt4-xmlpatterns (from .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-declarative.
Unpacking libqt4-declarative (from .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package patch.
Unpacking patch (from .../patch_2.6.1-3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10_amd64.deb) ...
Selecting previously unselected package qdbus.
Unpacking qdbus (from .../qdbus_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libaudio2 (1.9.3-4) ...
Setting up mysql-common (5.5.24-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18 (5.5.24-0ubuntu0.12.04.1) ...
Setting up libqtcore4 (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-xml (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-dbus (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-network (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-script (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-xmlpatterns (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql-mysql (4:4.8.1-0ubuntu4.1) ...
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc6-i386 (2.15-0ubuntu10) ...
Setting up qdbus (4:4.8.1-0ubuntu4.1) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up libqt4-declarative (4:4.8.1-0ubuntu4.1) ...
Setting up libqtgui4 (4:4.8.1-0ubuntu4.1) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-25-generic
Building for architecture x86_64
Building initial module for 3.2.0-25-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-25-generic/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic

2012-06-27 22:58:17,076 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-06-27 22:58:29,120 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:29,120 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:29,127 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:29,127 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,338 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,338 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,353 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,353 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,382 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,382 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-27 22:58:37,416 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,416 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,431 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,431 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,473 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,473 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,488 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,488 DEBUG: fglrx_updates is not the alternative in use
2012-06-27 22:58:37,515 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-27 22:58:37,515 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

```

---

### Post by weirddan455 on 2012-06-28
Ok this is very strange.  AMD Catalyst Control Center was added to my system and a lsmod shows that fglrx is indeed loaded and the open source radeon is not.  It appers to be installed but when I try reinstalling through the Ubuntu driver program it still says failed.  It makes me a little uneasy.

---

### Post by Redblade20XX on 2012-06-28
Take a look here, it should help you: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

### Post by Lyfang on 2012-06-28
Have you tried to install the proprietary driver downloaded from AMD'S website? [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by weirddan455 on 2012-06-28
> **Redblade20XX said:**
> Take a look here, it should help you: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

It says using the Ubuntu supplied drivers are the safest, which is what I used.  I did it this way.

> You must have jockey-common and jockey-gtk (or jockey-kde for Kubuntu) packages installed. For the default Ubuntu desktop (Unity), go to the dashboard home and search for "Additional Drivers" in the applications search field (or double-click the "available driver" notification icon) and activate the "ATI/AMD proprietary FGLRX graphics driver". 

Like I said, it looks like the driver is now installed and working but I'm a little uneasy that something went wrong because of that error.  I could try installing it manually but the problem is now I don't know how to uninstall the mess that GUI installer made since it says the driver isn't installed and trying to install again just gives the same error.

---

### Post by Lyfang on 2012-06-28
Is done at your own risk, uninstalling the FGLRX driver.

Installed manually:
```
sudo /usr/share/ati/fglrx-uninstall.sh
```

Ubuntu supplied Jockey driver, I'm not sure but maybe something like:
```
sudo apt-get purge fglrx
```

After that, try to do a fresh install of the FGLRX driver.

---

### Post by weirddan455 on 2012-06-28
OK, so at first I was using the "post-release updates" version and that was the one giving me errors.  I used sudo apt-get purge fglrx-updates and tried reinstalling it multiple times only to get the same error.  Finally, I decided to try the one that didn't say "post-release updates" and that one installed error free.  The version number in ATI CCC and in Synaptic Package Manager was the exact same in both packages, only the post-release updates one gave an error for no good reason.  I'm about to figure out how to post a bug report on this.

---

### Post by weirddan455 on 2012-06-28
Reported the bug.  Hopefully I did that well enough.

[https://bugs.launchpad.net/bugs/1019007](https://bugs.launchpad.net/bugs/1019007)

---

