---
title: "proprietary drivers not installing"
date: 2012-08-10
forum: General Help
---

### Post by gandalf3 on 2012-08-10
i just went from from 11.10 to 12.04,
and when i tried to install proprietary drivers for my Geforce Nvida 7900GT GPU, i got an error saying "sorry, installation of the drive failed, please look at the log file /var/log/jockey.log for details"

here's the content of the file:
```
2012-08-10 13:28:57,450 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0>
2012-08-10 13:29:04,811 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-08-10 13:29:05,259 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-08-10 13:29:05,267 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-08-10 13:29:05,471 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-08-10 13:29:05,571 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-08-10 13:29:05,583 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-08-10 13:29:05,583 DEBUG: fglrx.available: falling back to default
2012-08-10 13:29:05,871 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 13:29:05,885 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-10 13:29:05,899 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-08-10 13:29:05,900 DEBUG: fglrx.available: falling back to default
2012-08-10 13:29:05,996 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-08-10 13:29:05,996 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-08-10 13:29:06,040 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-08-10 13:29:06,053 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-08-10 13:29:06,056 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,101 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 13:29:06,102 DEBUG: NVIDIA accelerated graphics driver not available
2012-08-10 13:29:06,116 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-10 13:29:06,128 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-08-10 13:29:06,130 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,240 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-08-10 13:29:06,252 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 13:29:06,271 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-08-10 13:29:06,272 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,376 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 13:29:06,389 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-08-10 13:29:06,405 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-08-10 13:29:06,407 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,523 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 13:29:06,534 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-08-10 13:29:06,547 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-08-10 13:29:06,548 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,657 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-08-10 13:29:06,668 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-08-10 13:29:06,684 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-08-10 13:29:06,685 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:06,723 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 13:29:06,723 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-08-10 13:29:06,723 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-08-10 13:29:06,735 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-08-10 13:29:06,785 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-08-10 13:29:06,786 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-08-10 13:29:06,786 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-08-10 13:29:06,797 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-08-10 13:29:06,798 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-08-10 13:29:06,798 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-08-10 13:29:06,798 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-08-10 13:29:06,817 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-08-10 13:29:06,817 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-08-10 13:29:06,861 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-08-10 13:29:06,861 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-08-10 13:29:06,880 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-08-10 13:29:06,891 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-08-10 13:29:06,975 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-08-10 13:29:06,976 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-08-10 13:29:07,031 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-08-10 13:29:07,065 DEBUG: Software modem not available
2012-08-10 13:29:07,066 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-08-10 13:29:07,173 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-08-10 13:29:07,174 DEBUG: Firmware for DVB cards not available
2012-08-10 13:29:07,174 DEBUG: all custom handlers loaded
2012-08-10 13:29:07,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-08-10 13:29:07,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,2,4,11,k71,72,73,74,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,1FD,1FE,1FF,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2012-08-10 13:29:07,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:07,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:07,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:07,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:07,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:07,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:07,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:07,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:07,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-08-10 13:29:07,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-10 13:29:07,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000075sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:08,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'platform:pcspkr')
2012-08-10 13:29:08,360 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-08-10 13:29:08,360 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,361 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-08-10 13:29:08,361 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000007Asv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:08,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-10 13:29:08,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:08,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:08,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:08,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:08,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2012-08-10 13:29:08,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:08,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-08-10 13:29:08,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-08-10 13:29:08,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'platform:regulatory')
2012-08-10 13:29:08,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v0000104Cd00008023sv00001043sd0000808Bbc0Csc00i10')
2012-08-10 13:29:08,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-08-10 13:29:08,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-10 13:29:08,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000071sv00001043sd00008189bc06sc00i00')
2012-08-10 13:29:08,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000079sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:08,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNPB006:')
2012-08-10 13:29:08,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000055sv00001043sd00008162bc01sc01i85')
2012-08-10 13:29:08,724 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2012-08-10 13:29:08,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-10 13:29:08,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000007Fsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:08,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000078sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:08,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-10 13:29:08,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01')
2012-08-10 13:29:08,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000050sv00001043sd00008162bc06sc01i00')
2012-08-10 13:29:08,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v00001095d00003132sv00001043sd0000819Fbc01sc80i00')
2012-08-10 13:29:08,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_sil24'}
2012-08-10 13:29:08,789 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_sil24', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000053sv00001043sd00008162bc01sc01i8a')
2012-08-10 13:29:08,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2012-08-10 13:29:08,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:08,807 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:08,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v0925p1234d0288dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:08,809 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:08,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v00001102d00007002sv00001102sd00000020bc09sc80i00')
2012-08-10 13:29:08,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'emu10k1_gp'}
2012-08-10 13:29:08,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'emu10k1_gp', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-08-10 13:29:08,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:08,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:08,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:08,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-08-10 13:29:08,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:08,828 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:08,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2012-08-10 13:29:08,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:08,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,833 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:08,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-10 13:29:08,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000291sv000010DEsd00000321bc03sc00i00')
2012-08-10 13:29:08,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-08-10 13:29:08,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-08-10 13:29:08,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:08,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-08-10 13:29:08,925 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:08,925 DEBUG: nvidia_current is not the alternative in use
2012-08-10 13:29:08,850 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:08,934 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-10 13:29:08,950 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,029 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,029 DEBUG: nvidia_current is not the alternative in use
2012-08-10 13:29:08,997 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:09,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2012-08-10 13:29:09,070 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,071 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 13:29:09,030 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,082 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-08-10 13:29:09,099 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,179 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,180 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 13:29:09,146 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2012-08-10 13:29:09,215 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,216 DEBUG: nvidia_96_updates is not the alternative in use
2012-08-10 13:29:09,180 DEBUG: found match in handler pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,225 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-08-10 13:29:09,237 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,279 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 13:29:09,309 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,309 DEBUG: nvidia_96_updates is not the alternative in use
2012-08-10 13:29:09,279 DEBUG: ignoring unavailable handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,310 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96', 'package': 'nvidia-96'}
2012-08-10 13:29:09,341 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,341 DEBUG: nvidia_96 is not the alternative in use
2012-08-10 13:29:09,311 DEBUG: found match in handler pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:09,349 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-08-10 13:29:09,363 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,405 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 13:29:09,468 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,468 DEBUG: nvidia_96 is not the alternative in use
2012-08-10 13:29:09,406 DEBUG: ignoring unavailable handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:09,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2012-08-10 13:29:09,507 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,508 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 13:29:09,469 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:09,514 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-08-10 13:29:09,527 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,636 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,636 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 13:29:09,604 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 13:29:09,637 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-08-10 13:29:09,666 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,666 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 13:29:09,637 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,675 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 13:29:09,686 DEBUG: nvidia.available: falling back to default
2012-08-10 13:29:09,761 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:09,762 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 13:29:09,725 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 13:29:09,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v0D8Cp0008e0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-08-10 13:29:09,763 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:09,763 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:09,763 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:09,763 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:09,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-10 13:29:09,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v00001102d00000002sv00001102sd00008022bc04sc01i00')
2012-08-10 13:29:09,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_emu10k1'}
2012-08-10 13:29:09,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_emu10k1', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:09,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0405:bd08/17/2006:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N32-SLI-Deluxe:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-08-10 13:29:09,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000052sv00001043sd00008162bc0Csc05i00')
2012-08-10 13:29:09,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2012-08-10 13:29:09,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:09,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-10 13:29:09,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000011ABd00004362sv000011ABsd00005321bc02sc00i00')
2012-08-10 13:29:09,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2012-08-10 13:29:09,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:09,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000007Bsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:09,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip02')
2012-08-10 13:29:10,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:10,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-08-10 13:29:10,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 13:29:10,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc01ip00')
2012-08-10 13:29:10,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-08-10 13:29:10,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000054sv00001043sd00008162bc01sc01i85')
2012-08-10 13:29:10,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2012-08-10 13:29:10,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd000000B4sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000005Bsv00001043sd00008162bc0Csc03i20')
2012-08-10 13:29:10,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0003v0925p1234e0100-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,ra0,1,2,3,6,7,8,9,10,11,12,13,m4,lsfw')
2012-08-10 13:29:10,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:10,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:10,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:10,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:10,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 13:29:10,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:10,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0700:')
2012-08-10 13:29:10,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000006Fsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 13:29:10,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-10 13:29:10,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip01')
2012-08-10 13:29:10,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 13:29:10,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-08-10 13:29:10,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-08-10 13:29:10,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:10,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:10,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-08-10 13:29:10,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc02ip00')
2012-08-10 13:29:10,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v00001814d00000701sv00001814sd00002760bc02sc80i00')
2012-08-10 13:29:10,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2012-08-10 13:29:10,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000005Esv00001043sd00008162bc05sc80i00')
2012-08-10 13:29:10,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000076sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000007Dsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-10 13:29:10,078 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-08-10 13:29:10,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,078 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-08-10 13:29:10,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd00000057sv00001043sd000081D3bc06sc80i00')
2012-08-10 13:29:10,084 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2012-08-10 13:29:10,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-10 13:29:10,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 13:29:10,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 13:29:10,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 13:29:10,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'pci:v000010DEd0000007Csv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25e90e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-08-10 13:29:10,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-08-10 13:29:10,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,2,4,11,k71,72,73,74,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,1FD,1FE,1FF,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2012-08-10 13:29:10,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-08-10 13:29:10,091 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000075sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'platform:pcspkr')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Asv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-08-10 13:29:10,092 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'platform:regulatory')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v0000104Cd00008023sv00001043sd0000808Bbc0Csc00i10')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000071sv00001043sd00008189bc06sc00i00')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000079sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNPB006:')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000055sv00001043sd00008162bc01sc01i85')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-10 13:29:10,093 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Fsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000078sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000050sv00001043sd00008162bc06sc01i00')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v00001095d00003132sv00001043sd0000819Fbc01sc80i00')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000053sv00001043sd00008162bc01sc01i8a')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:10,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v0925p1234d0288dc00dsc00dp00ic03isc00ip00')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v00001102d00007002sv00001102sd00000020bc09sc80i00')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000291sv000010DEsd00000321bc03sc00i00')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v0D8Cp0008e0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-08-10 13:29:10,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v00001102d00000002sv00001102sd00008022bc04sc01i00')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0405:bd08/17/2006:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N32-SLI-Deluxe:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000052sv00001043sd00008162bc0Csc05i00')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000011ABd00004362sv000011ABsd00005321bc02sc00i00')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Bsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip02')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc01ip00')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000054sv00001043sd00008162bc01sc01i85')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd000000B4sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Bsv00001043sd00008162bc0Csc03i20')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0003v0925p1234e0100-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,ra0,1,2,3,6,7,8,9,10,11,12,13,m4,lsfw')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0700:')
2012-08-10 13:29:10,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000006Fsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip01')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc02ip00')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v00001814d00000701sv00001814sd00002760bc02sc80i00')
2012-08-10 13:29:10,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Esv00001043sd00008162bc05sc80i00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000076sv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Dsv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd00000057sv00001043sd000081D3bc06sc80i00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Csv00001043sd00008189bc05sc00i00')
2012-08-10 13:29:10,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x295a7a0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-08-10 13:29:10,135 DEBUG: handler xorg:nvidia_173 previously unseen
2012-08-10 13:29:10,136 DEBUG: handler xorg:nvidia_173_updates previously unseen
2012-08-10 13:29:10,136 DEBUG: handler xorg:nvidia_current previously unseen
2012-08-10 13:29:10,136 DEBUG: handler xorg:nvidia_current_updates previously unseen
2012-08-10 13:29:10,136 DEBUG: writing back check cache /var/cache/jockey/check
2012-08-10 13:29:10,159 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:10,160 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 13:29:10,181 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:10,182 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 13:29:10,203 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:10,204 DEBUG: nvidia_current is not the alternative in use
2012-08-10 13:29:10,225 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:10,225 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 13:29:10,259 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 13:29:10,259 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:01,780 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0>
2012-08-10 14:10:06,879 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-08-10 14:10:07,129 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-08-10 14:10:07,129 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-08-10 14:10:07,212 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-08-10 14:10:07,221 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-08-10 14:10:07,227 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-08-10 14:10:07,228 DEBUG: fglrx.available: falling back to default
2012-08-10 14:10:07,340 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 14:10:07,346 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-10 14:10:07,355 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-08-10 14:10:07,356 DEBUG: fglrx.available: falling back to default
2012-08-10 14:10:07,402 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-08-10 14:10:07,403 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-08-10 14:10:07,418 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-08-10 14:10:07,427 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-08-10 14:10:07,430 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,461 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 14:10:07,461 DEBUG: NVIDIA accelerated graphics driver not available
2012-08-10 14:10:07,468 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-10 14:10:07,476 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-08-10 14:10:07,477 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,533 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-08-10 14:10:07,539 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 14:10:07,546 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-08-10 14:10:07,547 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,601 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 14:10:07,608 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-08-10 14:10:07,617 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-08-10 14:10:07,618 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,673 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-08-10 14:10:07,681 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-08-10 14:10:07,688 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-08-10 14:10:07,689 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,743 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-08-10 14:10:07,749 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-08-10 14:10:07,756 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-08-10 14:10:07,757 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:07,783 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 14:10:07,783 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-08-10 14:10:07,783 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-08-10 14:10:07,790 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-08-10 14:10:07,818 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-08-10 14:10:07,819 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-08-10 14:10:07,819 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-08-10 14:10:07,827 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-08-10 14:10:07,827 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-08-10 14:10:07,828 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-08-10 14:10:07,828 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-08-10 14:10:07,834 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-08-10 14:10:07,834 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-08-10 14:10:07,857 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-08-10 14:10:07,857 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-08-10 14:10:07,867 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-08-10 14:10:07,876 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-08-10 14:10:07,922 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-08-10 14:10:07,923 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-08-10 14:10:07,952 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-08-10 14:10:07,965 DEBUG: Software modem not available
2012-08-10 14:10:07,965 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-08-10 14:10:08,002 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-08-10 14:10:08,003 DEBUG: Firmware for DVB cards not available
2012-08-10 14:10:08,003 DEBUG: all custom handlers loaded
2012-08-10 14:10:08,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-08-10 14:10:08,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,2,4,11,k71,72,73,74,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,1FD,1FE,1FF,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2012-08-10 14:10:08,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:08,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:08,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:08,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-08-10 14:10:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-10 14:10:08,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000075sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:08,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'platform:pcspkr')
2012-08-10 14:10:08,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-08-10 14:10:08,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-08-10 14:10:08,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000007Asv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:08,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-10 14:10:08,716 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:08,716 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,717 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:08,717 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:08,857 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:08,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2012-08-10 14:10:08,859 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:08,859 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,859 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-08-10 14:10:08,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-08-10 14:10:08,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'platform:regulatory')
2012-08-10 14:10:08,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v0000104Cd00008023sv00001043sd0000808Bbc0Csc00i10')
2012-08-10 14:10:08,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-08-10 14:10:08,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-10 14:10:08,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000071sv00001043sd00008189bc06sc00i00')
2012-08-10 14:10:08,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000079sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:08,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNPB006:')
2012-08-10 14:10:08,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000055sv00001043sd00008162bc01sc01i85')
2012-08-10 14:10:08,899 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2012-08-10 14:10:08,900 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-10 14:10:08,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000007Fsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:08,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000078sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:08,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-10 14:10:08,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01')
2012-08-10 14:10:08,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000050sv00001043sd00008162bc06sc01i00')
2012-08-10 14:10:08,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v00001095d00003132sv00001043sd0000819Fbc01sc80i00')
2012-08-10 14:10:08,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_sil24'}
2012-08-10 14:10:08,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_sil24', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000053sv00001043sd00008162bc01sc01i8a')
2012-08-10 14:10:08,952 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2012-08-10 14:10:08,952 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:08,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:08,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v0925p1234d0288dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:08,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:08,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v00001102d00007002sv00001102sd00000020bc09sc80i00')
2012-08-10 14:10:08,963 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'emu10k1_gp'}
2012-08-10 14:10:08,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'emu10k1_gp', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-08-10 14:10:08,964 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:08,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,964 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:08,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,964 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:08,965 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-08-10 14:10:08,965 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:08,965 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,965 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:08,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,966 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2012-08-10 14:10:08,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:08,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:08,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-10 14:10:08,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000291sv000010DEsd00000321bc03sc00i00')
2012-08-10 14:10:08,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-08-10 14:10:08,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-08-10 14:10:08,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:08,977 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-08-10 14:10:08,998 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:08,998 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:10:08,977 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,004 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-10 14:10:09,013 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,069 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,069 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:10:09,046 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,070 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2012-08-10 14:10:09,096 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,096 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:10:09,070 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,102 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-08-10 14:10:09,109 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,165 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,165 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:10:09,142 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2012-08-10 14:10:09,189 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,190 DEBUG: nvidia_96_updates is not the alternative in use
2012-08-10 14:10:09,166 DEBUG: found match in handler pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,197 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-08-10 14:10:09,205 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,228 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 14:10:09,253 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,254 DEBUG: nvidia_96_updates is not the alternative in use
2012-08-10 14:10:09,229 DEBUG: ignoring unavailable handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,254 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96', 'package': 'nvidia-96'}
2012-08-10 14:10:09,275 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,275 DEBUG: nvidia_96 is not the alternative in use
2012-08-10 14:10:09,254 DEBUG: found match in handler pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,281 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-08-10 14:10:09,289 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,316 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-08-10 14:10:09,342 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,342 DEBUG: nvidia_96 is not the alternative in use
2012-08-10 14:10:09,317 DEBUG: ignoring unavailable handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,342 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2012-08-10 14:10:09,364 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,365 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:09,342 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,373 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-08-10 14:10:09,381 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,440 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,440 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:09,410 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-08-10 14:10:09,441 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-08-10 14:10:09,472 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,473 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:10:09,441 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,481 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 14:10:09,491 DEBUG: nvidia.available: falling back to default
2012-08-10 14:10:09,551 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:09,551 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:10:09,521 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-08-10 14:10:09,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v0D8Cp0008e0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-08-10 14:10:09,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:09,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:09,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-10 14:10:09,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v00001102d00000002sv00001102sd00008022bc04sc01i00')
2012-08-10 14:10:09,553 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_emu10k1'}
2012-08-10 14:10:09,553 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_emu10k1', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0405:bd08/17/2006:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N32-SLI-Deluxe:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-08-10 14:10:09,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000052sv00001043sd00008162bc0Csc05i00')
2012-08-10 14:10:09,593 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2012-08-10 14:10:09,593 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-10 14:10:09,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000011ABd00004362sv000011ABsd00005321bc02sc00i00')
2012-08-10 14:10:09,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2012-08-10 14:10:09,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000007Bsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip02')
2012-08-10 14:10:09,745 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:09,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,746 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-08-10 14:10:09,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 14:10:09,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc01ip00')
2012-08-10 14:10:09,748 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-08-10 14:10:09,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000054sv00001043sd00008162bc01sc01i85')
2012-08-10 14:10:09,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'}
2012-08-10 14:10:09,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd000000B4sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000005Bsv00001043sd00008162bc0Csc03i20')
2012-08-10 14:10:09,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0003v0925p1234e0100-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,ra0,1,2,3,6,7,8,9,10,11,12,13,m4,lsfw')
2012-08-10 14:10:09,780 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:09,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,781 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:09,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,781 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:09,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:09,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-10 14:10:09,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,783 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:09,783 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0700:')
2012-08-10 14:10:09,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000006Fsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 14:10:09,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-10 14:10:09,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip01')
2012-08-10 14:10:09,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-10 14:10:09,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,798 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-08-10 14:10:09,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-08-10 14:10:09,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:09,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,800 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:09,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-08-10 14:10:09,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc02ip00')
2012-08-10 14:10:09,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v00001814d00000701sv00001814sd00002760bc02sc80i00')
2012-08-10 14:10:09,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci'}
2012-08-10 14:10:09,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800pci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000005Esv00001043sd00008162bc05sc80i00')
2012-08-10 14:10:09,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000076sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000007Dsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-10 14:10:09,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-08-10 14:10:09,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-08-10 14:10:09,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd00000057sv00001043sd000081D3bc06sc80i00')
2012-08-10 14:10:09,892 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2012-08-10 14:10:09,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-10 14:10:09,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-10 14:10:09,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-10 14:10:09,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-10 14:10:09,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'pci:v000010DEd0000007Csv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1d1b0e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-08-10 14:10:09,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0501:')
2012-08-10 14:10:09,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,2,4,11,k71,72,73,74,8C,8E,8F,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,D9,100,101,102,103,104,105,106,107,108,109,10A,10B,10C,10D,10E,10F,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,133,134,135,136,137,138,139,13A,13B,13C,13D,13E,13F,140,141,142,143,144,145,146,147,148,149,14A,14B,14C,14D,14E,14F,150,151,152,153,154,155,156,157,158,159,15A,15B,15C,15D,15E,15F,160,161,162,163,164,165,166,167,168,169,16A,16B,16C,16D,16E,16F,170,171,172,173,174,175,176,177,178,179,17A,17B,17C,17D,17E,17F,180,181,182,183,184,185,186,187,188,189,18A,18B,18C,18D,18E,18F,190,191,192,193,194,195,196,197,198,199,19A,19B,19C,19D,19E,19F,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1AF,1B0,1B1,1B2,1B3,1B4,1B5,1B6,1B7,1B8,1B9,1BA,1BB,1BC,1BD,1BE,1BF,1C0,1C1,1C2,1C3,1C4,1C5,1C6,1C7,1C8,1C9,1CA,1CB,1CC,1CD,1CE,1CF,1D0,1D1,1D2,1D3,1D4,1D5,1D6,1D7,1D8,1D9,1DA,1DB,1DC,1DD,1DE,1DF,1E0,1E1,1E2,1E3,1E4,1E5,1E6,1E7,1E8,1E9,1EA,1EB,1EC,1ED,1EE,1EF,1F0,1F1,1F2,1F3,1F4,1F5,1F6,1F7,1F8,1F9,1FA,1FB,1FC,1FD,1FE,1FF,r0,1,8,am4,l8,9,A,B,C,D,E,sfw')
2012-08-10 14:10:09,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-08-10 14:10:09,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-10 14:10:09,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000075sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'platform:pcspkr')
2012-08-10 14:10:09,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Asv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-10 14:10:09,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:09,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2012-08-10 14:10:09,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0800:')
2012-08-10 14:10:09,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'platform:regulatory')
2012-08-10 14:10:09,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v0000104Cd00008023sv00001043sd0000808Bbc0Csc00i10')
2012-08-10 14:10:09,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-10 14:10:09,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000071sv00001043sd00008189bc06sc00i00')
2012-08-10 14:10:09,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000079sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNPB006:')
2012-08-10 14:10:09,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000055sv00001043sd00008162bc01sc01i85')
2012-08-10 14:10:09,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-10 14:10:09,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Fsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000078sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,909 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-10 14:10:09,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01')
2012-08-10 14:10:09,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000050sv00001043sd00008162bc06sc01i00')
2012-08-10 14:10:09,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v00001095d00003132sv00001043sd0000819Fbc01sc80i00')
2012-08-10 14:10:09,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000053sv00001043sd00008162bc01sc01i8a')
2012-08-10 14:10:09,910 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:09,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v0925p1234d0288dc00dsc00dp00ic03isc00ip00')
2012-08-10 14:10:09,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v00001102d00007002sv00001102sd00000020bc09sc80i00')
2012-08-10 14:10:09,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-08-10 14:10:09,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-08-10 14:10:09,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v046DpC50Be0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,8,9,A,B,C,D,E,sfw')
2012-08-10 14:10:09,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-10 14:10:09,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000291sv000010DEsd00000321bc03sc00i00')
2012-08-10 14:10:09,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v0D8Cp0008e0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-08-10 14:10:09,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-10 14:10:09,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v00001102d00000002sv00001102sd00008022bc04sc01i00')
2012-08-10 14:10:09,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0405:bd08/17/2006:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5N32-SLI-Deluxe:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-08-10 14:10:09,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000052sv00001043sd00008162bc0Csc05i00')
2012-08-10 14:10:09,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-10 14:10:09,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000011ABd00004362sv000011ABsd00005321bc02sc00i00')
2012-08-10 14:10:09,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Bsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip02')
2012-08-10 14:10:09,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 14:10:09,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc01ip00')
2012-08-10 14:10:09,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000054sv00001043sd00008162bc01sc01i85')
2012-08-10 14:10:09,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd000000B4sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Bsv00001043sd00008162bc0Csc03i20')
2012-08-10 14:10:09,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0003v0925p1234e0100-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,ra0,1,2,3,6,7,8,9,10,11,12,13,m4,lsfw')
2012-08-10 14:10:09,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0700:')
2012-08-10 14:10:09,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000006Fsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v046DpC50Bd2100dc00dsc00dp00ic03isc01ip01')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-08-10 14:10:09,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'usb:v0D8Cp0008d0100dc00dsc00dp00ic01isc02ip00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v00001814d00000701sv00001814sd00002760bc02sc80i00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000005Esv00001043sd00008162bc05sc80i00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000076sv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Dsv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-10 14:10:09,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd00000057sv00001043sd000081D3bc06sc80i00')
2012-08-10 14:10:09,918 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-10 14:10:09,918 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'pci:v000010DEd0000007Csv00001043sd00008189bc05sc00i00')
2012-08-10 14:10:09,918 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208c7a0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-08-10 14:10:10,001 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:10,001 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:13,953 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:13,953 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:10:17,921 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:17,921 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:10:21,614 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:21,614 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:10:25,581 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:25,582 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:25,662 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:25,662 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:10:25,720 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:25,721 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:10:25,780 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:25,780 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:10:25,836 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:25,837 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:10:55,384 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:10:55,385 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:11,670 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:11,670 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:29,008 DEBUG: Installing package: nvidia-current
2012-08-10 14:11:30,155 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2012-08-10 14:11:30,408 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-10 14:11:30,409 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-08-10 14:11:30,422 ERROR: xorg:nvidia_current: get_alternative_by_name(nvidia-current) returned nothing
2012-08-10 14:11:30,515 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:30,516 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:38,852 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:38,852 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:11:38,915 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:38,916 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:11:38,973 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:38,973 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:39,031 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,031 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:11:39,098 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,098 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:39,172 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,172 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:11:39,226 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,227 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:11:39,281 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,281 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:11:39,335 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:39,336 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:11:46,734 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:11:46,734 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:12:04,359 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:04,359 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:12:04,717 DEBUG: Installing package: nvidia-current-updates
2012-08-10 14:12:05,867 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2012-08-10 14:12:06,128 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 14:12:06,129 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-08-10 14:12:06,142 ERROR: xorg:nvidia_current_updates: get_alternative_by_name(nvidia-current-updates) returned nothing
2012-08-10 14:12:06,221 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:06,221 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:12:08,425 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,425 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:12:08,488 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,488 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:12:08,552 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,553 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:12:08,623 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,623 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:12:08,695 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,696 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:12:08,775 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,775 DEBUG: nvidia_173 is not the alternative in use
2012-08-10 14:12:08,835 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,836 DEBUG: nvidia_173_updates is not the alternative in use
2012-08-10 14:12:08,896 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,896 DEBUG: nvidia_current is not the alternative in use
2012-08-10 14:12:08,956 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:12:08,956 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:24:15,465 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:24:15,466 DEBUG: nvidia_current_updates is not the alternative in use
2012-08-10 14:24:24,697 DEBUG: Installing package: nvidia-current-updates
2012-08-10 14:24:26,176 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2012-08-10 14:24:26,505 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-10 14:24:26,506 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-08-10 14:24:26,522 ERROR: xorg:nvidia_current_updates: get_alternative_by_name(nvidia-current-updates) returned nothing
2012-08-10 14:24:26,666 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-08-10 14:24:26,666 DEBUG: nvidia_current_updates is not the alternative in use
```

---

### Post by Frogs Hair on 2012-08-10
Have you run the update manager since upgrading ? I ask because the kernel version in the output appears to be version that came with 12.04 when it was first released and there have been updates since.

---

### Post by gandalf3 on 2012-08-10
yes, sure enough you were right, i needed to update (i thought it installed all the updates with installation.. oops.)
Thanks!

---

