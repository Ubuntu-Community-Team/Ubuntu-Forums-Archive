---
title: "Installing Ubuntu GPU Drivers?"
date: 2012-01-03
forum: General Help
---

### Post by D@rekills4 on 2012-01-03
Okay, so I installed Ubuntu 11.10 x86 for development purposes and everything seems good and am quite enjoying this.
I am also a gamer at the same time and had a thought in my mind if I could run World of Warcraft on Ubuntu.
I googled it up and found it.
I did all the settings and was able to run World of Warcraft successfully.
Well, except for the lag.

I pretty much think that the lag was caused by the lack of GPU Drivers.....
So I found how to install the GPU Drivers (I have a ATI 3300 HD) but it didn't quite turn out right......

[img]http://ubuntuforums.org/attachment.php?attachmentid=210188&stc=1&thumb=1&d=1325610708[/img]

When I install the second option it installs successfully and tells me to restart.
I do so but sadly the drivers are not working cause there is still lag when I move my Windows or Icons on the desktop.
And after I restart again the drivers are no longer active, I have the option to install again :(


When I install the first option I get an error saying :


[img]http://ubuntuforums.org/attachment.php?attachmentid=210189&stc=1&thumb=1&d=1325610776[/img]



Requesting help.

---

### Post by Mark Phelps on 2012-01-03
We can't help without some details ... so,you need to use Nautilus to open the log filed named in the screenshot and look at the last few lines in the file. That should tell you why the driver install failed.

---

### Post by D@rekills4 on 2012-01-03
> **Mark Phelps said:**
> We can't help without some details ... so,you need to use Nautilus to open the log filed named in the screenshot and look at the last few lines in the file. That should tell you why the driver install failed.



I deleted the contents of "jockey.log" file and then selected the second option from the screenshot I have posted in the first post.
And then here is the log after the error I got.



```
2012-01-03 22:47:41,472 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c>
2012-01-03 22:47:43,460 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2012-01-03 22:47:43,580 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-03 22:47:43,580 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-03 22:47:43,621 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-03 22:47:43,656 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-03 22:47:43,663 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-03 22:47:43,664 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-03 22:47:43,664 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-03 22:47:43,665 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-03 22:47:43,671 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-03 22:47:43,708 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-03 22:47:43,708 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-03 22:47:43,709 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-03 22:47:43,727 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-03 22:47:43,727 DEBUG: fglrx.available: falling back to default
2012-01-03 22:47:43,860 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-03 22:47:43,866 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-03 22:47:43,873 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-03 22:47:43,873 DEBUG: fglrx.available: falling back to default
2012-01-03 22:47:43,955 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-03 22:47:43,955 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-03 22:47:43,966 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-03 22:47:43,974 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-03 22:47:43,974 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,048 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-03 22:47:44,054 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-03 22:47:44,061 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-03 22:47:44,061 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,134 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-03 22:47:44,140 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-03 22:47:44,147 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-03 22:47:44,147 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,222 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-03 22:47:44,222 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-03 22:47:44,229 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-03 22:47:44,236 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-03 22:47:44,236 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,310 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-03 22:47:44,315 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-03 22:47:44,322 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-03 22:47:44,323 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,397 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-03 22:47:44,403 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-03 22:47:44,410 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-03 22:47:44,410 DEBUG: nvidia.available: falling back to default
2012-01-03 22:47:44,483 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-03 22:47:44,484 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-03 22:47:44,523 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-03 22:47:44,536 DEBUG: Software modem not available
2012-01-03 22:47:44,536 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-03 22:47:44,580 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-03 22:47:44,581 DEBUG: Firmware for DVB cards not available
2012-01-03 22:47:44,581 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-03 22:47:44,588 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-03 22:47:44,589 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-03 22:47:44,625 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-03 22:47:44,625 DEBUG: all custom handlers loaded
2012-01-03 22:47:44,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00009614sv00001458sd0000D000bc03sc00i00')
2012-01-03 22:47:45,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-03 22:47:45,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,093 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-01-03 22:47:45,133 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,134 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:45,093 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-03 22:47:45,141 DEBUG: fglrx.available: falling back to default
2012-01-03 22:47:45,225 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,226 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:45,183 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-03 22:47:45,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-03 22:47:45,266 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,267 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:45,226 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-03 22:47:45,274 DEBUG: fglrx.available: falling back to default
2012-01-03 22:47:45,356 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,356 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:45,315 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-03 22:47:45,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-03 22:47:45,397 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,398 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:45,357 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-03 22:47:45,403 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-03 22:47:45,410 DEBUG: fglrx.available: falling back to default
2012-01-03 22:47:45,490 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,490 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:45,452 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-03 22:47:45,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-03 22:47:45,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-03 22:47:45,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-03 22:47:45,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d0000960Fsv00001458sd0000960Fbc04sc03i00')
2012-01-03 22:47:45,523 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-03 22:47:45,523 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,523 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-03 22:47:45,523 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'platform:eisa')
2012-01-03 22:47:45,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-03 22:47:45,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-03 22:47:45,553 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-03 22:47:45,553 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-03 22:47:45,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-03 22:47:45,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-03 22:47:45,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'platform:pcspkr')
2012-01-03 22:47:45,559 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-03 22:47:45,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-03 22:47:45,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-01-03 22:47:45,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00009600sv00001022sd00009600bc06sc00i00')
2012-01-03 22:47:45,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-03 22:47:45,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-01-03 22:47:45,561 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-01-03 22:47:45,561 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0700:')
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-03 22:47:45,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-03 22:47:45,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic0Aisc00ip00')
2012-01-03 22:47:45,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-01-03 22:47:45,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-03 22:47:45,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-03 22:47:45,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-01-03 22:47:45,580 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-03 22:47:45,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00icFFisc42ip01')
2012-01-03 22:47:45,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-01-03 22:47:45,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-01-03 22:47:45,589 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-03 22:47:45,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,590 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-03 22:47:45,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF1:bd07/18/2008:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790GP-DS4H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790GP-DS4H:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-01-03 22:47:45,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-03 22:47:45,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2012-01-03 22:47:45,638 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-01-03 22:47:45,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,638 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-01-03 22:47:45,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-03 22:47:45,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-03 22:47:45,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-03 22:47:45,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic08isc06ip50')
2012-01-03 22:47:45,640 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-01-03 22:47:45,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,640 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2012-01-03 22:47:45,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-01-03 22:47:45,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-01-03 22:47:45,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-01-03 22:47:45,664 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-01-03 22:47:45,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-01-03 22:47:45,668 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-01-03 22:47:45,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-03 22:47:45,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-01-03 22:47:45,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-03 22:47:45,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-03 22:47:45,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic02isc02ip01')
2012-01-03 22:47:45,670 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cdc_acm'}
2012-01-03 22:47:45,670 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cdc_acm', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2012-01-03 22:47:45,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-03 22:47:45,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-03 22:47:45,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-03 22:47:45,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-03 22:47:45,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2012-01-03 22:47:45,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-03 22:47:45,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-03 22:47:45,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb77bf66c> about HardwareID('modalias', 'acpi:PNP0400:')
2012-01-03 22:47:45,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00009614sv00001458sd0000D000bc03sc00i00')
2012-01-03 22:47:45,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d0000960Fsv00001458sd0000960Fbc04sc03i00')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'platform:eisa')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'platform:pcspkr')
2012-01-03 22:47:45,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00009600sv00001022sd00009600bc06sc00i00')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0700:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic0Aisc00ip00')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00icFFisc42ip01')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF1:bd07/18/2008:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790GP-DS4H:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790GP-DS4H:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic08isc06ip50')
2012-01-03 22:47:45,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'usb:v04E8p681Cd0400dc02dsc00dp00ic02isc02ip01')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A102bc04sc03i00')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2012-01-03 22:47:45,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb75c5e0c> about HardwareID('modalias', 'acpi:PNP0400:')
2012-01-03 22:47:45,756 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,756 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:45,816 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,816 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:45,963 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:45,963 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:46,036 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:46,037 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:46,094 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:46,094 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:48,150 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:48,150 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:48,822 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:48,822 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:51,682 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:51,682 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:52,057 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-01-03 22:47:52,152 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-01-03 22:47:52,235 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:52,236 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:52,276 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:52,277 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:54,600 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,600 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:54,642 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,642 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:54,703 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,704 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-03 22:47:54,860 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,861 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:54,902 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,902 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:54,976 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:54,977 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:55,018 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:55,018 DEBUG: fglrx_updates is not the alternative in use
2012-01-03 22:47:55,075 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-03 22:47:55,076 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```

---

### Post by D@rekills4 on 2012-01-03
Bump..........

---

### Post by D@rekills4 on 2012-01-03
Great....
I installed the drivers manually and I am now stuck after tthe boot screen....
See attached image below....


[IMG]http://i.lulzimg.com/c964423b5e.jpg[/IMG]

---

