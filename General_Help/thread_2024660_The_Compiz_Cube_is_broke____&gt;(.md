---
title: "The Compiz Cube is broke    &gt;:("
date: 2012-07-13
forum: General Help
---

### Post by Petro Dawg on 2012-07-13
Some time ago (weeks) I installed CompizConfig and enabled the compiz cube and rotate.  It was buggy especially with known "Screen Flash" bug which prevented moving windows between different sides of the cube.  I fixed the bugs by running the following code:

```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
sudo apt-get update
sudo apt-get upgrade
```All was well and everything ran perfectly, then today I was stupid enough to run the "Additional Drivers" utility to install AMD drivers for my integrated graphics.  It failed to install the drivers the first time; I restarted and tried installing again.  The second time the drivers installed and activated, but now all the bug fixes for the cube are lost and the cube is basically unusable, and even the Compiz "Desktop Wall" feature is a little buggy.  

I tried simply running the above code again, but it now fails to fix the problems it solved before.  So, anyone have any ideas on how to go about fixing my compiz issues.

---

### Post by wildmanne39 on 2012-07-13
Hi, I recommend removing the driver you installed and using the one that you used when compiz worked right, drivers play the biggest role in compiz usability and the speed of ubuntu.
Thanks

---

### Post by Petro Dawg on 2012-07-14
thanks for the reply, 

I wanted the driver so I could play Nexiuz on something other than minimum graphics, now I can use that program at nearly full graphics settings.  Also, when switching from full screen mode on some applications my screen resolution would not change back to my preset standard size, the new drivers fixed that problem too.  

So the drivers fixed some problems, but broke the cube.  Its kinda sad I have to choose between which bugs I want to live with.  Right now, I'll lose the cube unless someone has an idea on how to fix it.  The cube is cool looking, but I will choose function over beauty if need be.

Also, the cube broke after the first failed attempt at installing the AMD drivers.  So at that point, there was no new driver installed. It seems the installation process broke the cube (or, more correctly, the cube bug fixes), not the driver itself (if that makes any sense) . I do not believe uninstalling the driver will get it working again, as it now works exactly the same buggy way it worked with the original drivers before I originally installed the ppa repository fixes.

What I would like to do is successfully uninstall and reinstall the files originally installed through the code I mentioned in my first post.  But when I simply try to run the same three lines again, after I run the "apt-get upgrade" line, I get the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```I don't think anything is getting reinstalled.  Anyone have any ideas on how to do this???

---

### Post by mc4man on 2012-07-14
compiz in 12.04 upgraded to a version higher than the ppa so you likely are now using that compiz which does not yet include the 'flashing' fix
You can either wait for the eventual official fix, maybe the ppa will do a new build  or you'll need to downgrade back to the ppa package set which is a min. of 6 packages

---

### Post by Petro Dawg on 2012-07-14
> **mc4man said:**
> compiz in 12.04 upgraded to a version higher than the ppa so you likely are now using that compiz which does not yet include the 'flashing' fix
You can either wait for the eventual official fix, maybe the ppa will do a new build  or you'll need to downgrade back to the ppa package set which is a min. of 6 packages

Unfortunately my Ubuntu/terminal skills are still lacking as I am new to this OS.  I'm not sure how to downgrade to the ppa package set.

The ppa set however did work in fixing the bug for a long time in 12.04, it just stopped working suddenly when my first attempt to install drivers for my graphics failed.  I have the failed attempt error log, if anyone is interested in looking at it.  The log code doesn't mean a whole lot to me and it is extremely long.

Last night was a long one for me as I tried unistalling CCSM which also unistalled unity.  It took a while but finally figured out how to reinstall unity and CCSM.  I then enabled the unity plugin in CCSM and then did an update/upgrade and I'm still left with what I started with; "blinking" screens when switching workspaces.

---

### Post by Petro Dawg on 2012-07-14
This is the root/var/log/jockey.log which was generated when my driver installation failed and cube stopped working.

```
2012-07-13 21:13:20,052 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c>
2012-07-13 21:13:22,214 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic-pae/modules.alias
2012-07-13 21:13:22,347 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-13 21:13:22,351 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-13 21:13:22,433 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-13 21:13:22,506 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-13 21:13:22,516 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-13 21:13:22,516 DEBUG: fglrx.available: falling back to default
2012-07-13 21:13:22,646 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:13:22,653 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-13 21:13:22,662 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-13 21:13:22,663 DEBUG: fglrx.available: falling back to default
2012-07-13 21:13:22,734 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-13 21:13:22,735 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-13 21:13:22,742 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-13 21:13:22,742 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-13 21:13:22,783 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-13 21:13:22,784 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-13 21:13:22,806 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-13 21:13:22,816 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-13 21:13:22,819 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:22,856 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:13:22,857 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:13:22,866 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-13 21:13:22,875 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-13 21:13:22,876 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:22,939 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-13 21:13:22,944 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-13 21:13:22,950 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-13 21:13:22,951 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:23,005 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:13:23,008 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-13 21:13:23,013 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-13 21:13:23,014 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:23,032 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:13:23,032 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:13:23,037 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-13 21:13:23,042 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-13 21:13:23,042 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:23,060 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:13:23,060 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:13:23,064 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-13 21:13:23,069 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-13 21:13:23,070 DEBUG: nvidia.available: falling back to default
2012-07-13 21:13:23,088 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:13:23,089 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:13:23,089 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-13 21:13:23,095 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-13 21:13:23,095 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-13 21:13:23,095 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-13 21:13:23,096 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-13 21:13:23,119 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-13 21:13:23,145 DEBUG: Software modem not available
2012-07-13 21:13:23,146 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-13 21:13:23,211 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-13 21:13:23,212 DEBUG: Firmware for DVB cards not available
2012-07-13 21:13:23,212 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-13 21:13:23,225 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-13 21:13:23,234 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-13 21:13:23,301 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-13 21:13:23,302 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-13 21:13:23,315 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-13 21:13:23,335 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-13 21:13:23,336 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-13 21:13:23,336 DEBUG: all custom handlers loaded
2012-07-13 21:13:23,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:13:23,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-13 21:13:23,751 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:23,751 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:23,691 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:13:23,758 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-13 21:13:23,768 DEBUG: fglrx.available: falling back to default
2012-07-13 21:13:23,823 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:23,824 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:23,802 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:13:23,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-13 21:13:23,846 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:23,846 DEBUG: fglrx is not the alternative in use
2012-07-13 21:13:23,825 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:13:23,851 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-13 21:13:23,861 DEBUG: fglrx.available: falling back to default
2012-07-13 21:13:23,920 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:23,921 DEBUG: fglrx is not the alternative in use
2012-07-13 21:13:23,894 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:13:23,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-13 21:13:24,027 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:13:24,032 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:13:24,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:13:24,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:13:24,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-07-13 21:13:24,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:13:24,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-13 21:13:24,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-13 21:13:24,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:13:24,062 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,062 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:13:24,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:13:24,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-13 21:13:24,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:13:24,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:13:24,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:13:24,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:13:24,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-13 21:13:24,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-13 21:13:24,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:13:24,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:13:24,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:13:24,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:13:24,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:13:24,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-07-13 21:13:24,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:13:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:13:24,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-13 21:13:24,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:13:24,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:13:24,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:13:24,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:13:24,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:13:24,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:13:24,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:13:24,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:13:24,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:13:24,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:13:24,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:13:24,175 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-13 21:13:24,176 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,176 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-13 21:13:24,176 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:13:24,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:13:24,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:13:24,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:13:24,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:13:24,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-07-13 21:13:24,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:13:24,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:13:24,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:13:24,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:13:24,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:13:24,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:13:24,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:13:24,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:13:24,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-13 21:13:24,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-13 21:13:24,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:13:24,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:13:24,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:13:24,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:13:24,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:13:24,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:13:24,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb718dd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:13:24,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:13:24,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:13:24,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:13:24,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688982c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:13:24,319 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:24,320 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:24,422 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:24,422 DEBUG: fglrx is not the alternative in use
2012-07-13 21:13:24,464 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:24,464 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:24,532 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:24,532 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:24,583 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:24,583 DEBUG: fglrx is not the alternative in use
2012-07-13 21:13:44,068 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-13 21:13:44,068 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:13:47,292 DEBUG: Installing package: fglrx-updates
2012-07-13 21:13:47,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-13 21:13:47,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-13 21:13:47,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-13 21:13:48,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-07-13 21:13:48,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.002413
2012-07-13 21:13:48,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.104466
2012-07-13 21:13:49,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.189745
2012-07-13 21:13:49,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.189745
2012-07-13 21:13:49,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.189745
2012-07-13 21:13:49,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.298621
2012-07-13 21:13:50,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.332638
2012-07-13 21:13:50,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.350916
2012-07-13 21:13:50,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.365981
2012-07-13 21:13:50,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.544869
2012-07-13 21:13:50,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.547754
2012-07-13 21:13:51,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.655993
2012-07-13 21:13:51,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.761138
2012-07-13 21:13:52,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.798249
2012-07-13 21:13:52,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.974523
2012-07-13 21:13:53,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.073484
2012-07-13 21:13:53,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.187907
2012-07-13 21:13:54,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.293053
2012-07-13 21:13:54,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.401291
2012-07-13 21:13:55,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.509530
2012-07-13 21:13:55,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.611583
2012-07-13 21:13:56,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.716729
2012-07-13 21:13:56,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.828060
2012-07-13 21:13:57,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.936298
2012-07-13 21:13:57,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.957946
2012-07-13 21:13:58,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.152775
2012-07-13 21:13:58,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.248643
2012-07-13 21:13:59,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.335234
2012-07-13 21:13:59,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.462028
2012-07-13 21:14:00,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.551711
2012-07-13 21:14:00,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.675412
2012-07-13 21:14:01,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.777465
2012-07-13 21:14:01,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.891889
2012-07-13 21:14:02,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.997034
2012-07-13 21:14:02,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.102180
2012-07-13 21:14:03,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.216604
2012-07-13 21:14:03,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.312472
2012-07-13 21:14:04,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.420710
2012-07-13 21:14:04,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.420710
2012-07-13 21:14:05,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.618632
2012-07-13 21:14:05,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.708315
2012-07-13 21:14:06,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.788721
2012-07-13 21:14:06,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.878404
2012-07-13 21:14:07,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.971180
2012-07-13 21:14:07,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.063956
2012-07-13 21:14:08,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.159824
2012-07-13 21:14:08,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.271155
2012-07-13 21:14:09,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.404134
2012-07-13 21:14:09,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.534020
2012-07-13 21:14:10,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.608240
2012-07-13 21:14:10,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.697923
2012-07-13 21:14:11,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.852550
2012-07-13 21:14:11,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.960788
2012-07-13 21:14:12,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.010269
2012-07-13 21:14:12,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.112322
2012-07-13 21:14:13,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.282411
2012-07-13 21:14:13,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.390649
2012-07-13 21:14:14,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.495795
2012-07-13 21:14:14,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.600941
2012-07-13 21:14:15,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.709179
2012-07-13 21:14:15,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.814325
2012-07-13 21:14:16,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.925656
2012-07-13 21:14:16,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.978229
2012-07-13 21:14:17,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.132855
2012-07-13 21:14:17,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.244186
2012-07-13 21:14:18,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.352425
2012-07-13 21:14:18,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.457570
2012-07-13 21:14:19,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.565809
2012-07-13 21:14:19,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.670955
2012-07-13 21:14:20,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.776101
2012-07-13 21:14:20,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.887432
2012-07-13 21:14:21,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.995670
2012-07-13 21:14:21,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.063705
2012-07-13 21:14:22,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.184314
2012-07-13 21:14:22,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.304922
2012-07-13 21:14:23,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.403883
2012-07-13 21:14:23,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.505937
2012-07-13 21:14:24,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.617268
2012-07-13 21:14:24,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.688396
2012-07-13 21:14:25,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.805912
2012-07-13 21:14:25,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.914150
2012-07-13 21:14:26,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.022388
2012-07-13 21:14:26,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.127534
2012-07-13 21:14:27,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.238865
2012-07-13 21:14:27,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.344011
2012-07-13 21:14:28,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.452249
2012-07-13 21:14:28,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.557395
2012-07-13 21:14:29,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.643986
2012-07-13 21:14:29,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.770780
2012-07-13 21:14:30,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.879018
2012-07-13 21:14:30,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.984164
2012-07-13 21:14:31,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.089310
2012-07-13 21:14:31,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.197548
2012-07-13 21:14:32,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.302694
2012-07-13 21:14:32,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.414025
2012-07-13 21:14:33,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.516078
2012-07-13 21:14:33,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.624317
2012-07-13 21:14:34,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.732555
2012-07-13 21:14:34,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.840793
2012-07-13 21:14:35,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.945939
2012-07-13 21:14:35,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.054178
2012-07-13 21:14:36,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.159324
2012-07-13 21:14:36,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.261377
2012-07-13 21:14:37,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.375800
2012-07-13 21:14:37,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.480946
2012-07-13 21:14:38,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.579907
2012-07-13 21:14:38,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.694330
2012-07-13 21:14:39,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.722163
2012-07-13 21:14:39,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.898437
2012-07-13 21:14:40,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.009768
2012-07-13 21:14:40,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.114914
2012-07-13 21:14:41,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.142747
2012-07-13 21:14:41,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.254078
2012-07-13 21:14:42,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.427259
2012-07-13 21:14:42,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.544775
2012-07-13 21:14:43,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.653013
2012-07-13 21:14:43,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.758159
2012-07-13 21:14:44,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.857120
2012-07-13 21:14:44,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.974636
2012-07-13 21:14:45,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.082874
2012-07-13 21:14:45,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.188020
2012-07-13 21:14:46,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.293166
2012-07-13 21:14:46,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.358109
2012-07-13 21:14:47,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.487995
2012-07-13 21:14:47,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.593141
2012-07-13 21:14:48,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.716842
2012-07-13 21:14:48,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.825081
2012-07-13 21:14:49,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.933319
2012-07-13 21:14:49,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.035372
2012-07-13 21:14:50,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.146703
2012-07-13 21:14:50,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.254942
2012-07-13 21:14:51,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.360087
2012-07-13 21:14:51,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.465233
2012-07-13 21:14:52,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.573472
2012-07-13 21:14:52,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.672433
2012-07-13 21:14:53,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.678618
2012-07-13 21:14:53,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.888909
2012-07-13 21:14:54,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.960037
2012-07-13 21:14:54,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.099201
2012-07-13 21:14:55,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.201254
2012-07-13 21:14:55,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.300215
2012-07-13 21:14:56,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.411546
2012-07-13 21:14:56,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.519784
2012-07-13 21:14:57,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.640393
2012-07-13 21:14:57,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.692966
2012-07-13 21:14:58,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.853777
2012-07-13 21:14:59,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.955831
2012-07-13 21:14:59,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.064069
2012-07-13 21:15:00,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.091902
2012-07-13 21:15:00,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.274361
2012-07-13 21:15:01,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.385692
2012-07-13 21:15:01,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.484652
2012-07-13 21:15:02,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.583613
2012-07-13 21:15:02,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.707314
2012-07-13 21:15:03,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.809368
2012-07-13 21:15:03,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.914514
2012-07-13 21:15:04,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.010382
2012-07-13 21:15:04,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.103158
2012-07-13 21:15:05,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.236136
2012-07-13 21:15:05,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.335097
2012-07-13 21:15:06,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.437327
2012-07-13 21:15:06,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.554666
2012-07-13 21:15:07,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.662905
2012-07-13 21:15:07,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.724755
2012-07-13 21:15:08,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.867011
2012-07-13 21:15:08,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.975250
2012-07-13 21:15:09,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.083488
2012-07-13 21:15:09,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.188634
2012-07-13 21:15:10,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.238114
2012-07-13 21:15:10,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.402018
2012-07-13 21:15:11,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.442221
2012-07-13 21:15:11,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.606125
2012-07-13 21:15:12,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.708178
2012-07-13 21:15:12,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.822602
2012-07-13 21:15:13,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.918470
2012-07-13 21:15:13,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.023616
2012-07-13 21:15:14,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.119484
2012-07-13 21:15:14,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.202982
2012-07-13 21:15:15,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.298851
2012-07-13 21:15:15,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.376164
2012-07-13 21:15:16,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.456569
2012-07-13 21:15:16,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.499865
2012-07-13 21:15:17,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.617381
2012-07-13 21:15:17,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.710157
2012-07-13 21:15:18,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.799840
2012-07-13 21:15:18,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.867875
2012-07-13 21:15:19,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.926633
2012-07-13 21:15:19,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.010132
2012-07-13 21:15:20,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.059612
2012-07-13 21:15:20,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.167850
2012-07-13 21:15:21,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.201868
2012-07-13 21:15:21,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.303921
2012-07-13 21:15:22,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.368865
2012-07-13 21:15:22,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.433808
2012-07-13 21:15:23,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.492566
2012-07-13 21:15:23,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.588434
2012-07-13 21:15:24,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.659562
2012-07-13 21:15:24,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.684302
2012-07-13 21:15:25,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.814188
2012-07-13 21:15:25,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.885316
2012-07-13 21:15:26,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.922427
2012-07-13 21:15:26,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.993555
2012-07-13 21:15:27,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.080145
2012-07-13 21:15:27,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.138903
2012-07-13 21:15:28,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.191476
2012-07-13 21:15:28,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.222402
2012-07-13 21:15:29,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.265697
2012-07-13 21:15:29,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.318270
2012-07-13 21:15:30,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.367750
2012-07-13 21:15:30,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.411046
2012-07-13 21:15:31,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.479081
2012-07-13 21:15:31,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.537839
2012-07-13 21:15:32,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.581135
2012-07-13 21:15:32,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.633707
2012-07-13 21:15:33,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.692465
2012-07-13 21:15:33,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.757408
2012-07-13 21:15:34,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.819259
2012-07-13 21:15:34,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.881109
2012-07-13 21:15:35,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.930590
2012-07-13 21:15:35,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.989348
2012-07-13 21:15:36,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.051198
2012-07-13 21:15:36,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.075939
2012-07-13 21:15:37,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.159437
2012-07-13 21:15:37,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.218195
2012-07-13 21:15:38,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.276953
2012-07-13 21:15:38,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.348081
2012-07-13 21:15:39,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.409931
2012-07-13 21:15:39,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.487244
2012-07-13 21:15:40,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.561465
2012-07-13 21:15:40,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.644963
2012-07-13 21:15:41,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.750109
2012-07-13 21:15:41,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.858348
2012-07-13 21:15:42,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.966586
2012-07-13 21:15:42,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.012974
2012-07-13 21:15:43,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.158323
2012-07-13 21:15:43,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.272746
2012-07-13 21:15:44,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.377892
2012-07-13 21:15:44,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.486130
2012-07-13 21:15:45,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.585091
2012-07-13 21:15:45,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.699514
2012-07-13 21:15:46,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.801568
2012-07-13 21:15:46,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.919084
2012-07-13 21:15:47,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.021137
2012-07-13 21:15:47,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.138653
2012-07-13 21:15:48,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.225244
2012-07-13 21:15:48,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.339667
2012-07-13 21:15:49,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.444813
2012-07-13 21:15:49,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.485016
2012-07-13 21:15:50,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.664382
2012-07-13 21:15:50,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.769528
2012-07-13 21:15:51,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.877767
2012-07-13 21:15:51,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.899414
2012-07-13 21:15:52,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.094244
2012-07-13 21:15:52,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.199389
2012-07-13 21:15:53,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.307628
2012-07-13 21:15:53,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.418959
2012-07-13 21:15:54,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.521012
2012-07-13 21:15:54,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.632343
2012-07-13 21:15:55,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.740581
2012-07-13 21:15:55,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.845727
2012-07-13 21:15:56,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.944688
2012-07-13 21:15:56,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.994168
2012-07-13 21:15:57,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.161165
2012-07-13 21:15:57,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.260126
2012-07-13 21:15:58,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.371457
2012-07-13 21:15:58,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.476602
2012-07-13 21:15:59,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.572471
2012-07-13 21:15:59,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.668339
2012-07-13 21:16:00,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.792040
2012-07-13 21:16:00,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.903371
2012-07-13 21:16:01,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.020887
2012-07-13 21:16:01,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.126033
2012-07-13 21:16:02,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.138403
2012-07-13 21:16:02,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.345602
2012-07-13 21:16:03,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.453840
2012-07-13 21:16:03,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.531154
2012-07-13 21:16:04,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.667225
2012-07-13 21:16:04,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.775463
2012-07-13 21:16:05,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.871331
2012-07-13 21:16:05,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.973385
2012-07-13 21:16:06,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.078531
2012-07-13 21:16:06,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.180584
2012-07-13 21:16:07,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.291915
2012-07-13 21:16:07,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.387783
2012-07-13 21:16:08,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.486744
2012-07-13 21:16:08,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.601167
2012-07-13 21:16:09,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.697036
2012-07-13 21:16:09,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.789811
2012-07-13 21:16:10,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.888772
2012-07-13 21:16:10,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.969178
2012-07-13 21:16:11,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.071231
2012-07-13 21:16:11,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.157822
2012-07-13 21:16:12,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.238228
2012-07-13 21:16:12,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.324818
2012-07-13 21:16:13,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.402132
2012-07-13 21:16:13,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.402132
2012-07-13 21:16:14,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.572220
2012-07-13 21:16:14,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.643349
2012-07-13 21:16:15,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.733032
2012-07-13 21:16:15,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.822715
2012-07-13 21:16:16,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.878380
2012-07-13 21:16:16,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.989711
2012-07-13 21:16:17,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.070117
2012-07-13 21:16:17,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.135060
2012-07-13 21:16:18,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.221651
2012-07-13 21:16:18,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.295871
2012-07-13 21:16:19,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.376277
2012-07-13 21:16:19,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.444313
2012-07-13 21:16:20,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.515441
2012-07-13 21:16:20,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.558736
2012-07-13 21:16:21,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.657697
2012-07-13 21:16:21,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.735010
2012-07-13 21:16:22,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.818508
2012-07-13 21:16:22,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.905099
2012-07-13 21:16:23,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.991690
2012-07-13 21:16:23,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.044263
2012-07-13 21:16:24,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.124668
2012-07-13 21:16:24,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.189611
2012-07-13 21:16:25,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.235999
2012-07-13 21:16:25,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.310220
2012-07-13 21:16:26,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.359700
2012-07-13 21:16:26,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.421551
2012-07-13 21:16:27,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.477216
2012-07-13 21:16:27,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.529789
2012-07-13 21:16:28,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.579270
2012-07-13 21:16:28,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.628750
2012-07-13 21:16:29,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.681323
2012-07-13 21:16:29,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.755543
2012-07-13 21:16:30,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.845227
2012-07-13 21:16:30,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.938002
2012-07-13 21:16:31,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.033871
2012-07-13 21:16:31,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.074074
2012-07-13 21:16:32,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.200867
2012-07-13 21:16:32,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.284365
2012-07-13 21:16:33,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.349308
2012-07-13 21:16:33,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.411159
2012-07-13 21:16:34,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.500842
2012-07-13 21:16:34,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.578155
2012-07-13 21:16:35,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.649283
2012-07-13 21:16:35,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.732782
2012-07-13 21:16:36,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.797725
2012-07-13 21:16:36,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.856483
2012-07-13 21:16:37,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.927611
2012-07-13 21:16:37,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.998739
2012-07-13 21:16:38,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.072959
2012-07-13 21:16:38,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.147180
2012-07-13 21:16:39,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.239956
2012-07-13 21:16:39,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.323454
2012-07-13 21:16:40,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.403860
2012-07-13 21:16:40,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.462618
2012-07-13 21:16:41,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.573948
2012-07-13 21:16:41,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.626521
2012-07-13 21:16:42,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.765685
2012-07-13 21:16:42,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.864646
2012-07-13 21:16:43,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.963607
2012-07-13 21:16:43,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.071845
2012-07-13 21:16:44,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.170806
2012-07-13 21:16:44,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.257397
2012-07-13 21:16:45,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.347080
2012-07-13 21:16:45,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.439856
2012-07-13 21:16:46,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.523354
2012-07-13 21:16:46,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.622315
2012-07-13 21:16:47,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.711998
2012-07-13 21:16:47,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.798589
2012-07-13 21:16:48,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.823329
2012-07-13 21:16:48,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.956307
2012-07-13 21:16:49,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.959400
2012-07-13 21:16:49,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.120211
2012-07-13 21:16:50,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.200617
2012-07-13 21:16:50,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.228450
2012-07-13 21:16:51,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.311948
2012-07-13 21:16:51,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.429464
2012-07-13 21:16:52,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.506777
2012-07-13 21:16:52,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.553165
2012-07-13 21:16:53,339 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.639756
2012-07-13 21:16:53,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.704699
2012-07-13 21:16:54,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.772734
2012-07-13 21:16:54,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.834585
2012-07-13 21:16:55,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.893343
2012-07-13 21:16:55,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.958286
2012-07-13 21:16:56,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.017044
2012-07-13 21:16:56,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.078894
2012-07-13 21:16:57,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.140745
2012-07-13 21:16:57,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.199503
2012-07-13 21:16:58,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.258261
2012-07-13 21:16:58,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.286093
2012-07-13 21:16:59,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.317019
2012-07-13 21:16:59,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.366499
2012-07-13 21:17:00,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.406702
2012-07-13 21:17:00,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.440720
2012-07-13 21:17:01,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.480922
2012-07-13 21:17:01,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.530403
2012-07-13 21:17:02,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.592253
2012-07-13 21:17:02,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.672659
2012-07-13 21:17:03,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.768527
2012-07-13 21:17:03,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.842748
2012-07-13 21:17:04,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.929339
2012-07-13 21:17:04,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.019022
2012-07-13 21:17:05,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.096335
2012-07-13 21:17:05,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.139630
2012-07-13 21:17:06,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.266424
2012-07-13 21:17:06,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.340645
2012-07-13 21:17:07,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.405588
2012-07-13 21:17:07,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.470531
2012-07-13 21:17:08,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.554029
2012-07-13 21:17:08,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.612787
2012-07-13 21:17:09,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.696285
2012-07-13 21:17:09,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.736488
2012-07-13 21:17:10,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.847819
2012-07-13 21:17:10,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.956057
2012-07-13 21:17:11,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.021000
2012-07-13 21:17:11,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.092128
2012-07-13 21:17:12,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.160164
2012-07-13 21:17:12,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.240569
2012-07-13 21:17:13,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.317883
2012-07-13 21:17:13,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.395196
2012-07-13 21:17:14,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.463231
2012-07-13 21:17:14,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.543637
2012-07-13 21:17:15,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.611673
2012-07-13 21:17:15,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.688986
2012-07-13 21:17:16,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.766299
2012-07-13 21:17:16,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.843612
2012-07-13 21:17:17,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.920925
2012-07-13 21:17:17,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.010608
2012-07-13 21:17:18,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.100292
2012-07-13 21:17:18,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.183790
2012-07-13 21:17:19,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.217808
2012-07-13 21:17:19,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.350786
2012-07-13 21:17:20,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.434284
2012-07-13 21:17:20,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.517783
2012-07-13 21:17:21,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.604373
2012-07-13 21:17:21,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.647669
2012-07-13 21:17:22,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.780647
2012-07-13 21:17:22,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.861053
2012-07-13 21:17:23,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.956921
2012-07-13 21:17:23,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.055882
2012-07-13 21:17:24,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.139380
2012-07-13 21:17:24,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.235248
2012-07-13 21:17:25,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.303284
2012-07-13 21:17:25,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.426985
2012-07-13 21:17:26,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.510483
2012-07-13 21:17:26,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.593981
2012-07-13 21:17:27,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.662017
2012-07-13 21:17:27,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.733145
2012-07-13 21:17:28,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.798088
2012-07-13 21:17:28,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.869216
2012-07-13 21:17:29,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.943437
2012-07-13 21:17:29,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.020750
2012-07-13 21:17:30,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.098063
2012-07-13 21:17:30,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.175376
2012-07-13 21:17:31,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.252689
2012-07-13 21:17:31,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.330002
2012-07-13 21:17:32,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.422778
2012-07-13 21:17:32,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.521739
2012-07-13 21:17:33,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.608330
2012-07-13 21:17:33,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.694920
2012-07-13 21:17:34,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.790789
2012-07-13 21:17:34,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.868102
2012-07-13 21:17:35,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.948508
2012-07-13 21:17:35,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.050561
2012-07-13 21:17:36,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.140244
2012-07-13 21:17:36,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.239205
2012-07-13 21:17:37,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.325796
2012-07-13 21:17:37,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.390739
2012-07-13 21:17:38,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.458774
2012-07-13 21:17:38,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.536087
2012-07-13 21:17:39,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.619586
2012-07-13 21:17:39,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.681436
2012-07-13 21:17:40,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.740194
2012-07-13 21:17:40,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.832970
2012-07-13 21:17:41,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.897913
2012-07-13 21:17:41,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.959763
2012-07-13 21:17:42,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.027799
2012-07-13 21:17:42,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.098927
2012-07-13 21:17:43,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.166963
2012-07-13 21:17:43,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.225721
2012-07-13 21:17:44,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.306126
2012-07-13 21:17:44,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.380347
2012-07-13 21:17:45,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.457660
2012-07-13 21:17:45,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.531881
2012-07-13 21:17:46,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.603009
2012-07-13 21:17:46,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.683414
2012-07-13 21:17:47,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.763820
2012-07-13 21:17:47,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.847318
2012-07-13 21:17:48,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.927724
2012-07-13 21:17:48,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.011222
2012-07-13 21:17:49,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.063795
2012-07-13 21:17:49,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.141108
2012-07-13 21:17:50,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.221514
2012-07-13 21:17:51,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.305012
2012-07-13 21:17:51,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.391603
2012-07-13 21:17:52,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.475101
2012-07-13 21:17:52,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.493656
2012-07-13 21:17:53,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.617357
2012-07-13 21:17:53,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.694670
2012-07-13 21:17:54,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.768891
2012-07-13 21:17:54,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.843111
2012-07-13 21:17:55,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.917332
2012-07-13 21:17:55,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.935887
2012-07-13 21:17:56,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.071958
2012-07-13 21:17:56,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.139994
2012-07-13 21:17:57,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.220400
2012-07-13 21:17:57,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.294620
2012-07-13 21:17:58,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.378118
2012-07-13 21:17:58,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.452339
2012-07-13 21:17:59,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.520375
2012-07-13 21:17:59,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.610058
2012-07-13 21:18:00,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.696649
2012-07-13 21:18:00,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.736851
2012-07-13 21:18:01,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.838905
2012-07-13 21:18:01,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.928588
2012-07-13 21:18:02,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.015179
2012-07-13 21:18:02,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.092492
2012-07-13 21:18:03,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.172897
2012-07-13 21:18:03,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.256396
2012-07-13 21:18:04,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.333709
2012-07-13 21:18:04,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.414114
2012-07-13 21:18:05,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.500705
2012-07-13 21:18:05,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.578018
2012-07-13 21:18:06,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.664609
2012-07-13 21:18:06,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.735737
2012-07-13 21:18:07,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.816143
2012-07-13 21:18:07,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.908919
2012-07-13 21:18:08,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.010972
2012-07-13 21:18:08,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.097563
2012-07-13 21:18:09,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.187246
2012-07-13 21:18:09,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.218171
2012-07-13 21:18:10,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.338780
2012-07-13 21:18:10,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.419185
2012-07-13 21:18:11,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.502683
2012-07-13 21:18:11,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.598552
2012-07-13 21:18:12,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.682050
2012-07-13 21:18:12,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.759363
2012-07-13 21:18:13,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.836676
2012-07-13 21:18:13,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.935637
2012-07-13 21:18:14,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.997487
2012-07-13 21:18:14,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.074801
2012-07-13 21:18:15,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.149021
2012-07-13 21:18:15,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.207779
2012-07-13 21:18:16,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.309833
2012-07-13 21:18:16,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.380961
2012-07-13 21:18:17,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.461366
2012-07-13 21:18:17,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.566512
2012-07-13 21:18:18,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.625270
2012-07-13 21:18:18,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.752064
2012-07-13 21:18:19,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.792267
2012-07-13 21:18:19,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.906690
2012-07-13 21:18:20,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.993281
2012-07-13 21:18:20,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.064409
2012-07-13 21:18:21,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.132444
2012-07-13 21:18:21,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.200480
2012-07-13 21:18:22,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.277793
2012-07-13 21:18:22,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.364384
2012-07-13 21:18:23,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.444789
2012-07-13 21:18:23,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.534473
2012-07-13 21:18:24,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.608693
2012-07-13 21:18:24,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.713839
2012-07-13 21:18:25,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.797337
2012-07-13 21:18:25,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.853003
2012-07-13 21:18:26,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.961241
2012-07-13 21:18:26,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.023092
2012-07-13 21:18:27,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.106590
2012-07-13 21:18:27,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.193181
2012-07-13 21:18:28,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.285956
2012-07-13 21:18:28,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.378732
2012-07-13 21:18:29,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.474600
2012-07-13 21:18:29,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.576654
2012-07-13 21:18:30,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.666337
2012-07-13 21:18:30,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.762205
2012-07-13 21:18:31,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.854981
2012-07-13 21:18:31,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.953942
2012-07-13 21:18:32,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.059088
2012-07-13 21:18:32,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.161141
2012-07-13 21:18:33,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.247732
2012-07-13 21:18:33,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.334323
2012-07-13 21:18:34,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.417821
2012-07-13 21:18:34,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.498226
2012-07-13 21:18:35,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.566262
2012-07-13 21:18:35,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.572447
2012-07-13 21:18:36,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.665223
2012-07-13 21:18:36,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.826034
2012-07-13 21:18:37,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.835312
2012-07-13 21:18:37,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.921902
2012-07-13 21:18:38,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.971383
2012-07-13 21:18:38,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.138379
2012-07-13 21:18:39,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.228062
2012-07-13 21:18:39,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.323931
2012-07-13 21:18:40,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.404336
2012-07-13 21:18:40,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.494020
2012-07-13 21:18:41,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.583703
2012-07-13 21:18:41,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.688849
2012-07-13 21:18:42,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.787810
2012-07-13 21:18:42,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.883678
2012-07-13 21:18:43,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.985731
2012-07-13 21:18:43,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.072322
2012-07-13 21:18:44,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.171283
2012-07-13 21:18:44,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.245503
2012-07-13 21:18:45,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.335187
2012-07-13 21:18:45,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.344464
2012-07-13 21:18:46,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.418685
2012-07-13 21:18:46,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.613514
2012-07-13 21:18:47,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.706290
2012-07-13 21:18:47,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.799065
2012-07-13 21:18:48,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.829991
2012-07-13 21:18:48,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.981524
2012-07-13 21:18:49,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.065023
2012-07-13 21:18:49,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.182539
2012-07-13 21:18:50,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.303147
2012-07-13 21:18:50,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.414478
2012-07-13 21:18:51,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.507254
2012-07-13 21:18:51,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.596937
2012-07-13 21:18:52,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.689713
2012-07-13 21:18:52,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.797951
2012-07-13 21:18:53,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.903097
2012-07-13 21:18:53,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.998965
2012-07-13 21:18:54,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.088649
2012-07-13 21:18:54,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.172147
2012-07-13 21:18:55,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.172147
2012-07-13 21:18:55,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.258737
2012-07-13 21:18:56,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.422641
2012-07-13 21:18:56,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.515417
2012-07-13 21:18:57,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.617470
2012-07-13 21:18:57,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.744264
2012-07-13 21:18:58,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.827762
2012-07-13 21:18:58,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.827762
2012-07-13 21:18:59,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.019499
2012-07-13 21:18:59,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.198865
2012-07-13 21:19:00,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.322566
2012-07-13 21:19:00,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.427712
2012-07-13 21:19:01,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.539043
2012-07-13 21:19:01,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.644189
2012-07-13 21:19:02,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.746242
2012-07-13 21:19:02,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.845203
2012-07-13 21:19:03,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.941071
2012-07-13 21:19:03,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.030755
2012-07-13 21:19:04,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.095698
2012-07-13 21:19:04,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.095698
2012-07-13 21:19:05,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.290527
2012-07-13 21:19:05,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.389487
2012-07-13 21:19:06,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.513189
2012-07-13 21:19:06,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.609057
2012-07-13 21:19:07,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.720388
2012-07-13 21:19:07,721 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.806978
2012-07-13 21:19:08,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.856459
2012-07-13 21:19:08,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.983252
2012-07-13 21:19:09,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.076028
2012-07-13 21:19:09,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.162619
2012-07-13 21:19:10,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.264672
2012-07-13 21:19:10,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.351263
2012-07-13 21:19:11,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.416206
2012-07-13 21:19:11,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.444039
2012-07-13 21:19:12,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.567740
2012-07-13 21:19:12,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.669793
2012-07-13 21:19:13,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.753291
2012-07-13 21:19:13,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.827512
2012-07-13 21:19:14,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.911010
2012-07-13 21:19:14,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.979046
2012-07-13 21:19:15,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.056359
2012-07-13 21:19:15,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.142949
2012-07-13 21:19:16,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.214078
2012-07-13 21:19:16,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.291391
2012-07-13 21:19:17,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.356334
2012-07-13 21:19:17,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.430554
2012-07-13 21:19:18,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.489312
2012-07-13 21:19:18,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.489312
2012-07-13 21:19:19,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.699604
2012-07-13 21:19:19,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.786195
2012-07-13 21:19:20,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.878971
2012-07-13 21:19:20,772 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.959376
2012-07-13 21:19:21,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.036689
2012-07-13 21:19:21,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.104725
2012-07-13 21:19:22,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.194408
2012-07-13 21:19:22,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.280999
2012-07-13 21:19:23,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.358312
2012-07-13 21:19:23,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.435625
2012-07-13 21:19:24,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.522216
2012-07-13 21:19:24,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.611899
2012-07-13 21:19:25,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.683027
2012-07-13 21:19:25,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.710860
2012-07-13 21:19:26,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.710860
2012-07-13 21:19:26,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.710860
2012-07-13 21:19:27,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.004650
2012-07-13 21:19:27,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.078870
2012-07-13 21:19:28,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.078870
2012-07-13 21:19:28,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.245867
2012-07-13 21:19:29,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.298440
2012-07-13 21:19:29,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.394308
2012-07-13 21:19:30,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.474714
2012-07-13 21:19:30,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.545842
2012-07-13 21:19:31,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.623155
2012-07-13 21:19:31,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.709746
2012-07-13 21:19:32,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.796336
2012-07-13 21:19:32,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.892205
2012-07-13 21:19:33,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.966425
2012-07-13 21:19:33,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.062294
2012-07-13 21:19:34,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.164347
2012-07-13 21:19:34,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.278770
2012-07-13 21:19:35,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.362269
2012-07-13 21:19:35,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.451952
2012-07-13 21:19:36,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.532357
2012-07-13 21:19:36,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.606578
2012-07-13 21:19:37,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.606578
2012-07-13 21:19:37,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.606578
2012-07-13 21:19:38,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.606578
2012-07-13 21:19:38,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.813777
2012-07-13 21:19:39,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.020976
2012-07-13 21:19:39,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.098290
2012-07-13 21:19:40,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.178695
2012-07-13 21:19:40,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.246731
2012-07-13 21:19:41,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.348784
2012-07-13 21:19:41,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.429190
2012-07-13 21:19:42,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.515781
2012-07-13 21:19:42,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.599279
2012-07-13 21:19:43,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.685869
2012-07-13 21:19:43,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.766275
2012-07-13 21:19:44,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.852866
2012-07-13 21:19:44,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.936364
2012-07-13 21:19:45,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.016770
2012-07-13 21:19:45,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.090990
2012-07-13 21:19:46,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.159026
2012-07-13 21:19:46,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.233246
2012-07-13 21:19:47,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.301282
2012-07-13 21:19:47,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.301282
2012-07-13 21:19:48,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.301282
2012-07-13 21:19:48,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.527036
2012-07-13 21:19:49,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.595072
2012-07-13 21:19:49,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.663108
2012-07-13 21:19:50,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.737328
2012-07-13 21:19:50,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.799179
2012-07-13 21:19:51,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.861029
2012-07-13 21:19:51,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.922880
2012-07-13 21:19:52,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.922880
2012-07-13 21:19:52,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.099154
2012-07-13 21:19:53,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.167189
2012-07-13 21:19:53,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.250687
2012-07-13 21:19:54,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.324908
2012-07-13 21:19:54,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.411499
2012-07-13 21:19:55,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.491904
2012-07-13 21:19:55,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.575403
2012-07-13 21:19:56,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.655808
2012-07-13 21:19:56,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.742399
2012-07-13 21:19:57,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.764047
2012-07-13 21:19:57,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.791879
2012-07-13 21:19:58,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.958876
2012-07-13 21:19:58,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.054744
2012-07-13 21:19:59,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.128965
2012-07-13 21:19:59,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.218648
2012-07-13 21:20:00,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.299054
2012-07-13 21:20:00,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.376367
2012-07-13 21:20:01,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.456772
2012-07-13 21:20:01,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.534085
2012-07-13 21:20:02,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.623769
2012-07-13 21:20:02,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.710359
2012-07-13 21:20:03,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.759840
2012-07-13 21:20:03,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.759840
2012-07-13 21:20:04,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.945391
2012-07-13 21:20:04,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.028890
2012-07-13 21:20:05,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.121665
2012-07-13 21:20:05,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.208256
2012-07-13 21:20:06,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.267014
2012-07-13 21:20:06,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.267014
2012-07-13 21:20:07,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.458751
2012-07-13 21:20:07,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.536064
2012-07-13 21:20:08,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.604099
2012-07-13 21:20:08,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.610284
2012-07-13 21:20:09,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.749448
2012-07-13 21:20:09,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.829854
2012-07-13 21:20:10,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.894797
2012-07-13 21:20:10,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.978295
2012-07-13 21:20:11,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.049423
2012-07-13 21:20:11,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.129829
2012-07-13 21:20:12,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.163846
2012-07-13 21:20:12,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.268992
2012-07-13 21:20:13,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.340120
2012-07-13 21:20:13,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.392693
2012-07-13 21:20:14,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.457636
2012-07-13 21:20:14,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.534949
2012-07-13 21:20:15,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.609170
2012-07-13 21:20:15,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.701946
2012-07-13 21:20:16,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.791629
2012-07-13 21:20:16,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.831832
2012-07-13 21:20:17,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.940070
2012-07-13 21:20:17,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.045216
2012-07-13 21:20:18,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.128714
2012-07-13 21:20:18,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.240045
2012-07-13 21:20:19,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.317358
2012-07-13 21:20:19,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.410134
2012-07-13 21:20:20,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.453430
2012-07-13 21:20:20,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.589501
2012-07-13 21:20:21,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.700832
2012-07-13 21:20:21,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.809070
2012-07-13 21:20:22,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.895661
2012-07-13 21:20:22,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.022454
2012-07-13 21:20:23,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.136878
2012-07-13 21:20:23,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.242024
2012-07-13 21:20:24,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.303874
2012-07-13 21:20:24,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.439945
2012-07-13 21:20:25,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.551276
2012-07-13 21:20:25,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.650237
2012-07-13 21:20:26,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.773938
2012-07-13 21:20:26,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.875991
2012-07-13 21:20:27,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.984230
2012-07-13 21:20:27,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.089376
2012-07-13 21:20:28,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.179059
2012-07-13 21:20:28,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.296575
2012-07-13 21:20:29,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.407906
2012-07-13 21:20:29,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.513052
2012-07-13 21:20:30,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.621290
2012-07-13 21:20:30,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.735713
2012-07-13 21:20:31,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.785194
2012-07-13 21:20:31,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.908895
2012-07-13 21:20:32,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.989300
2012-07-13 21:20:32,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.097539
2012-07-13 21:20:33,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.224332
2012-07-13 21:20:33,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.326386
2012-07-13 21:20:34,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.425347
2012-07-13 21:20:34,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.505752
2012-07-13 21:20:35,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.626361
2012-07-13 21:20:35,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.728414
2012-07-13 21:20:36,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.818097
2012-07-13 21:20:36,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.923243
2012-07-13 21:20:37,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.028389
2012-07-13 21:20:37,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.114980
2012-07-13 21:20:38,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.164460
2012-07-13 21:20:38,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.300531
2012-07-13 21:20:39,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.408770
2012-07-13 21:20:39,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.529378
2012-07-13 21:20:40,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.628339
2012-07-13 21:20:40,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.724207
2012-07-13 21:20:41,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.832446
2012-07-13 21:20:42,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.931406
2012-07-13 21:20:42,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.030367
2012-07-13 21:20:43,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.135513
2012-07-13 21:20:43,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.240659
2012-07-13 21:20:44,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.355082
2012-07-13 21:20:44,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.475691
2012-07-13 21:20:45,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.571559
2012-07-13 21:20:45,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.692168
2012-07-13 21:20:46,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.791129
2012-07-13 21:20:46,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.902459
2012-07-13 21:20:47,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.982865
2012-07-13 21:20:47,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.063271
2012-07-13 21:20:48,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.100381
2012-07-13 21:20:48,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.267378
2012-07-13 21:20:49,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.350876
2012-07-13 21:20:49,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.449837
2012-07-13 21:20:50,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.545705
2012-07-13 21:20:50,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.632296
2012-07-13 21:20:51,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.715794
2012-07-13 21:20:51,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.814755
2012-07-13 21:20:52,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.895160
2012-07-13 21:20:52,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.975566
2012-07-13 21:20:53,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.062157
2012-07-13 21:20:53,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.164210
2012-07-13 21:20:54,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.250801
2012-07-13 21:20:54,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.343576
2012-07-13 21:20:55,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.470370
2012-07-13 21:20:55,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.600256
2012-07-13 21:20:56,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.631181
2012-07-13 21:20:56,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.804363
2012-07-13 21:20:57,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.897138
2012-07-13 21:20:57,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.986822
2012-07-13 21:20:58,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.082690
2012-07-13 21:20:58,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.175466
2012-07-13 21:20:59,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.299167
2012-07-13 21:20:59,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.429053
2012-07-13 21:21:00,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.506366
2012-07-13 21:21:00,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.565124
2012-07-13 21:21:01,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.778508
2012-07-13 21:21:01,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.849636
2012-07-13 21:21:02,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.991892
2012-07-13 21:21:02,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.097038
2012-07-13 21:21:03,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.205277
2012-07-13 21:21:03,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.313515
2012-07-13 21:21:04,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.418661
2012-07-13 21:21:04,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.523807
2012-07-13 21:21:05,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.635138
2012-07-13 21:21:05,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.740284
2012-07-13 21:21:06,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.845430
2012-07-13 21:21:06,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.953668
2012-07-13 21:21:07,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.027889
2012-07-13 21:21:07,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.163960
2012-07-13 21:21:08,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.275291
2012-07-13 21:21:08,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.374251
2012-07-13 21:21:09,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.491767
2012-07-13 21:21:09,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.538155
2012-07-13 21:21:10,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.689689
2012-07-13 21:21:10,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.791742
2012-07-13 21:21:11,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.906166
2012-07-13 21:21:11,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.008219
2012-07-13 21:21:12,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.131920
2012-07-13 21:21:12,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.237066
2012-07-13 21:21:13,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.342212
2012-07-13 21:21:13,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.444265
2012-07-13 21:21:14,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.546319
2012-07-13 21:21:14,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.632909
2012-07-13 21:21:15,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.734963
2012-07-13 21:21:15,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.818461
2012-07-13 21:21:16,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.914329
2012-07-13 21:21:16,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.994735
2012-07-13 21:21:17,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.053493
2012-07-13 21:21:17,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.053493
2012-07-13 21:21:18,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.068955
2012-07-13 21:21:18,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.232859
2012-07-13 21:21:19,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.477169
2012-07-13 21:21:19,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.563759
2012-07-13 21:21:20,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.653443
2012-07-13 21:21:20,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.743126
2012-07-13 21:21:21,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.848272
2012-07-13 21:21:21,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.931770
2012-07-13 21:21:22,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.030731
2012-07-13 21:21:22,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.135877
2012-07-13 21:21:23,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.222467
2012-07-13 21:21:23,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.321428
2012-07-13 21:21:24,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.426574
2012-07-13 21:21:24,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.528627
2012-07-13 21:21:25,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.618311
2012-07-13 21:21:25,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.695624
2012-07-13 21:21:26,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.714179
2012-07-13 21:21:26,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.726549
2012-07-13 21:21:27,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.893545
2012-07-13 21:21:27,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.893545
2012-07-13 21:21:28,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.156410
2012-07-13 21:21:28,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.261556
2012-07-13 21:21:29,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.366702
2012-07-13 21:21:29,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.468755
2012-07-13 21:21:30,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.564623
2012-07-13 21:21:30,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.660492
2012-07-13 21:21:31,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.691417
2012-07-13 21:21:31,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.855321
2012-07-13 21:21:32,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.957374
2012-07-13 21:21:32,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.037780
2012-07-13 21:21:33,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.146018
2012-07-13 21:21:33,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.248072
2012-07-13 21:21:34,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.350125
2012-07-13 21:21:34,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.433623
2012-07-13 21:21:35,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.532584
2012-07-13 21:21:35,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.612990
2012-07-13 21:21:36,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.702673
2012-07-13 21:21:36,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.724321
2012-07-13 21:21:37,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.903687
2012-07-13 21:21:37,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.005740
2012-07-13 21:21:38,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.110886
2012-07-13 21:21:38,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.200569
2012-07-13 21:21:39,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.311900
2012-07-13 21:21:39,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.395399
2012-07-13 21:21:40,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.500544
2012-07-13 21:21:40,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.580950
2012-07-13 21:21:41,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.692281
2012-07-13 21:21:41,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.785057
2012-07-13 21:21:42,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.896388
2012-07-13 21:21:42,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.023181
2012-07-13 21:21:43,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.081939
2012-07-13 21:21:43,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.196363
2012-07-13 21:21:44,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.230380
2012-07-13 21:21:44,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.446857
2012-07-13 21:21:45,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.558188
2012-07-13 21:21:45,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.660242
2012-07-13 21:21:46,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.756110
2012-07-13 21:21:46,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.861256
2012-07-13 21:21:47,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.966402
2012-07-13 21:21:47,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.071547
2012-07-13 21:21:48,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.176693
2012-07-13 21:21:48,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.288024
2012-07-13 21:21:49,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.393170
2012-07-13 21:21:49,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.504501
2012-07-13 21:21:50,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.606554
2012-07-13 21:21:50,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.699330
2012-07-13 21:21:51,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.813754
2012-07-13 21:21:51,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.847771
2012-07-13 21:21:52,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-13 21:21:52,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-13 21:21:52,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-13 21:21:52,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.023637
2012-07-13 21:21:52,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.134282
2012-07-13 21:21:53,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.214688
2012-07-13 21:21:53,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.341481
2012-07-13 21:21:54,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.455905
2012-07-13 21:21:54,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.471367
2012-07-13 21:21:55,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.666197
2012-07-13 21:21:55,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.777527
2012-07-13 21:21:56,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.882673
2012-07-13 21:21:56,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.987819
2012-07-13 21:21:57,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.099150
2012-07-13 21:21:57,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.201203
2012-07-13 21:21:58,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.312534
2012-07-13 21:21:58,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.420773
2012-07-13 21:21:59,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.525919
2012-07-13 21:21:59,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.541381
2012-07-13 21:22:00,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.739303
2012-07-13 21:22:00,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.841356
2012-07-13 21:22:01,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.949595
2012-07-13 21:22:01,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.036185
2012-07-13 21:22:02,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.144424
2012-07-13 21:22:02,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.274310
2012-07-13 21:22:03,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.289772
2012-07-13 21:22:03,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.487694
2012-07-13 21:22:04,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.595932
2012-07-13 21:22:04,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.704171
2012-07-13 21:22:05,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.809317
2012-07-13 21:22:05,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.809317
2012-07-13 21:22:06,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.025793
2012-07-13 21:22:06,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.130939
2012-07-13 21:22:07,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.236085
2012-07-13 21:22:07,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.341231
2012-07-13 21:22:08,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.378341
2012-07-13 21:22:08,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.560800
2012-07-13 21:22:09,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.669039
2012-07-13 21:22:09,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.771092
2012-07-13 21:22:10,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.882423
2012-07-13 21:22:10,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.938088
2012-07-13 21:22:11,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.089622
2012-07-13 21:22:11,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.191676
2012-07-13 21:22:12,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.309192
2012-07-13 21:22:12,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.417430
2012-07-13 21:22:13,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.504281
2012-07-13 21:22:13,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.624629
2012-07-13 21:22:14,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.739053
2012-07-13 21:22:14,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.841106
2012-07-13 21:22:15,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.940067
2012-07-13 21:22:15,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.051398
2012-07-13 21:22:16,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.162729
2012-07-13 21:22:16,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.264782
2012-07-13 21:22:17,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.369928
2012-07-13 21:22:17,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.481259
2012-07-13 21:22:18,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.589497
2012-07-13 21:22:18,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.697736
2012-07-13 21:22:19,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.809066
2012-07-13 21:22:19,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.911120
2012-07-13 21:22:20,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.019358
2012-07-13 21:22:20,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.130689
2012-07-13 21:22:21,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.238927
2012-07-13 21:22:21,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.337888
2012-07-13 21:22:22,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.446127
2012-07-13 21:22:22,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.560550
2012-07-13 21:22:23,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.637863
2012-07-13 21:22:23,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.705899
2012-07-13 21:22:24,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.869803
2012-07-13 21:22:25,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.984226
2012-07-13 21:22:25,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.089372
2012-07-13 21:22:26,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.098650
2012-07-13 21:22:26,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.138852
2012-07-13 21:22:27,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.395532
2012-07-13 21:22:27,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.504567
2012-07-13 21:22:28,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.618194
2012-07-13 21:22:28,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.729525
2012-07-13 21:22:29,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.837763
2012-07-13 21:22:29,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.942909
2012-07-13 21:22:30,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.054240
2012-07-13 21:22:30,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.153201
2012-07-13 21:22:31,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.267624
2012-07-13 21:22:31,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.375863
2012-07-13 21:22:32,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.484101
2012-07-13 21:22:32,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.539766
2012-07-13 21:22:33,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.638727
2012-07-13 21:22:33,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.805724
2012-07-13 21:22:34,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.910870
2012-07-13 21:22:34,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.978905
2012-07-13 21:22:35,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.124254
2012-07-13 21:22:35,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.232492
2012-07-13 21:22:36,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.331453
2012-07-13 21:22:36,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.445876
2012-07-13 21:22:37,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.554115
2012-07-13 21:22:37,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.659261
2012-07-13 21:22:38,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.761314
2012-07-13 21:22:38,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.872645
2012-07-13 21:22:39,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.980883
2012-07-13 21:22:39,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.089122
2012-07-13 21:22:40,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.126232
2012-07-13 21:22:40,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.302506
2012-07-13 21:22:41,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.410744
2012-07-13 21:22:41,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.518983
2012-07-13 21:22:42,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.624129
2012-07-13 21:22:42,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.670517
2012-07-13 21:22:43,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.840605
2012-07-13 21:22:43,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.945751
2012-07-13 21:22:44,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.053990
2012-07-13 21:22:44,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.162228
2012-07-13 21:22:45,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.267374
2012-07-13 21:22:45,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.375612
2012-07-13 21:22:46,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.480758
2012-07-13 21:22:46,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.588997
2012-07-13 21:22:47,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.697235
2012-07-13 21:22:47,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.796196
2012-07-13 21:22:48,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.820936
2012-07-13 21:22:48,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.015765
2012-07-13 21:22:49,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.124004
2012-07-13 21:22:49,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.232242
2012-07-13 21:22:50,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.334295
2012-07-13 21:22:50,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.445626
2012-07-13 21:22:51,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.547680
2012-07-13 21:22:51,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.659010
2012-07-13 21:22:52,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.767249
2012-07-13 21:22:52,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.875487
2012-07-13 21:22:53,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.980633
2012-07-13 21:22:53,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2012-07-13 21:22:53,433 DEBUG: install progress dpkg-exec 0.000000
2012-07-13 21:22:53,906 DEBUG: install progress patch 0.000000
2012-07-13 21:22:53,908 DEBUG: install progress patch 4.000000
2012-07-13 21:22:54,211 DEBUG: install progress patch 8.000000
2012-07-13 21:22:54,264 DEBUG: install progress patch 12.000000
2012-07-13 21:22:54,530 DEBUG: install progress dkms 12.000000
2012-07-13 21:22:54,631 DEBUG: install progress dkms 16.000000
2012-07-13 21:22:54,884 DEBUG: install progress dkms 20.000000
2012-07-13 21:22:54,941 DEBUG: install progress dkms 24.000000
2012-07-13 21:22:55,204 DEBUG: install progress fakeroot 24.000000
2012-07-13 21:22:55,305 DEBUG: install progress fakeroot 28.000000
2012-07-13 21:22:55,498 DEBUG: install progress fakeroot 32.000000
2012-07-13 21:22:55,550 DEBUG: install progress fakeroot 36.000000
2012-07-13 21:22:55,885 DEBUG: install progress fglrx-updates 36.000000
2012-07-13 21:22:55,987 DEBUG: install progress fglrx-updates 40.000000
2012-07-13 21:22:59,211 DEBUG: install progress fglrx-updates 44.000000
2012-07-13 21:22:59,282 DEBUG: install progress fglrx-updates 48.000000
2012-07-13 21:22:59,491 DEBUG: install progress fglrx-amdcccle-updates 48.000000
2012-07-13 21:22:59,592 DEBUG: install progress fglrx-amdcccle-updates 52.000000
2012-07-13 21:22:59,926 DEBUG: install progress fglrx-amdcccle-updates 56.000000
2012-07-13 21:23:00,013 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-07-13 21:23:00,088 DEBUG: install progress man-db 60.000000
2012-07-13 21:23:02,321 DEBUG: install progress ureadahead 60.000000
2012-07-13 21:23:02,645 DEBUG: install progress dpkg-exec 60.000000
2012-07-13 21:23:02,703 DEBUG: install progress patch 60.000000
2012-07-13 21:23:02,784 DEBUG: install progress patch 64.000000
2012-07-13 21:23:02,843 DEBUG: install progress patch 68.000000
2012-07-13 21:23:02,902 DEBUG: install progress dkms 68.000000
2012-07-13 21:23:03,798 DEBUG: install progress dkms 72.000000
2012-07-13 21:23:03,848 DEBUG: install progress dkms 76.000000
2012-07-13 21:23:03,900 DEBUG: install progress fakeroot 76.000000
2012-07-13 21:23:03,951 DEBUG: install progress fakeroot 80.000000
2012-07-13 21:23:04,556 DEBUG: install progress fakeroot 84.000000
2012-07-13 21:23:04,614 DEBUG: install progress fglrx-updates 84.000000
2012-07-13 21:23:04,868 DEBUG: install progress fglrx-updates 88.000000
2012-07-13 21:23:34,390 DEBUG: install progress fglrx-updates 92.000000
2012-07-13 21:23:34,760 DEBUG: install progress bamfdaemon 92.000000
2012-07-13 21:23:34,988 DEBUG: install progress fglrx-amdcccle-updates 92.000000
2012-07-13 21:23:35,055 DEBUG: install progress fglrx-amdcccle-updates 96.000000
2012-07-13 21:23:35,114 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-13 21:23:35,174 DEBUG: install progress initramfs-tools 100.000000
2012-07-13 21:23:52,769 DEBUG: install progress libc-bin 100.000000
2012-07-13 21:23:53,874 DEBUG: Selecting previously unselected package patch.
(Reading database ... 255659 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic-pae
Building for architecture i686
Building initial module for 3.2.0-26-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic-pae/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-13 21:23:54,195 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-13 21:24:22,954 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:24:22,955 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:24:22,987 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:24:22,988 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:44,742 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:44,743 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:44,775 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:44,775 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:44,843 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:44,843 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:25:44,911 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:44,911 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:44,942 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:44,943 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:45,047 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:45,047 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:45,078 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:45,079 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:25:45,139 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:25:45,140 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:25:46,307 DEBUG: Shutting down
2012-07-13 21:36:06,740 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c>
2012-07-13 21:36:08,797 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic-pae/modules.alias
2012-07-13 21:36:08,931 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-13 21:36:08,936 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-13 21:36:09,018 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-13 21:36:09,103 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-13 21:36:09,103 DEBUG: fglrx.available: falling back to default
2012-07-13 21:36:09,216 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:36:09,220 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-13 21:36:09,225 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-13 21:36:09,226 DEBUG: fglrx.available: falling back to default
2012-07-13 21:36:09,287 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-13 21:36:09,287 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-13 21:36:09,296 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-13 21:36:09,296 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-13 21:36:09,343 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-13 21:36:09,344 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-13 21:36:09,365 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-13 21:36:09,375 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-13 21:36:09,379 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,406 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:36:09,406 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:36:09,411 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-13 21:36:09,416 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-13 21:36:09,417 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,464 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-13 21:36:09,471 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-13 21:36:09,477 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-13 21:36:09,478 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,520 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:36:09,524 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-13 21:36:09,529 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-13 21:36:09,530 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,551 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:36:09,551 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:36:09,555 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-13 21:36:09,561 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-13 21:36:09,562 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,584 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:36:09,585 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:36:09,590 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-13 21:36:09,596 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-13 21:36:09,597 DEBUG: nvidia.available: falling back to default
2012-07-13 21:36:09,618 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:36:09,618 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:36:09,618 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-13 21:36:09,624 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-13 21:36:09,625 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-13 21:36:09,625 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-13 21:36:09,625 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-13 21:36:09,665 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-13 21:36:09,700 DEBUG: Software modem not available
2012-07-13 21:36:09,701 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-13 21:36:09,766 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-13 21:36:09,767 DEBUG: Firmware for DVB cards not available
2012-07-13 21:36:09,767 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-13 21:36:09,780 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-13 21:36:09,797 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-13 21:36:09,834 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-13 21:36:09,834 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-13 21:36:09,840 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-13 21:36:09,867 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-13 21:36:09,868 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-13 21:36:09,868 DEBUG: all custom handlers loaded
2012-07-13 21:36:09,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:36:10,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-13 21:36:10,335 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,335 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:10,241 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:36:10,345 DEBUG: fglrx.available: falling back to default
2012-07-13 21:36:10,411 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,412 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:10,380 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:36:10,412 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-13 21:36:10,434 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,435 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:10,413 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:36:10,441 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-13 21:36:10,448 DEBUG: fglrx.available: falling back to default
2012-07-13 21:36:10,514 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,514 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:10,486 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:36:10,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-13 21:36:10,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-07-13 21:36:10,672 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,673 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:10,651 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:36:10,685 DEBUG: fglrx.available: falling back to default
2012-07-13 21:36:10,751 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:10,752 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:10,724 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:36:10,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:36:10,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:36:10,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:36:10,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:36:10,793 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-07-13 21:36:10,793 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:36:10,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-13 21:36:10,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-13 21:36:10,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:36:10,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:36:10,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:36:10,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-13 21:36:10,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:36:10,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:36:10,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:36:10,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:36:10,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-13 21:36:10,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-13 21:36:10,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:36:10,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:36:10,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:36:10,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-07-13 21:36:10,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:36:10,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:36:10,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:36:10,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-13 21:36:10,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:36:10,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:36:10,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:36:10,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:36:10,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:36:10,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:36:10,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:36:10,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:36:10,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:36:10,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:36:10,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:36:10,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-13 21:36:10,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-13 21:36:10,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:36:10,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:36:10,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:36:10,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:36:10,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:36:10,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-07-13 21:36:10,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:36:10,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:36:10,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:36:10,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:36:10,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:36:10,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:36:10,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:36:10,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:36:10,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-13 21:36:10,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-13 21:36:10,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:36:10,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:36:10,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:36:10,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:36:10,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:36:10,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:36:10,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720ed0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:36:10,944 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:36:10,945 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:36:10,946 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:36:10,947 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:36:10,948 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb690d84c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:36:11,050 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:11,050 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:11,124 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:11,125 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:11,268 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:11,269 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:11,316 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:11,316 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:36:11,344 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:11,344 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:13,518 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:13,518 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:22,353 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:36:22,353 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:36:26,125 DEBUG: Installing package: fglrx
2012-07-13 21:36:26,707 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-07-13 21:36:26,708 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-07-13 21:36:26,738 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-07-13 21:36:26,869 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-07-13 21:36:27,003 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-07-13 21:36:27,504 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.083259
2012-07-13 21:36:28,005 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.188980
2012-07-13 21:36:28,507 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.204528
2012-07-13 21:36:29,008 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.403533
2012-07-13 21:36:29,510 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.512364
2012-07-13 21:36:30,011 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.621195
2012-07-13 21:36:30,513 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.726916
2012-07-13 21:36:31,015 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.782886
2012-07-13 21:36:31,516 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.944578
2012-07-13 21:36:32,017 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.050299
2012-07-13 21:36:32,519 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.159130
2012-07-13 21:36:33,020 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.264852
2012-07-13 21:36:33,522 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.367464
2012-07-13 21:36:34,023 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.482514
2012-07-13 21:36:34,536 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.591345
2012-07-13 21:36:35,037 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.700176
2012-07-13 21:36:35,539 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.805897
2012-07-13 21:36:36,040 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.911618
2012-07-13 21:36:36,542 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.914728
2012-07-13 21:36:37,042 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.129280
2012-07-13 21:36:37,544 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.235002
2012-07-13 21:36:38,045 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.337614
2012-07-13 21:36:38,546 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.437116
2012-07-13 21:36:39,047 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.545947
2012-07-13 21:36:39,548 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.657888
2012-07-13 21:36:40,049 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.772938
2012-07-13 21:36:40,551 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.872440
2012-07-13 21:36:41,052 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.971943
2012-07-13 21:36:41,554 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.086992
2012-07-13 21:36:42,055 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.195823
2012-07-13 21:36:42,556 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.298435
2012-07-13 21:36:43,057 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.332639
2012-07-13 21:36:43,558 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.509878
2012-07-13 21:36:44,059 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.609381
2012-07-13 21:36:44,560 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.708884
2012-07-13 21:36:45,062 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.820824
2012-07-13 21:36:45,563 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.945202
2012-07-13 21:36:46,065 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.044705
2012-07-13 21:36:46,566 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.128660
2012-07-13 21:36:47,068 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.203287
2012-07-13 21:36:47,569 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.271695
2012-07-13 21:36:48,070 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.340103
2012-07-13 21:36:48,571 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.445824
2012-07-13 21:36:49,073 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.545327
2012-07-13 21:36:49,574 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.651048
2012-07-13 21:36:50,075 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.731894
2012-07-13 21:36:50,576 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.843835
2012-07-13 21:36:51,078 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.946447
2012-07-13 21:36:51,579 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.061496
2012-07-13 21:36:52,080 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.213860
2012-07-13 21:36:52,581 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.316472
2012-07-13 21:36:53,083 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.425303
2012-07-13 21:36:53,584 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.524805
2012-07-13 21:36:54,086 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.636746
2012-07-13 21:36:54,587 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.742467
2012-07-13 21:36:55,089 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.854408
2012-07-13 21:36:55,590 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.953910
2012-07-13 21:36:56,092 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.994333
2012-07-13 21:36:56,593 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.087617
2012-07-13 21:36:57,095 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.249308
2012-07-13 21:36:57,596 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.370577
2012-07-13 21:36:58,097 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.491846
2012-07-13 21:36:58,599 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.597567
2012-07-13 21:36:59,100 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.709508
2012-07-13 21:36:59,602 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.815229
2012-07-13 21:37:00,103 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.920951
2012-07-13 21:37:00,605 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.023563
2012-07-13 21:37:01,106 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.095080
2012-07-13 21:37:01,608 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.241224
2012-07-13 21:37:02,109 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.284757
2012-07-13 21:37:02,610 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.455777
2012-07-13 21:37:03,111 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.558389
2012-07-13 21:37:03,613 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.651673
2012-07-13 21:37:04,114 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.776051
2012-07-13 21:37:04,616 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.884882
2012-07-13 21:37:05,117 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.990603
2012-07-13 21:37:05,618 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.062121
2012-07-13 21:37:06,120 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.205156
2012-07-13 21:37:06,621 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.310877
2012-07-13 21:37:07,123 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.419708
2012-07-13 21:37:07,624 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.500554
2012-07-13 21:37:08,125 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.603166
2012-07-13 21:37:08,627 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.708887
2012-07-13 21:37:09,128 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.799061
2012-07-13 21:37:09,629 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.914111
2012-07-13 21:37:10,130 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.032271
2012-07-13 21:37:10,632 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.144211
2012-07-13 21:37:11,133 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.240604
2012-07-13 21:37:11,635 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.343216
2012-07-13 21:37:12,136 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.445828
2012-07-13 21:37:12,637 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.483142
2012-07-13 21:37:13,139 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.483142
2012-07-13 21:37:13,640 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.747445
2012-07-13 21:37:14,142 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.828291
2012-07-13 21:37:14,643 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.946450
2012-07-13 21:37:15,144 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.036625
2012-07-13 21:37:15,646 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.129908
2012-07-13 21:37:16,147 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.167222
2012-07-13 21:37:16,648 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.328913
2012-07-13 21:37:17,150 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.437744
2012-07-13 21:37:17,651 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.559013
2012-07-13 21:37:18,152 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.636749
2012-07-13 21:37:18,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.714486
2012-07-13 21:37:19,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.795332
2012-07-13 21:37:19,655 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.879287
2012-07-13 21:37:20,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.969461
2012-07-13 21:37:20,658 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.062745
2012-07-13 21:37:21,160 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.230655
2012-07-13 21:37:21,661 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.311501
2012-07-13 21:37:22,162 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.355034
2012-07-13 21:37:22,664 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.541601
2012-07-13 21:37:23,165 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.669089
2012-07-13 21:37:23,666 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.768591
2012-07-13 21:37:24,168 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.883641
2012-07-13 21:37:24,669 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.986253
2012-07-13 21:37:25,171 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.101303
2012-07-13 21:37:25,672 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.207024
2012-07-13 21:37:26,173 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.315855
2012-07-13 21:37:26,675 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.421577
2012-07-13 21:37:27,176 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.521079
2012-07-13 21:37:27,678 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.636129
2012-07-13 21:37:28,179 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.657895
2012-07-13 21:37:28,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.853791
2012-07-13 21:37:29,182 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.962622
2012-07-13 21:37:29,683 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.996826
2012-07-13 21:37:30,185 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.161627
2012-07-13 21:37:30,686 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.258020
2012-07-13 21:37:31,188 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.388617
2012-07-13 21:37:31,689 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.481901
2012-07-13 21:37:32,190 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.578294
2012-07-13 21:37:32,692 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.702672
2012-07-13 21:37:33,193 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.820831
2012-07-13 21:37:33,695 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.926553
2012-07-13 21:37:34,196 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.032274
2012-07-13 21:37:34,698 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.137996
2012-07-13 21:37:35,199 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.215732
2012-07-13 21:37:35,701 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.299688
2012-07-13 21:37:36,202 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.464489
2012-07-13 21:37:36,703 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.573320
2012-07-13 21:37:37,205 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.629290
2012-07-13 21:37:37,706 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.781653
2012-07-13 21:37:38,208 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.890484
2012-07-13 21:37:38,709 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.002424
2012-07-13 21:37:39,211 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.111255
2012-07-13 21:37:39,712 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.216977
2012-07-13 21:37:40,214 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.325808
2012-07-13 21:37:40,715 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.434639
2012-07-13 21:37:41,216 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.540360
2012-07-13 21:37:41,718 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.649191
2012-07-13 21:37:42,219 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.745584
2012-07-13 21:37:42,721 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.773569
2012-07-13 21:37:43,222 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.969465
2012-07-13 21:37:43,723 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.068967
2012-07-13 21:37:44,225 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.187127
2012-07-13 21:37:44,726 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.292848
2012-07-13 21:37:45,227 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.339490
2012-07-13 21:37:45,728 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.435883
2012-07-13 21:37:46,230 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.610013
2012-07-13 21:37:46,731 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.721953
2012-07-13 21:37:47,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.833893
2012-07-13 21:37:47,734 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.908520
2012-07-13 21:37:48,236 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.039117
2012-07-13 21:37:48,737 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.141729
2012-07-13 21:37:49,238 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.253670
2012-07-13 21:37:49,740 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.362501
2012-07-13 21:37:50,241 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.474441
2012-07-13 21:37:50,742 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.573944
2012-07-13 21:37:51,244 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.661008
2012-07-13 21:37:51,745 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.772949
2012-07-13 21:37:52,246 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.782277
2012-07-13 21:37:52,747 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.925312
2012-07-13 21:37:53,248 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.018596
2012-07-13 21:37:53,749 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.024815
2012-07-13 21:37:54,250 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.180287
2012-07-13 21:37:54,751 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.273571
2012-07-13 21:37:55,252 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.388621
2012-07-13 21:37:55,754 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.475686
2012-07-13 21:37:56,255 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.581407
2012-07-13 21:37:56,756 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.665362
2012-07-13 21:37:57,259 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.771084
2012-07-13 21:37:57,761 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.867477
2012-07-13 21:37:58,262 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.985636
2012-07-13 21:37:58,763 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.094467
2012-07-13 21:37:59,264 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.184641
2012-07-13 21:37:59,766 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.262378
2012-07-13 21:38:00,267 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.402303
2012-07-13 21:38:00,768 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.517353
2012-07-13 21:38:01,270 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.629294
2012-07-13 21:38:01,771 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.700811
2012-07-13 21:38:02,272 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.778547
2012-07-13 21:38:02,774 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.952677
2012-07-13 21:38:03,275 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.045960
2012-07-13 21:38:03,776 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.151682
2012-07-13 21:38:04,277 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.276060
2012-07-13 21:38:04,778 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.378672
2012-07-13 21:38:05,280 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.484394
2012-07-13 21:38:05,781 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.593225
2012-07-13 21:38:06,283 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.702056
2012-07-13 21:38:06,784 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.807777
2012-07-13 21:38:07,285 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.919717
2012-07-13 21:38:07,787 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.947702
2012-07-13 21:38:08,288 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.124941
2012-07-13 21:38:08,790 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.236882
2012-07-13 21:38:09,291 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.339494
2012-07-13 21:38:09,793 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.457653
2012-07-13 21:38:10,295 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.473200
2012-07-13 21:38:10,796 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.669096
2012-07-13 21:38:11,297 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.768599
2012-07-13 21:38:11,798 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.874320
2012-07-13 21:38:12,299 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.989370
2012-07-13 21:38:12,801 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.076435
2012-07-13 21:38:13,302 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.188375
2012-07-13 21:38:13,803 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.312753
2012-07-13 21:38:14,305 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.421584
2012-07-13 21:38:14,806 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.524196
2012-07-13 21:38:15,307 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.636137
2012-07-13 21:38:15,809 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.720092
2012-07-13 21:38:16,310 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.828923
2012-07-13 21:38:16,812 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.925316
2012-07-13 21:38:17,313 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.043475
2012-07-13 21:38:17,814 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.158525
2012-07-13 21:38:18,315 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.264247
2012-07-13 21:38:18,817 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.351311
2012-07-13 21:38:19,318 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.478799
2012-07-13 21:38:19,819 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.584520
2012-07-13 21:38:20,320 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.693351
2012-07-13 21:38:20,822 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.802182
2012-07-13 21:38:21,323 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.907904
2012-07-13 21:38:21,825 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.016735
2012-07-13 21:38:22,326 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.078924
2012-07-13 21:38:22,828 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.097580
2012-07-13 21:38:23,329 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.287257
2012-07-13 21:38:23,831 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.386760
2012-07-13 21:38:24,332 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.492481
2012-07-13 21:38:24,834 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.585765
2012-07-13 21:38:25,335 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.585765
2012-07-13 21:38:25,836 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.766113
2012-07-13 21:38:26,338 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.865616
2012-07-13 21:38:26,840 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.881163
2012-07-13 21:38:27,341 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.098825
2012-07-13 21:38:27,842 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.204546
2012-07-13 21:38:28,344 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.313377
2012-07-13 21:38:28,845 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.419099
2012-07-13 21:38:29,347 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.512383
2012-07-13 21:38:29,848 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.630542
2012-07-13 21:38:30,350 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.733154
2012-07-13 21:38:30,851 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.835766
2012-07-13 21:38:31,352 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.925940
2012-07-13 21:38:31,854 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.028552
2012-07-13 21:38:32,355 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.124945
2012-07-13 21:38:32,857 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.218229
2012-07-13 21:38:33,358 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.305294
2012-07-13 21:38:33,860 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.401687
2012-07-13 21:38:34,361 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.482533
2012-07-13 21:38:34,862 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.482533
2012-07-13 21:38:35,364 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.541612
2012-07-13 21:38:35,865 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.675319
2012-07-13 21:38:36,366 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.700194
2012-07-13 21:38:36,868 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.927185
2012-07-13 21:38:37,370 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.017359
2012-07-13 21:38:37,871 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.107533
2012-07-13 21:38:38,372 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.194598
2012-07-13 21:38:38,874 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.287881
2012-07-13 21:38:39,375 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.384274
2012-07-13 21:38:39,877 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.486887
2012-07-13 21:38:40,378 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.595717
2012-07-13 21:38:40,880 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.679673
2012-07-13 21:38:41,381 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.779175
2012-07-13 21:38:41,884 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.863131
2012-07-13 21:38:42,385 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.959524
2012-07-13 21:38:42,886 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.040370
2012-07-13 21:38:43,388 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.040370
2012-07-13 21:38:43,889 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.149200
2012-07-13 21:38:44,391 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.301564
2012-07-13 21:38:44,892 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.360643
2012-07-13 21:38:45,393 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.369972
2012-07-13 21:38:45,895 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.522335
2012-07-13 21:38:46,397 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.618728
2012-07-13 21:38:46,898 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.696465
2012-07-13 21:38:47,400 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.799077
2012-07-13 21:38:47,901 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.876813
2012-07-13 21:38:48,403 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.960768
2012-07-13 21:38:48,904 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.035395
2012-07-13 21:38:49,405 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.100694
2012-07-13 21:38:49,907 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.169102
2012-07-13 21:38:50,408 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.231291
2012-07-13 21:38:50,910 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.290370
2012-07-13 21:38:51,411 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.290370
2012-07-13 21:38:51,913 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.514251
2012-07-13 21:38:52,414 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.545346
2012-07-13 21:38:52,915 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.679052
2012-07-13 21:38:53,416 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.809649
2012-07-13 21:38:53,918 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.915371
2012-07-13 21:38:54,419 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.989998
2012-07-13 21:38:54,921 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.086391
2012-07-13 21:38:55,422 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.232535
2012-07-13 21:38:55,923 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.328928
2012-07-13 21:38:56,425 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.425322
2012-07-13 21:38:56,926 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.524824
2012-07-13 21:38:57,427 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.627436
2012-07-13 21:38:57,929 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.733158
2012-07-13 21:38:58,430 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.841989
2012-07-13 21:38:58,932 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.947710
2012-07-13 21:38:59,433 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.056541
2012-07-13 21:38:59,935 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.165372
2012-07-13 21:39:00,436 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.277312
2012-07-13 21:39:00,937 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.355049
2012-07-13 21:39:01,438 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.423457
2012-07-13 21:39:01,940 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.594477
2012-07-13 21:39:02,441 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.693979
2012-07-13 21:39:02,943 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.728183
2012-07-13 21:39:03,444 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.920969
2012-07-13 21:39:03,945 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.029800
2012-07-13 21:39:04,447 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.132412
2012-07-13 21:39:04,948 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.235024
2012-07-13 21:39:05,450 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.340746
2012-07-13 21:39:05,951 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.437139
2012-07-13 21:39:06,453 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.539751
2012-07-13 21:39:06,954 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.667239
2012-07-13 21:39:07,456 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.782289
2012-07-13 21:39:07,957 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.878682
2012-07-13 21:39:08,458 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.993731
2012-07-13 21:39:08,960 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.077687
2012-07-13 21:39:09,461 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.198955
2012-07-13 21:39:09,962 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.307786
2012-07-13 21:39:10,464 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.407289
2012-07-13 21:39:10,967 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.528558
2012-07-13 21:39:11,469 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.637389
2012-07-13 21:39:11,969 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.684030
2012-07-13 21:39:12,470 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.836394
2012-07-13 21:39:12,971 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.901692
2012-07-13 21:39:13,472 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.985648
2012-07-13 21:39:13,973 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.106916
2012-07-13 21:39:14,474 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.206419
2012-07-13 21:39:14,976 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.312140
2012-07-13 21:39:15,477 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.417862
2012-07-13 21:39:15,979 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.508036
2012-07-13 21:39:16,480 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.623086
2012-07-13 21:39:16,981 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.731917
2012-07-13 21:39:17,483 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.818982
2012-07-13 21:39:17,984 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.902937
2012-07-13 21:39:18,486 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.999330
2012-07-13 21:39:18,986 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.083285
2012-07-13 21:39:19,487 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.198335
2012-07-13 21:39:19,989 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.310275
2012-07-13 21:39:20,490 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.403559
2012-07-13 21:39:20,991 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.481296
2012-07-13 21:39:21,493 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.593236
2012-07-13 21:39:21,994 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.689629
2012-07-13 21:39:22,495 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.726942
2012-07-13 21:39:22,996 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.894853
2012-07-13 21:39:23,497 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.894853
2012-07-13 21:39:23,998 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.059654
2012-07-13 21:39:24,499 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.124953
2012-07-13 21:39:25,001 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.246221
2012-07-13 21:39:25,502 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.336396
2012-07-13 21:39:26,003 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.432789
2012-07-13 21:39:26,504 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.532291
2012-07-13 21:39:27,005 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.634903
2012-07-13 21:39:27,507 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.734406
2012-07-13 21:39:28,008 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.846346
2012-07-13 21:39:28,510 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.896098
2012-07-13 21:39:29,011 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.064008
2012-07-13 21:39:29,526 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.175949
2012-07-13 21:39:30,027 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.250575
2012-07-13 21:39:30,529 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.381173
2012-07-13 21:39:31,030 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.483785
2012-07-13 21:39:31,532 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.589506
2012-07-13 21:39:32,033 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.673461
2012-07-13 21:39:32,535 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.772964
2012-07-13 21:39:33,036 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.875576
2012-07-13 21:39:33,538 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.981297
2012-07-13 21:39:34,039 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.090128
2012-07-13 21:39:34,540 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.198959
2012-07-13 21:39:35,041 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.304681
2012-07-13 21:39:35,543 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.416621
2012-07-13 21:39:36,044 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.519233
2012-07-13 21:39:36,546 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.596970
2012-07-13 21:39:37,047 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.690253
2012-07-13 21:39:37,549 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.845726
2012-07-13 21:39:38,050 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.954557
2012-07-13 21:39:38,551 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.985651
2012-07-13 21:39:39,052 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.138015
2012-07-13 21:39:39,554 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.215751
2012-07-13 21:39:40,054 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.277940
2012-07-13 21:39:40,556 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.337020
2012-07-13 21:39:41,057 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.420975
2012-07-13 21:39:41,558 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.492493
2012-07-13 21:39:42,058 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.539134
2012-07-13 21:39:42,559 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.573338
2012-07-13 21:39:43,060 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.573338
2012-07-13 21:39:43,561 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.613761
2012-07-13 21:39:44,062 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.616871
2012-07-13 21:39:44,564 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.672841
2012-07-13 21:39:45,068 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.697717
2012-07-13 21:39:45,569 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.710154
2012-07-13 21:39:46,070 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.741249
2012-07-13 21:39:46,571 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.772344
2012-07-13 21:39:47,072 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.791000
2012-07-13 21:39:47,573 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.791000
2012-07-13 21:39:48,074 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.797219
2012-07-13 21:39:48,575 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.812766
2012-07-13 21:39:49,077 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.840752
2012-07-13 21:39:49,578 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.871846
2012-07-13 21:39:50,080 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.909160
2012-07-13 21:39:50,581 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.937145
2012-07-13 21:39:51,082 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.965130
2012-07-13 21:39:51,583 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.008662
2012-07-13 21:39:52,085 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.042866
2012-07-13 21:39:52,585 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.042866
2012-07-13 21:39:53,086 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.045976
2012-07-13 21:39:53,587 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.061523
2012-07-13 21:39:54,088 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.070851
2012-07-13 21:39:54,590 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.095727
2012-07-13 21:39:55,091 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.123712
2012-07-13 21:39:55,592 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.154807
2012-07-13 21:39:56,094 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.176573
2012-07-13 21:39:56,594 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.220105
2012-07-13 21:39:57,096 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.260528
2012-07-13 21:39:57,597 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.322717
2012-07-13 21:39:58,099 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.412891
2012-07-13 21:39:58,600 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.487518
2012-07-13 21:39:59,101 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.562145
2012-07-13 21:39:59,603 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.633663
2012-07-13 21:40:00,104 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.702071
2012-07-13 21:40:00,605 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.801573
2012-07-13 21:40:01,106 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.888638
2012-07-13 21:40:01,608 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.988140
2012-07-13 21:40:02,109 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.093862
2012-07-13 21:40:02,610 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.202693
2012-07-13 21:40:03,111 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.311524
2012-07-13 21:40:03,613 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.389260
2012-07-13 21:40:04,114 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.476325
2012-07-13 21:40:04,615 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.634907
2012-07-13 21:40:05,117 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.740629
2012-07-13 21:40:05,618 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.796599
2012-07-13 21:40:06,120 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.955181
2012-07-13 21:40:06,621 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.060902
2012-07-13 21:40:07,122 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.172843
2012-07-13 21:40:07,624 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.278564
2012-07-13 21:40:08,125 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.387395
2012-07-13 21:40:08,627 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.493117
2012-07-13 21:40:09,128 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.601948
2012-07-13 21:40:09,630 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.710779
2012-07-13 21:40:10,131 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.816500
2012-07-13 21:40:10,632 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.925331
2012-07-13 21:40:11,134 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.940878
2012-07-13 21:40:11,635 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.136774
2012-07-13 21:40:12,137 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.248714
2012-07-13 21:40:12,638 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.357545
2012-07-13 21:40:13,140 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.419734
2012-07-13 21:40:13,641 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.497471
2012-07-13 21:40:14,143 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.668491
2012-07-13 21:40:14,644 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.777322
2012-07-13 21:40:15,146 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.879934
2012-07-13 21:40:15,647 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.966998
2012-07-13 21:40:16,148 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.075829
2012-07-13 21:40:16,650 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.209536
2012-07-13 21:40:17,151 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.321476
2012-07-13 21:40:17,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.427198
2012-07-13 21:40:18,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.536029
2012-07-13 21:40:18,656 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.591999
2012-07-13 21:40:19,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.688392
2012-07-13 21:40:19,658 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.859412
2012-07-13 21:40:20,160 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.965134
2012-07-13 21:40:20,661 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.064636
2012-07-13 21:40:21,162 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.136154
2012-07-13 21:40:21,664 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.282298
2012-07-13 21:40:22,165 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.384910
2012-07-13 21:40:22,667 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.450209
2012-07-13 21:40:23,168 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.524835
2012-07-13 21:40:23,669 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.618119
2012-07-13 21:40:24,171 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.708293
2012-07-13 21:40:24,672 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.770482
2012-07-13 21:40:25,174 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.857547
2012-07-13 21:40:25,675 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.938393
2012-07-13 21:40:26,176 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.991254
2012-07-13 21:40:26,678 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.115632
2012-07-13 21:40:27,179 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.208916
2012-07-13 21:40:27,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.308418
2012-07-13 21:40:28,182 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.386154
2012-07-13 21:40:28,683 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.476329
2012-07-13 21:40:29,184 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.557175
2012-07-13 21:40:29,686 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.641130
2012-07-13 21:40:30,186 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.737523
2012-07-13 21:40:30,687 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.840135
2012-07-13 21:40:31,189 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.936528
2012-07-13 21:40:31,690 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.045359
2012-07-13 21:40:32,192 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.138643
2012-07-13 21:40:32,693 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.231926
2012-07-13 21:40:33,195 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.315882
2012-07-13 21:40:33,696 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.340757
2012-07-13 21:40:34,197 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.434041
2012-07-13 21:40:34,699 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.623718
2012-07-13 21:40:35,200 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.779190
2012-07-13 21:40:35,702 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.794738
2012-07-13 21:40:36,203 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.950210
2012-07-13 21:40:36,705 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.099464
2012-07-13 21:40:37,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.205186
2012-07-13 21:40:37,708 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.310907
2012-07-13 21:40:38,209 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.404191
2012-07-13 21:40:38,710 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.494365
2012-07-13 21:40:39,212 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.600087
2012-07-13 21:40:39,714 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.736903
2012-07-13 21:40:40,215 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.845733
2012-07-13 21:40:40,716 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.954564
2012-07-13 21:40:41,218 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.060286
2012-07-13 21:40:41,719 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.094490
2012-07-13 21:40:42,220 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.271729
2012-07-13 21:40:42,722 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.383669
2012-07-13 21:40:43,223 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.492500
2012-07-13 21:40:43,724 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.598222
2012-07-13 21:40:44,225 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.598222
2012-07-13 21:40:44,727 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.781679
2012-07-13 21:40:45,228 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.868744
2012-07-13 21:40:45,729 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.918495
2012-07-13 21:40:46,231 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.080187
2012-07-13 21:40:46,732 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.179690
2012-07-13 21:40:47,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.282302
2012-07-13 21:40:47,735 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.406680
2012-07-13 21:40:48,238 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.521730
2012-07-13 21:40:48,738 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.627451
2012-07-13 21:40:49,240 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.739392
2012-07-13 21:40:49,741 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.845113
2012-07-13 21:40:50,243 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.953944
2012-07-13 21:40:50,744 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.059665
2012-07-13 21:40:51,245 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.165387
2012-07-13 21:40:51,747 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.221357
2012-07-13 21:40:52,248 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.386158
2012-07-13 21:40:52,750 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.491880
2012-07-13 21:40:53,259 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.597601
2012-07-13 21:40:53,760 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.706432
2012-07-13 21:40:54,261 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.753074
2012-07-13 21:40:54,762 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.924094
2012-07-13 21:40:55,263 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.032925
2012-07-13 21:40:55,765 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.138646
2012-07-13 21:40:56,266 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.247477
2012-07-13 21:40:56,767 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.303448
2012-07-13 21:40:57,268 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.462030
2012-07-13 21:40:57,769 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.570861
2012-07-13 21:40:58,271 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.676582
2012-07-13 21:40:58,772 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.785413
2012-07-13 21:40:59,273 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.810289
2012-07-13 21:40:59,774 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.999965
2012-07-13 21:41:00,276 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.108796
2012-07-13 21:41:00,777 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.214518
2012-07-13 21:41:01,278 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.323349
2012-07-13 21:41:01,780 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.429070
2012-07-13 21:41:02,281 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.537901
2012-07-13 21:41:02,782 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.646732
2012-07-13 21:41:03,284 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.752454
2012-07-13 21:41:03,785 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.858175
2012-07-13 21:41:04,286 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.954568
2012-07-13 21:41:04,788 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.029195
2012-07-13 21:41:05,289 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.181558
2012-07-13 21:41:05,791 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.290389
2012-07-13 21:41:06,292 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.399220
2012-07-13 21:41:06,793 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.448972
2012-07-13 21:41:07,294 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.607554
2012-07-13 21:41:07,796 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.719494
2012-07-13 21:41:08,297 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.822106
2012-07-13 21:41:08,798 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.924718
2012-07-13 21:41:09,299 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.024221
2012-07-13 21:41:09,801 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.142380
2012-07-13 21:41:10,302 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.248101
2012-07-13 21:41:10,804 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.347604
2012-07-13 21:41:11,305 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.419121
2012-07-13 21:41:11,806 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.571485
2012-07-13 21:41:12,308 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.655440
2012-07-13 21:41:12,809 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.742505
2012-07-13 21:41:13,310 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.891759
2012-07-13 21:41:13,811 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.000590
2012-07-13 21:41:14,313 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.068998
2012-07-13 21:41:14,814 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.146734
2012-07-13 21:41:15,315 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.274222
2012-07-13 21:41:15,816 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.311535
2012-07-13 21:41:16,317 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.361286
2012-07-13 21:41:16,818 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.470117
2012-07-13 21:41:17,320 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.560292
2012-07-13 21:41:17,821 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.631809
2012-07-13 21:41:18,323 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.718874
2012-07-13 21:41:18,824 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.805938
2012-07-13 21:41:19,325 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.883675
2012-07-13 21:41:19,827 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.976958
2012-07-13 21:41:20,328 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.079571
2012-07-13 21:41:20,830 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.188401
2012-07-13 21:41:21,331 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.315889
2012-07-13 21:41:21,833 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.424720
2012-07-13 21:41:22,334 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.452705
2012-07-13 21:41:22,836 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.642382
2012-07-13 21:41:23,337 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.751213
2012-07-13 21:41:23,839 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.791636
2012-07-13 21:41:24,340 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.962656
2012-07-13 21:41:24,841 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.068377
2012-07-13 21:41:25,343 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.177208
2012-07-13 21:41:25,844 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.273601
2012-07-13 21:41:26,346 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.391761
2012-07-13 21:41:26,847 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.497482
2012-07-13 21:41:27,349 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.612532
2012-07-13 21:41:27,850 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.718253
2012-07-13 21:41:28,351 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.820865
2012-07-13 21:41:28,853 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.935915
2012-07-13 21:41:29,354 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.951462
2012-07-13 21:41:29,856 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.147358
2012-07-13 21:41:30,357 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.249970
2012-07-13 21:41:30,859 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.365020
2012-07-13 21:41:31,360 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.464523
2012-07-13 21:41:31,862 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.542259
2012-07-13 21:41:32,363 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.672856
2012-07-13 21:41:32,865 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.791015
2012-07-13 21:41:33,367 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.815891
2012-07-13 21:41:33,867 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.921612
2012-07-13 21:41:34,369 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.039772
2012-07-13 21:41:34,870 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.142384
2012-07-13 21:41:35,370 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.198354
2012-07-13 21:41:35,872 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.297857
2012-07-13 21:41:36,373 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.403578
2012-07-13 21:41:36,874 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.499971
2012-07-13 21:41:37,375 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.596364
2012-07-13 21:41:37,877 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.689648
2012-07-13 21:41:38,378 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.782932
2012-07-13 21:41:38,879 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.866887
2012-07-13 21:41:39,383 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.969499
2012-07-13 21:41:39,884 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.093877
2012-07-13 21:41:40,385 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.199598
2012-07-13 21:41:40,886 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.305320
2012-07-13 21:41:41,387 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.379947
2012-07-13 21:41:41,888 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.379947
2012-07-13 21:41:42,390 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.550967
2012-07-13 21:41:42,891 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.638032
2012-07-13 21:41:43,393 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.721987
2012-07-13 21:41:43,894 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.821490
2012-07-13 21:41:44,395 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.908554
2012-07-13 21:41:44,897 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.011166
2012-07-13 21:41:45,398 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.104450
2012-07-13 21:41:45,899 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.141763
2012-07-13 21:41:46,400 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.287908
2012-07-13 21:41:46,901 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.371863
2012-07-13 21:41:47,402 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.471366
2012-07-13 21:41:47,904 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.570868
2012-07-13 21:41:48,405 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.682809
2012-07-13 21:41:48,907 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.791639
2012-07-13 21:41:49,408 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.925346
2012-07-13 21:41:49,909 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.027958
2012-07-13 21:41:50,411 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.127461
2012-07-13 21:41:50,912 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.230073
2012-07-13 21:41:51,414 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.314028
2012-07-13 21:41:51,914 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.419749
2012-07-13 21:41:52,416 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.435297
2012-07-13 21:41:52,917 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.646740
2012-07-13 21:41:53,418 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.764899
2012-07-13 21:41:53,920 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.867511
2012-07-13 21:41:54,425 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.960795
2012-07-13 21:41:54,926 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.072735
2012-07-13 21:41:55,427 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.169128
2012-07-13 21:41:55,928 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.284178
2012-07-13 21:41:56,430 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.374352
2012-07-13 21:41:56,931 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.467636
2012-07-13 21:41:57,432 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.570248
2012-07-13 21:41:57,933 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.672860
2012-07-13 21:41:58,438 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.769253
2012-07-13 21:41:58,939 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.884303
2012-07-13 21:41:59,440 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.896741
2012-07-13 21:41:59,942 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.080198
2012-07-13 21:42:00,442 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.173482
2012-07-13 21:42:00,944 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.285422
2012-07-13 21:42:01,445 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.391144
2012-07-13 21:42:01,946 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.490647
2012-07-13 21:42:02,447 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.583930
2012-07-13 21:42:02,948 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.646119
2012-07-13 21:42:03,449 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.680323
2012-07-13 21:42:03,951 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.876219
2012-07-13 21:42:04,452 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.981940
2012-07-13 21:42:04,954 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.103209
2012-07-13 21:42:05,455 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.193383
2012-07-13 21:42:05,956 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.277339
2012-07-13 21:42:06,457 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.361294
2012-07-13 21:42:06,958 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.435921
2012-07-13 21:42:07,459 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.519876
2012-07-13 21:42:07,960 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.594503
2012-07-13 21:42:08,461 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.641145
2012-07-13 21:42:08,963 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.715133
2012-07-13 21:42:09,464 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.868135
2012-07-13 21:42:09,965 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.970747
2012-07-13 21:42:10,466 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.042265
2012-07-13 21:42:10,968 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.054702
2012-07-13 21:42:11,469 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.154205
2012-07-13 21:42:11,970 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.238160
2012-07-13 21:42:12,472 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.350101
2012-07-13 21:42:12,973 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.415399
2012-07-13 21:42:13,474 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.474479
2012-07-13 21:42:13,976 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.552215
2012-07-13 21:42:14,477 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.605076
2012-07-13 21:42:14,979 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.608185
2012-07-13 21:42:15,480 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.738783
2012-07-13 21:42:15,981 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.813409
2012-07-13 21:42:16,483 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.888036
2012-07-13 21:42:16,984 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.975101
2012-07-13 21:42:17,485 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.062166
2012-07-13 21:42:17,987 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.130574
2012-07-13 21:42:18,488 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.226967
2012-07-13 21:42:18,989 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.307813
2012-07-13 21:42:19,491 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.413534
2012-07-13 21:42:19,992 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.447738
2012-07-13 21:42:20,493 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.584554
2012-07-13 21:42:20,995 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.665400
2012-07-13 21:42:21,496 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.746246
2012-07-13 21:42:21,997 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.820873
2012-07-13 21:42:22,499 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.901719
2012-07-13 21:42:23,000 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.986929
2012-07-13 21:42:23,501 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.078958
2012-07-13 21:42:24,003 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.178460
2012-07-13 21:42:24,504 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.277963
2012-07-13 21:42:25,006 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.389903
2012-07-13 21:42:25,507 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.483187
2012-07-13 21:42:26,009 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.585799
2012-07-13 21:42:26,510 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.697739
2012-07-13 21:42:27,011 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.797242
2012-07-13 21:42:27,513 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.896744
2012-07-13 21:42:28,014 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.990028
2012-07-13 21:42:28,516 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.098859
2012-07-13 21:42:29,017 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.207690
2012-07-13 21:42:29,518 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.313411
2012-07-13 21:42:30,020 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.419133
2012-07-13 21:42:30,521 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.509307
2012-07-13 21:42:31,023 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.624357
2012-07-13 21:42:31,524 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.717640
2012-07-13 21:42:32,025 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.810924
2012-07-13 21:42:32,527 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.894879
2012-07-13 21:42:33,028 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.975725
2012-07-13 21:42:33,530 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.997491
2012-07-13 21:42:34,031 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.124979
2012-07-13 21:42:34,532 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.202715
2012-07-13 21:42:35,033 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.261795
2012-07-13 21:42:35,534 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.355079
2012-07-13 21:42:36,036 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.435925
2012-07-13 21:42:36,537 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.498114
2012-07-13 21:42:37,038 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.585178
2012-07-13 21:42:37,539 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.666024
2012-07-13 21:42:38,040 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.753089
2012-07-13 21:42:38,541 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.830825
2012-07-13 21:42:39,042 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.927219
2012-07-13 21:42:39,543 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.020502
2012-07-13 21:42:40,044 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.101348
2012-07-13 21:42:40,545 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.200851
2012-07-13 21:42:41,047 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.309681
2012-07-13 21:42:41,548 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.418512
2012-07-13 21:42:42,050 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.518015
2012-07-13 21:42:42,551 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.620627
2012-07-13 21:42:43,053 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.735677
2012-07-13 21:42:43,554 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.847617
2012-07-13 21:42:44,055 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.853836
2012-07-13 21:42:44,557 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.062170
2012-07-13 21:42:45,058 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.158563
2012-07-13 21:42:45,560 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.242518
2012-07-13 21:42:46,061 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.329583
2012-07-13 21:42:46,563 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.407319
2012-07-13 21:42:47,064 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.494384
2012-07-13 21:42:47,565 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.494384
2012-07-13 21:42:48,067 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.740031
2012-07-13 21:42:48,568 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.855081
2012-07-13 21:42:49,069 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.973240
2012-07-13 21:42:49,571 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.103837
2012-07-13 21:42:50,072 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.103837
2012-07-13 21:42:50,574 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.293514
2012-07-13 21:42:51,075 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.393016
2012-07-13 21:42:51,576 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.480081
2012-07-13 21:42:52,078 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.517395
2012-07-13 21:42:52,580 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.679086
2012-07-13 21:42:53,081 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.794136
2012-07-13 21:42:53,583 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.896748
2012-07-13 21:42:54,084 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.011798
2012-07-13 21:42:54,585 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.136176
2012-07-13 21:42:55,087 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.257445
2012-07-13 21:42:55,588 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.363166
2012-07-13 21:42:56,090 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.471997
2012-07-13 21:42:56,591 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.580828
2012-07-13 21:42:57,092 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.627470
2012-07-13 21:42:57,593 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.789162
2012-07-13 21:42:58,095 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.901102
2012-07-13 21:42:58,596 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.994386
2012-07-13 21:42:59,097 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.115655
2012-07-13 21:42:59,599 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.227595
2012-07-13 21:43:00,100 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.249361
2012-07-13 21:43:00,601 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.432819
2012-07-13 21:43:01,102 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.544759
2012-07-13 21:43:01,604 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.641152
2012-07-13 21:43:02,105 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.756202
2012-07-13 21:43:02,606 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.865033
2012-07-13 21:43:03,108 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.902347
2012-07-13 21:43:03,609 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.082695
2012-07-13 21:43:04,110 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.194635
2012-07-13 21:43:04,612 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.297247
2012-07-13 21:43:05,113 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.381203
2012-07-13 21:43:05,614 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.514909
2012-07-13 21:43:06,115 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.620631
2012-07-13 21:43:06,616 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.732571
2012-07-13 21:43:07,118 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.838293
2012-07-13 21:43:07,619 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.853840
2012-07-13 21:43:08,121 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.055954
2012-07-13 21:43:08,622 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.161676
2012-07-13 21:43:09,123 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.270507
2012-07-13 21:43:09,625 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.376228
2012-07-13 21:43:10,126 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.416651
2012-07-13 21:43:10,628 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.593890
2012-07-13 21:43:11,129 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.693393
2012-07-13 21:43:11,630 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.805333
2012-07-13 21:43:12,132 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.914164
2012-07-13 21:43:12,633 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.985682
2012-07-13 21:43:13,135 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.131826
2012-07-13 21:43:13,636 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.237547
2012-07-13 21:43:14,137 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.346378
2012-07-13 21:43:14,639 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.452100
2012-07-13 21:43:15,140 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.554712
2012-07-13 21:43:15,641 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.666652
2012-07-13 21:43:16,143 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.775483
2012-07-13 21:43:16,644 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.884314
2012-07-13 21:43:17,145 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.986926
2012-07-13 21:43:17,647 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.024240
2012-07-13 21:43:18,148 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.204588
2012-07-13 21:43:18,650 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.313419
2012-07-13 21:43:19,152 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.422250
2012-07-13 21:43:19,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.531081
2012-07-13 21:43:20,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.630583
2012-07-13 21:43:20,656 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.742524
2012-07-13 21:43:21,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.845136
2012-07-13 21:43:21,659 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.947748
2012-07-13 21:43:22,160 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.059688
2012-07-13 21:43:22,662 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.171628
2012-07-13 21:43:23,164 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.199614
2012-07-13 21:43:23,665 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.389290
2012-07-13 21:43:24,167 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.488793
2012-07-13 21:43:24,668 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.603843
2012-07-13 21:43:25,169 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.709564
2012-07-13 21:43:25,671 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.815286
2012-07-13 21:43:26,172 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.927226
2012-07-13 21:43:26,674 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.029838
2012-07-13 21:43:27,175 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.135560
2012-07-13 21:43:27,676 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.244390
2012-07-13 21:43:28,178 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.291032
2012-07-13 21:43:28,679 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.449615
2012-07-13 21:43:29,181 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.573993
2012-07-13 21:43:29,682 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.670386
2012-07-13 21:43:30,184 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.766779
2012-07-13 21:43:30,685 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.875610
2012-07-13 21:43:31,186 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.996879
2012-07-13 21:43:31,688 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.111928
2012-07-13 21:43:32,189 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.124366
2012-07-13 21:43:32,691 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.323371
2012-07-13 21:43:33,192 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.357575
2012-07-13 21:43:33,693 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.534814
2012-07-13 21:43:34,195 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.643645
2012-07-13 21:43:34,696 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.755586
2012-07-13 21:43:35,198 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.858198
2012-07-13 21:43:35,698 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.967029
2012-07-13 21:43:36,200 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.075860
2012-07-13 21:43:36,700 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.184690
2012-07-13 21:43:37,202 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.290412
2012-07-13 21:43:37,703 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.396133
2012-07-13 21:43:38,204 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.504964
2012-07-13 21:43:38,706 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.560935
2012-07-13 21:43:39,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.719517
2012-07-13 21:43:39,709 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.828348
2012-07-13 21:43:40,210 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.937179
2012-07-13 21:43:40,712 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.033572
2012-07-13 21:43:41,213 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.086432
2012-07-13 21:43:41,714 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.257452
2012-07-13 21:43:42,215 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.366283
2012-07-13 21:43:42,717 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.475114
2012-07-13 21:43:43,219 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.580836
2012-07-13 21:43:43,720 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.689667
2012-07-13 21:43:44,222 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.798498
2012-07-13 21:43:44,723 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.894891
2012-07-13 21:43:45,225 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.013050
2012-07-13 21:43:45,726 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.121881
2012-07-13 21:43:46,228 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.224493
2012-07-13 21:43:46,729 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.336433
2012-07-13 21:43:47,230 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.442155
2012-07-13 21:43:47,732 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.550986
2012-07-13 21:43:48,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.656707
2012-07-13 21:43:48,735 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.765538
2012-07-13 21:43:49,236 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.874369
2012-07-13 21:43:49,598 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.951926
2012-07-13 21:43:49,608 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.951926
2012-07-13 21:43:50,109 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.060249
2012-07-13 21:43:50,611 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.094453
2012-07-13 21:43:51,112 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.274801
2012-07-13 21:43:51,614 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.383632
2012-07-13 21:43:52,115 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.492463
2012-07-13 21:43:52,616 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.591966
2012-07-13 21:43:53,118 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.644826
2012-07-13 21:43:53,619 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.812737
2012-07-13 21:43:54,121 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.921568
2012-07-13 21:43:54,622 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.027289
2012-07-13 21:43:55,124 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.136120
2012-07-13 21:43:55,625 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.241842
2012-07-13 21:43:56,127 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.350673
2012-07-13 21:43:56,628 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.459504
2012-07-13 21:43:57,129 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.565225
2012-07-13 21:43:57,631 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.674056
2012-07-13 21:43:58,132 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.720698
2012-07-13 21:43:58,634 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.823310
2012-07-13 21:43:59,135 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.985002
2012-07-13 21:43:59,637 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.103161
2012-07-13 21:44:00,138 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.211992
2012-07-13 21:44:00,640 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.271071
2012-07-13 21:44:01,141 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.426544
2012-07-13 21:44:01,642 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.535375
2012-07-13 21:44:02,143 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.641097
2012-07-13 21:44:02,645 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.749928
2012-07-13 21:44:03,146 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.858758
2012-07-13 21:44:03,647 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.964480
2012-07-13 21:44:04,149 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.073311
2012-07-13 21:44:04,650 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.182142
2012-07-13 21:44:05,151 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.287863
2012-07-13 21:44:05,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.390475
2012-07-13 21:44:06,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.443336
2012-07-13 21:44:06,656 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.611247
2012-07-13 21:44:07,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.716968
2012-07-13 21:44:07,658 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.825799
2012-07-13 21:44:08,159 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.891098
2012-07-13 21:44:08,661 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.040351
2012-07-13 21:44:09,162 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.149182
2012-07-13 21:44:09,664 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.254904
2012-07-13 21:44:10,165 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.363735
2012-07-13 21:44:10,666 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.472566
2012-07-13 21:44:11,167 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.578287
2012-07-13 21:44:11,669 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.687118
2012-07-13 21:44:12,170 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.792839
2012-07-13 21:44:12,672 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.845700
2012-07-13 21:44:13,173 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.982516
2012-07-13 21:44:13,674 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.078909
2012-07-13 21:44:14,175 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.187740
2012-07-13 21:44:14,677 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.290352
2012-07-13 21:44:15,178 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.386745
2012-07-13 21:44:15,679 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.489357
2012-07-13 21:44:16,180 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.595079
2012-07-13 21:44:16,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.700800
2012-07-13 21:44:17,183 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.797193
2012-07-13 21:44:17,684 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.899806
2012-07-13 21:44:18,185 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.965104
2012-07-13 21:44:18,686 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.098811
2012-07-13 21:44:19,187 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.195204
2012-07-13 21:44:19,688 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.241846
2012-07-13 21:44:20,189 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.409756
2012-07-13 21:44:20,690 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.515478
2012-07-13 21:44:21,192 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.624309
2012-07-13 21:44:21,693 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.730030
2012-07-13 21:44:22,195 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.838861
2012-07-13 21:44:22,696 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.947692
2012-07-13 21:44:23,198 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.053413
2012-07-13 21:44:23,699 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.162244
2012-07-13 21:44:24,201 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.267966
2012-07-13 21:44:24,702 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.376797
2012-07-13 21:44:25,204 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.485628
2012-07-13 21:44:25,705 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.501175
2012-07-13 21:44:26,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.700180
2012-07-13 21:44:26,708 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.809011
2012-07-13 21:44:27,209 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.914732
2012-07-13 21:44:27,711 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.945827
2012-07-13 21:44:28,212 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.129285
2012-07-13 21:44:28,713 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.238116
2012-07-13 21:44:29,214 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.346947
2012-07-13 21:44:29,716 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.452668
2012-07-13 21:44:30,217 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.558390
2012-07-13 21:44:30,718 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.667221
2012-07-13 21:44:31,220 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.776051
2012-07-13 21:44:31,721 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.884882
2012-07-13 21:44:32,222 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.990604
2012-07-13 21:44:32,723 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.093216
2012-07-13 21:44:33,224 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.133639
2012-07-13 21:44:33,726 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.313987
2012-07-13 21:44:34,226 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.419709
2012-07-13 21:44:34,728 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.528540
2012-07-13 21:44:35,229 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.590729
2012-07-13 21:44:35,730 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.743092
2012-07-13 21:44:36,232 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.848813
2012-07-13 21:44:36,733 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.957644
2012-07-13 21:44:37,235 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.066475
2012-07-13 21:44:37,736 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.172197
2012-07-13 21:44:38,238 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.281028
2012-07-13 21:44:38,739 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.389859
2012-07-13 21:44:39,240 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.495580
2012-07-13 21:44:39,741 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.604411
2012-07-13 21:44:40,242 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.710133
2012-07-13 21:44:40,743 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.735008
2012-07-13 21:44:41,245 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.927794
2012-07-13 21:44:41,746 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.033516
2012-07-13 21:44:42,246 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.142347
2012-07-13 21:44:42,747 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.248068
2012-07-13 21:44:43,249 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.269834
2012-07-13 21:44:43,750 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.462621
2012-07-13 21:44:44,252 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.571452
2012-07-13 21:44:44,753 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.677173
2012-07-13 21:44:45,254 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.786004
2012-07-13 21:44:45,756 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.894835
2012-07-13 21:44:46,257 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.000556
2012-07-13 21:44:46,758 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.109387
2012-07-13 21:44:47,260 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.218218
2012-07-13 21:44:47,761 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.323940
2012-07-13 21:44:48,262 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.389238
2012-07-13 21:44:48,764 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.476303
2012-07-13 21:44:49,265 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.647323
2012-07-13 21:44:49,766 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.753045
2012-07-13 21:44:50,268 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.861875
2012-07-13 21:44:50,769 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.917846
2012-07-13 21:44:50,917 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 100.000000
2012-07-13 21:44:51,925 DEBUG: install progress dpkg-exec 0.000000
2012-07-13 21:44:55,588 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-07-13 21:44:55,668 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-07-13 21:44:55,669 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-07-13 21:44:55,912 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-07-13 21:44:56,267 DEBUG: install progress fglrx-updates 18.750000
2012-07-13 21:44:56,269 DEBUG: install progress fglrx-updates 25.000000
2012-07-13 21:45:06,961 DEBUG: install progress fglrx-updates 31.250000
2012-07-13 21:45:07,572 DEBUG: install progress fglrx-updates 37.500000
2012-07-13 21:45:07,666 DEBUG: install progress bamfdaemon 37.500000
2012-07-13 21:45:07,800 DEBUG: install progress ureadahead 37.500000
2012-07-13 21:45:07,910 DEBUG: install progress initramfs-tools 37.500000
2012-07-13 21:45:24,606 DEBUG: install progress libc-bin 37.500000
2012-07-13 21:45:24,966 DEBUG: install progress dpkg-exec 37.500000
2012-07-13 21:45:25,723 DEBUG: install progress fglrx 37.500000
2012-07-13 21:45:25,726 DEBUG: install progress fglrx 43.750000
2012-07-13 21:45:28,584 DEBUG: install progress fglrx 50.000000
2012-07-13 21:45:28,644 DEBUG: install progress fglrx 56.250000
2012-07-13 21:45:28,833 DEBUG: install progress fglrx-amdcccle 56.250000
2012-07-13 21:45:28,934 DEBUG: install progress fglrx-amdcccle 62.500000
2012-07-13 21:45:29,270 DEBUG: install progress fglrx-amdcccle 68.750000
2012-07-13 21:45:29,341 DEBUG: install progress fglrx-amdcccle 75.000000
2012-07-13 21:45:29,426 DEBUG: install progress ureadahead 75.000000
2012-07-13 21:45:29,719 DEBUG: install progress dpkg-exec 75.000000
2012-07-13 21:45:29,775 DEBUG: install progress fglrx 75.000000
2012-07-13 21:45:30,083 DEBUG: install progress fglrx 81.250000
2012-07-13 21:45:53,823 DEBUG: install progress fglrx 87.500000
2012-07-13 21:45:54,176 DEBUG: install progress bamfdaemon 87.500000
2012-07-13 21:45:54,386 DEBUG: install progress fglrx-amdcccle 87.500000
2012-07-13 21:45:54,453 DEBUG: install progress fglrx-amdcccle 93.750000
2012-07-13 21:45:54,512 DEBUG: install progress fglrx-amdcccle 100.000000
2012-07-13 21:45:54,607 DEBUG: install progress initramfs-tools 100.000000
2012-07-13 21:46:07,403 DEBUG: install progress libc-bin 100.000000
2012-07-13 21:46:08,508 DEBUG: (Reading database ... 255999 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx.
(Reading database ... 255760 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic-pae
Building for architecture i686
Building initial module for 3.2.0-26-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-13 21:46:08,802 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:05.0
2012-07-13 21:46:33,151 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,151 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:33,290 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,291 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:33,454 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,454 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:46:33,536 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,536 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:33,675 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,675 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:33,866 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:33,866 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:34,004 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:34,004 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:34,220 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:34,221 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:46:34,281 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:34,282 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:34,425 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:46:34,425 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:46:59,599 DEBUG: Shutting down
2012-07-13 21:48:56,297 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c>
2012-07-13 21:48:58,552 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic-pae/modules.alias
2012-07-13 21:48:58,690 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-13 21:48:58,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-13 21:48:58,790 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-13 21:48:58,875 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-13 21:48:58,885 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-13 21:48:58,885 DEBUG: fglrx.available: falling back to default
2012-07-13 21:48:59,011 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:48:59,022 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-13 21:48:59,023 DEBUG: fglrx.available: falling back to default
2012-07-13 21:48:59,066 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-13 21:48:59,066 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-13 21:48:59,070 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-13 21:48:59,071 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-13 21:48:59,119 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-13 21:48:59,119 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-13 21:48:59,141 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-13 21:48:59,153 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-13 21:48:59,157 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,182 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:48:59,182 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:48:59,190 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-13 21:48:59,196 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-13 21:48:59,197 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,237 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-13 21:48:59,240 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-13 21:48:59,245 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-13 21:48:59,246 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,309 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-13 21:48:59,315 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-13 21:48:59,325 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-13 21:48:59,327 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,348 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:48:59,349 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:48:59,352 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-13 21:48:59,357 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-13 21:48:59,357 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,378 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:48:59,378 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-13 21:48:59,385 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-13 21:48:59,395 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-13 21:48:59,397 DEBUG: nvidia.available: falling back to default
2012-07-13 21:48:59,429 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-13 21:48:59,429 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-13 21:48:59,429 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-13 21:48:59,471 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-13 21:48:59,472 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-13 21:48:59,472 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-13 21:48:59,472 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-13 21:48:59,516 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-13 21:48:59,550 DEBUG: Software modem not available
2012-07-13 21:48:59,551 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-13 21:48:59,624 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-13 21:48:59,625 DEBUG: Firmware for DVB cards not available
2012-07-13 21:48:59,625 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-13 21:48:59,647 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-13 21:48:59,658 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-13 21:48:59,720 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-13 21:48:59,721 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-13 21:48:59,731 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-13 21:48:59,757 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-13 21:48:59,758 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-13 21:48:59,758 DEBUG: all custom handlers loaded
2012-07-13 21:48:59,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:49:00,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-13 21:49:00,227 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,228 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:49:00,134 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:49:00,235 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-13 21:49:00,245 DEBUG: fglrx.available: falling back to default
2012-07-13 21:49:00,313 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,313 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:49:00,285 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-13 21:49:00,313 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-13 21:49:00,344 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,345 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:00,314 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:49:00,478 DEBUG: fglrx.available: falling back to default
2012-07-13 21:49:00,535 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,535 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:00,507 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:49:00,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-13 21:49:00,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:00,787 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-07-13 21:49:00,809 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,809 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:00,788 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:49:00,938 DEBUG: fglrx.available: falling back to default
2012-07-13 21:49:00,976 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:00,976 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:00,958 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-13 21:49:01,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:49:01,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:49:01,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:49:01,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:49:01,143 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-07-13 21:49:01,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:49:01,144 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-13 21:49:01,144 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,144 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-13 21:49:01,144 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:49:01,144 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,144 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:49:01,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:49:01,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-13 21:49:01,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:49:01,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:49:01,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:49:01,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:49:01,168 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-13 21:49:01,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,168 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-13 21:49:01,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:49:01,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:49:01,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:49:01,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:49:01,170 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2012-07-13 21:49:01,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:49:01,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:49:01,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-13 21:49:01,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:49:01,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:49:01,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:49:01,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:49:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:49:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-07-13 21:49:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:49:01,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:49:01,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:49:01,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:49:01,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:49:01,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-13 21:49:01,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,260 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-13 21:49:01,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:49:01,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:49:01,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:49:01,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:49:01,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:49:01,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-07-13 21:49:01,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:49:01,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:49:01,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:49:01,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:49:01,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:49:01,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:49:01,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:49:01,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:49:01,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-13 21:49:01,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-13 21:49:01,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:49:01,295 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:49:01,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-13 21:49:01,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:49:01,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-13 21:49:01,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-13 21:49:01,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-13 21:49:01,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb719ad0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:49:01,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001444bc03sc00i00')
2012-07-13 21:49:01,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2012-07-13 21:49:01,296 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000103Csd00003040bc02sc80i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:pcspkr')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:hp-wmi')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00001444bc0Csc05i00')
2012-07-13 21:49:01,297 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001444bc06sc00i00')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:SYN1E28:SYN1E00:SYN0002:PNP0F13:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00001235bc06sc04i00')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00001444bc02sc00i00')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-13 21:49:01,298 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0C32:')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.29:bd04/07/2011:svnHewlett-Packard:pnPresarioCQ62NotebookPC:pvr0495100003242810000020000:rvnHewlett-Packard:rn1444:rvr69.37:cvnHewlett-Packard:ct10:cvrN/A:')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'usb:v045Ep00E1d0010dc00dsc00dp00ic03isc01ip02')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001444bc06sc01i00')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001444bc01sc06i01')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:eisa')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-07-13 21:49:01,299 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001444bc0Csc03i20')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'platform:regulatory')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001444bc04sc03i00')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-13 21:49:01,300 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb689984c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-13 21:49:01,363 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:01,363 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:49:01,470 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:01,471 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:01,727 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:01,728 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:49:01,804 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:01,805 DEBUG: fglrx_updates is not the alternative in use
2012-07-13 21:49:01,861 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:01,862 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:06,216 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-13 21:49:06,216 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-13 21:49:20,850 DEBUG: Shutting down
```

---

