---
title: "help with Ubuntu 11.10 lightdm?"
date: 2011-10-15
forum: General Help
---

### Post by jeggy on 2011-10-15
i've installed the nvidia driver in ubuntu 11.10 and i had to turn of lightdm and i did that by writing 'sudo stop lightdm' and then i installed the driver successfully, but now i don't know how to start the lightdm again or how i can come to the desktop again.

i have tried 'sudo start lightdm' but it's getting stuck at 'logmein-hamachi' don't know why it has to load hamachi to get to the desktop... 

any solutions?

---

### Post by effenberg0x0 on 2011-10-15
The correct commands would have been:

```
sudo service lightdm stop
sudo service lightdm start
sudo service lightdm restart
```Try ```
sudo service lightdm start
```Report back.

Effenberg

---

### Post by jeggy on 2011-10-16
when i write 'sudo service lightdm start' i get this screen

```

* Starting configure network device
* Starting mDNS/DNS-SD daemon
* Starting ntework connection manager
soeech-dispatcher disabled; edit /etc/default/speech.dispatcher
checking for running unattended-upgrades:
* Starting Winbind daemon winbind
* Starting CUPS printing spooler/server
* Starting Bluetooth
* PulseAudio configured for pre-user session
saned disabled; edit /etc/default/saned
* Starting anac(h)ronistic cron
* Stopping anac(h)ronistic cron
fsck from util-linux 2.19.1
/dev/sda6: clean, 193232/13869056 files, 2372908/55468554 blocks (check in 4 mounts)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
* Starting AppArmor profiles
Starting LogMeIn VPN tunneling engine logmein-hamachi *

```

it's stuck with that hamachi thing.

---

### Post by effenberg0x0 on 2011-10-16
Run this please:

```
lspci | grep -i vga
```

Effenberg

---

### Post by effenberg0x0 on 2011-10-16
Run these commands. These are some fixes for general problems that are affecting Oneiric.

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo mkdir /run
sudo mkdir /run/lock
sudo  mv /var/run/* /run
sudo  mv /var/lock/* /run/lock
sudo rm -rf /var/run
sudo rm -rf /var/rock
sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock
sudo killall -s KILL /usr/bin/X
sudo killall -s KILL /usr/bin/lightdm
sudo killall -s KILL /usr/bin/gdm
sudo apt-get update
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm
if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf
sudo reboot now

```You PC will reboot. If you still don't see lightdm and GUI interface, consider reinstalling video drivers:

If the command lspci | grep -i vga gives you nvidia, try the instructions I posted at [http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia](http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia) (Post #5).

It it's ATI, look at
[http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922) (Post #27)

If its Intel:
```
sudo apt-get install --reinstall xserver-xorg-video-intel
sudo mv /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
sudo service lightdm stop
sudo service lightdm start
```If you still have problems, you might consider renistalling Unity/Compiz critical packages:```

sudo apt-get install --reinstall --fix-broken --allow-unauthenticated unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main
```

---

### Post by jeggy on 2011-10-16
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

i did that you posted #27 but when i  typed sudo service lightdm start
it got stuck checking my battery :/

---

### Post by jeggy on 2011-10-16
I'm just gonna reinstall ubuntu.

---

### Post by jeggy on 2011-10-17
i formatted ubuntu and tried to activate the nvidia driver the easy way through additional drivers and i get an error
```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

and the jockey.log 
```
2011-10-17 08:53:03,565 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c>
2011-10-17 08:53:04,600 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 08:53:04,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 08:53:04,702 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 08:53:04,726 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 08:53:04,769 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 08:53:04,831 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 08:53:04,865 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 08:53:04,866 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 08:53:04,866 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 08:53:04,917 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 08:53:04,918 DEBUG: Firmware for DVB cards not available
2011-10-17 08:53:04,919 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 08:53:04,942 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 08:53:04,949 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 08:53:04,950 DEBUG: fglrx.available: falling back to default
2011-10-17 08:53:05,095 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:53:05,102 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 08:53:05,109 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 08:53:05,110 DEBUG: fglrx.available: falling back to default
2011-10-17 08:53:05,170 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 08:53:05,171 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 08:53:05,180 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 08:53:05,181 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 08:53:05,182 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 08:53:05,182 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 08:53:05,190 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 08:53:05,191 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 08:53:05,225 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 08:53:05,226 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 08:53:05,263 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 08:53:05,294 DEBUG: Software modem not available
2011-10-17 08:53:05,295 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 08:53:05,303 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 08:53:05,309 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 08:53:05,309 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,374 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:53:05,381 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 08:53:05,389 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 08:53:05,389 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,456 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:53:05,463 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 08:53:05,470 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 08:53:05,471 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,543 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:53:05,543 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 08:53:05,561 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 08:53:05,568 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 08:53:05,569 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,637 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:53:05,643 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 08:53:05,651 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 08:53:05,652 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,720 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 08:53:05,728 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 08:53:05,736 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 08:53:05,737 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:05,803 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 08:53:05,804 DEBUG: all custom handlers loaded
2011-10-17 08:53:05,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 08:53:06,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 08:53:06,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 08:53:06,112 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 08:53:06,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 08:53:06,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 08:53:06,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 08:53:06,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 08:53:06,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 08:53:06,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 08:53:06,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 08:53:06,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:53:06,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 08:53:06,130 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 08:53:06,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 08:53:06,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 08:53:06,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 08:53:06,137 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 08:53:06,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 08:53:06,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 08:53:06,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 08:53:06,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 08:53:06,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 08:53:06,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 08:53:06,587 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:06,587 DEBUG: KMH enabled: False
2011-10-17 08:53:06,324 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 08:53:06,595 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 08:53:06,604 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:06,680 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:06,681 DEBUG: KMH enabled: False
2011-10-17 08:53:06,639 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 08:53:06,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 08:53:06,721 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:06,721 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:06,682 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 08:53:06,726 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 08:53:06,735 DEBUG: nvidia.available: falling back to default
2011-10-17 08:53:06,807 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:06,807 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:06,767 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 08:53:06,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 08:53:06,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 08:53:06,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:53:06,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 08:53:06,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 08:53:06,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 08:53:06,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 08:53:06,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:53:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 08:53:06,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 08:53:06,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 08:53:06,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 08:53:06,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 08:53:06,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 08:53:06,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 08:53:06,835 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:53:06,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,835 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 08:53:06,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 08:53:06,835 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,835 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:53:06,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 08:53:06,836 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,836 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 08:53:06,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 08:53:06,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 08:53:06,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 08:53:06,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 08:53:06,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,848 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 08:53:06,848 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 08:53:06,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 08:53:06,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 08:53:06,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 08:53:06,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:53:06,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 08:53:06,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 08:53:06,855 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 08:53:06,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 08:53:06,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,855 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 08:53:06,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 08:53:06,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 08:53:06,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 08:53:06,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 08:53:06,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 08:53:06,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,858 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 08:53:06,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 08:53:06,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 08:53:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 08:53:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 08:53:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 08:53:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 08:53:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 08:53:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:53:06,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,862 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:53:06,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,862 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 08:53:06,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 08:53:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 08:53:06,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 08:53:06,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 08:53:06,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 08:53:06,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 08:53:06,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 08:53:06,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 08:53:06,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 08:53:06,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 08:53:06,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 08:53:06,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725064c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 08:53:06,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 08:53:06,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 08:53:06,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 08:53:06,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69446ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 08:53:06,936 DEBUG: handler xorg:nvidia_current previously unseen
2011-10-17 08:53:06,936 DEBUG: handler xorg:nvidia_current_updates previously unseen
2011-10-17 08:53:06,936 DEBUG: writing back check cache /var/cache/jockey/check
2011-10-17 08:53:06,975 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:06,975 DEBUG: KMH enabled: False
2011-10-17 08:53:07,012 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:07,012 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:07,084 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:07,084 DEBUG: KMH enabled: False
2011-10-17 08:53:20,215 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:20,216 DEBUG: KMH enabled: False
2011-10-17 08:53:20,353 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:20,353 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:21,647 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:21,648 DEBUG: KMH enabled: False
2011-10-17 08:53:21,774 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:21,775 DEBUG: KMH enabled: False
2011-10-17 08:53:21,859 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:21,859 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:23,983 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:23,984 DEBUG: KMH enabled: False
2011-10-17 08:53:24,348 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:24,348 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:53:25,169 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:25,169 DEBUG: KMH enabled: False
2011-10-17 08:53:26,841 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:53:26,842 DEBUG: KMH enabled: False
2011-10-17 08:53:30,286 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 08:53:30,287 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 08:54:00,272 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:00,272 DEBUG: KMH enabled: False
2011-10-17 08:54:00,320 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:00,321 DEBUG: KMH enabled: False
2011-10-17 08:54:05,370 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,370 DEBUG: KMH enabled: False
2011-10-17 08:54:05,385 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,386 DEBUG: KMH enabled: False
2011-10-17 08:54:05,415 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,416 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 08:54:05,449 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,449 DEBUG: KMH enabled: False
2011-10-17 08:54:05,464 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,464 DEBUG: KMH enabled: False
2011-10-17 08:54:05,507 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,507 DEBUG: KMH enabled: False
2011-10-17 08:54:05,522 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,522 DEBUG: KMH enabled: False
2011-10-17 08:54:05,549 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 08:54:05,549 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:05:56,709 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:05:56,709 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:05:58,125 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:05:58,126 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:06:02,916 DEBUG: Installing package: nvidia-current-updates
2011-10-17 09:06:03,099 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2011-10-17 09:06:03,219 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 09:06:03,220 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 09:06:03,231 ERROR: xorg:nvidia_current_updates: get_alternative_by_name(nvidia-current-updates) returned nothing
2011-10-17 09:06:03,332 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:03,333 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:06:09,048 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,049 DEBUG: KMH enabled: False
2011-10-17 09:06:09,095 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,096 DEBUG: KMH enabled: False
2011-10-17 09:06:09,188 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,188 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:06:09,284 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,284 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:06:09,387 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,388 DEBUG: KMH enabled: False
2011-10-17 09:06:09,434 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,435 DEBUG: KMH enabled: False
2011-10-17 09:06:09,517 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:06:09,518 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:06:10,780 DEBUG: Shutting down
2011-10-17 09:36:25,217 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c>
2011-10-17 09:36:26,353 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 09:36:26,454 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 09:36:26,462 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 09:36:26,490 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 09:36:26,501 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 09:36:26,557 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 09:36:26,567 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 09:36:26,567 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 09:36:26,567 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 09:36:26,593 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 09:36:26,594 DEBUG: Firmware for DVB cards not available
2011-10-17 09:36:26,594 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 09:36:26,630 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 09:36:26,633 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 09:36:26,633 DEBUG: fglrx.available: falling back to default
2011-10-17 09:36:26,732 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 09:36:26,734 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 09:36:26,737 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 09:36:26,737 DEBUG: fglrx.available: falling back to default
2011-10-17 09:36:26,759 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 09:36:26,759 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 09:36:26,762 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 09:36:26,762 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 09:36:26,762 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 09:36:26,762 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 09:36:26,765 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 09:36:26,765 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 09:36:26,776 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 09:36:26,777 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 09:36:26,788 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 09:36:26,806 DEBUG: Software modem not available
2011-10-17 09:36:26,806 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 09:36:26,813 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 09:36:26,816 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 09:36:26,816 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,838 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 09:36:26,841 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 09:36:26,844 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 09:36:26,844 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,867 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 09:36:26,870 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 09:36:26,872 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 09:36:26,873 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,895 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 09:36:26,895 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 09:36:26,911 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 09:36:26,914 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 09:36:26,914 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,937 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 09:36:26,939 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 09:36:26,942 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 09:36:26,942 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,963 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 09:36:26,966 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 09:36:26,969 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 09:36:26,969 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:26,991 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 09:36:26,991 DEBUG: all custom handlers loaded
2011-10-17 09:36:26,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 09:36:27,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 09:36:27,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 09:36:27,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 09:36:27,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 09:36:27,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 09:36:27,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 09:36:27,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 09:36:27,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 09:36:27,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 09:36:27,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 09:36:27,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 09:36:27,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 09:36:27,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,368 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 09:36:27,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 09:36:27,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 09:36:27,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 09:36:27,377 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 09:36:27,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 09:36:27,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 09:36:27,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 09:36:27,608 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 09:36:27,608 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,608 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 09:36:27,608 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,609 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 09:36:27,791 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:27,791 DEBUG: KMH enabled: False
2011-10-17 09:36:27,609 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 09:36:27,793 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 09:36:27,796 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:27,819 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:27,819 DEBUG: KMH enabled: False
2011-10-17 09:36:27,806 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 09:36:27,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 09:36:27,832 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:27,832 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:27,820 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 09:36:27,834 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-17 09:36:27,836 DEBUG: nvidia.available: falling back to default
2011-10-17 09:36:27,862 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:27,862 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:27,847 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 09:36:27,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 09:36:27,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 09:36:27,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 09:36:27,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 09:36:27,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 09:36:27,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 09:36:27,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 09:36:27,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 09:36:27,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 09:36:27,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 09:36:27,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 09:36:27,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 09:36:27,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 09:36:27,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 09:36:27,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 09:36:27,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 09:36:27,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 09:36:27,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 09:36:27,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 09:36:27,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 09:36:27,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 09:36:27,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 09:36:27,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 09:36:27,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 09:36:27,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 09:36:27,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,922 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 09:36:27,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 09:36:27,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 09:36:27,930 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 09:36:27,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 09:36:27,930 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,930 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 09:36:27,931 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 09:36:27,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 09:36:27,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 09:36:27,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 09:36:27,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 09:36:27,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 09:36:27,937 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 09:36:27,937 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 09:36:27,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 09:36:27,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 09:36:27,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,939 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 09:36:27,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 09:36:27,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 09:36:27,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 09:36:27,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 09:36:27,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 09:36:27,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 09:36:27,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 09:36:27,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 09:36:27,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 09:36:27,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 09:36:27,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 09:36:27,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 09:36:27,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 09:36:27,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 09:36:27,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 09:36:27,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 09:36:27,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 09:36:27,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 09:36:27,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 09:36:27,957 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,957 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 09:36:27,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 09:36:27,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724f64c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 09:36:27,958 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 09:36:27,959 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 09:36:27,960 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 09:36:27,961 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 09:36:27,962 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69436ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 09:36:27,999 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:27,999 DEBUG: KMH enabled: False
2011-10-17 09:36:28,737 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:28,737 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:29,452 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:29,452 DEBUG: KMH enabled: False
2011-10-17 09:36:29,492 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:29,493 DEBUG: KMH enabled: False
2011-10-17 09:36:29,518 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:29,518 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:30,604 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:30,604 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:32,147 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 09:36:32,147 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 09:36:33,864 DEBUG: Installing package: nvidia-current-updates
2011-10-17 09:36:34,123 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-17 09:36:34,123 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-17 09:36:34,416 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-17 09:36:34,568 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-17 09:36:34,834 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.003415
2011-10-17 09:36:35,335 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.034239
2011-10-17 09:36:35,836 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.069467
2011-10-17 09:36:36,337 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.069467
2011-10-17 09:36:36,837 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.069467
2011-10-17 09:36:37,338 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.069467
2011-10-17 09:36:37,839 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.069467
2011-10-17 09:36:38,340 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.095888
2011-10-17 09:36:38,841 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.144327
2011-10-17 09:36:39,341 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.166344
2011-10-17 09:36:39,842 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.210379
2011-10-17 09:36:40,343 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.276431
2011-10-17 09:36:40,844 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.342483
2011-10-17 09:36:41,344 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.452571
2011-10-17 09:36:41,845 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.518623
2011-10-17 09:36:42,346 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.694762
2011-10-17 09:36:42,847 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.804849
2011-10-17 09:36:43,348 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 1.047041
2011-10-17 09:36:43,848 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 1.377303
2011-10-17 09:36:44,349 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 1.861686
2011-10-17 09:36:44,850 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 2.081860
2011-10-17 09:36:45,351 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 2.575051
2011-10-17 09:36:45,852 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 2.918523
2011-10-17 09:36:46,352 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 3.116679
2011-10-17 09:36:46,853 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 3.592256
2011-10-17 09:36:47,354 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 3.896096
2011-10-17 09:36:47,855 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 4.503777
2011-10-17 09:36:48,356 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 4.856056
2011-10-17 09:36:48,856 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 5.115862
2011-10-17 09:36:49,357 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 5.560614
2011-10-17 09:36:49,858 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 5.785192
2011-10-17 09:36:50,359 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 6.172698
2011-10-17 09:36:50,859 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 6.366452
2011-10-17 09:36:51,360 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 6.789186
2011-10-17 09:36:51,861 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 6.842028
2011-10-17 09:36:52,362 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.093027
2011-10-17 09:36:52,863 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.119448
2011-10-17 09:36:53,363 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.216325
2011-10-17 09:36:53,864 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.388060
2011-10-17 09:36:54,365 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.674287
2011-10-17 09:36:54,866 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.951707
2011-10-17 09:36:55,366 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 8.185091
2011-10-17 09:36:55,867 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 8.334810
2011-10-17 09:36:56,368 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 8.612229
2011-10-17 09:36:56,869 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 8.858825
2011-10-17 09:36:57,370 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.061385
2011-10-17 09:36:57,870 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.197893
2011-10-17 09:36:58,371 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.202297
2011-10-17 09:36:58,872 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.211104
2011-10-17 09:36:59,373 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.211104
2011-10-17 09:36:59,874 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.228717
2011-10-17 09:37:00,375 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.294770
2011-10-17 09:37:00,875 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.387243
2011-10-17 09:37:01,376 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.563382
2011-10-17 09:37:01,877 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.655856
2011-10-17 09:37:02,378 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.757136
2011-10-17 09:37:02,878 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.889240
2011-10-17 09:37:03,379 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.096204
2011-10-17 09:37:03,880 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.232712
2011-10-17 09:37:04,381 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.391238
2011-10-17 09:37:04,881 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.589395
2011-10-17 09:37:05,382 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.783148
2011-10-17 09:37:05,883 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 11.219093
2011-10-17 09:37:06,385 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 11.443671
2011-10-17 09:37:06,886 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.033738
2011-10-17 09:37:07,387 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.284737
2011-10-17 09:37:07,888 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.355192
2011-10-17 09:37:08,389 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.738296
2011-10-17 09:37:08,890 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.958470
2011-10-17 09:37:09,391 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 13.222679
2011-10-17 09:37:09,892 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 13.385608
2011-10-17 09:37:10,393 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 13.618993
2011-10-17 09:37:10,894 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 14.098973
2011-10-17 09:37:11,395 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 14.715461
2011-10-17 09:37:11,896 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 15.204248
2011-10-17 09:37:12,397 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 15.543316
2011-10-17 09:37:12,899 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 16.115769
2011-10-17 09:37:13,400 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 16.291908
2011-10-17 09:37:13,901 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 16.591346
2011-10-17 09:37:14,402 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 17.185816
2011-10-17 09:37:14,903 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 17.524884
2011-10-17 09:37:15,404 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.062110
2011-10-17 09:37:15,905 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.216232
2011-10-17 09:37:16,406 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.251460
2011-10-17 09:37:16,908 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.277881
2011-10-17 09:37:17,409 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.286687
2011-10-17 09:37:17,910 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.304301
2011-10-17 09:37:18,411 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.396775
2011-10-17 09:37:18,912 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.458423
2011-10-17 09:37:19,414 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.572914
2011-10-17 09:37:19,915 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.660984
2011-10-17 09:37:20,416 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.876755
2011-10-17 09:37:20,917 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.876755
2011-10-17 09:37:21,418 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.176192
2011-10-17 09:37:21,919 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.264261
2011-10-17 09:37:22,420 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.365541
2011-10-17 09:37:22,922 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.563698
2011-10-17 09:37:23,423 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.669382
2011-10-17 09:37:23,924 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.889556
2011-10-17 09:37:24,425 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.017257
2011-10-17 09:37:24,926 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.312291
2011-10-17 09:37:25,428 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.475220
2011-10-17 09:37:25,929 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.638149
2011-10-17 09:37:26,430 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.950796
2011-10-17 09:37:26,931 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 21.078497
2011-10-17 09:37:27,432 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 21.254637
2011-10-17 09:37:27,934 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 21.417566
2011-10-17 09:37:28,435 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 21.620126
2011-10-17 09:37:28,936 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 21.840300
2011-10-17 09:37:29,437 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 22.029650
2011-10-17 09:37:29,938 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 22.236614
2011-10-17 09:37:30,440 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 22.712191
2011-10-17 09:37:30,941 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 22.954382
2011-10-17 09:37:31,442 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 23.275837
2011-10-17 09:37:31,943 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 23.557660
2011-10-17 09:37:32,445 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 23.562063
2011-10-17 09:37:32,946 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 24.165341
2011-10-17 09:37:33,447 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 24.319463
2011-10-17 09:37:33,948 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 24.596882
2011-10-17 09:37:34,449 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 25.010810
2011-10-17 09:37:34,950 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 25.446755
2011-10-17 09:37:35,452 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 25.706561
2011-10-17 09:37:35,953 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 25.904718
2011-10-17 09:37:36,455 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 26.221769
2011-10-17 09:37:36,956 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 26.587258
2011-10-17 09:37:37,457 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 26.789818
2011-10-17 09:37:37,958 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 27.186132
2011-10-17 09:37:38,460 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 27.688129
2011-10-17 09:37:38,961 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 28.234162
2011-10-17 09:37:39,462 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 28.595247
2011-10-17 09:37:39,963 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 29.290998
2011-10-17 09:37:40,465 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 29.669698
2011-10-17 09:37:40,966 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 30.215730
2011-10-17 09:37:41,467 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 30.356642
2011-10-17 09:37:41,969 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 30.858639
2011-10-17 09:37:42,470 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 30.858639
2011-10-17 09:37:42,971 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 31.316602
2011-10-17 09:37:43,472 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 31.726126
2011-10-17 09:37:43,973 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 31.968317
2011-10-17 09:37:44,475 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.351421
2011-10-17 09:37:44,976 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.514350
2011-10-17 09:37:45,477 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.593612
2011-10-17 09:37:45,979 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.804980
2011-10-17 09:37:46,480 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.959102
2011-10-17 09:37:46,981 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 33.148452
2011-10-17 09:37:47,483 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 33.359819
2011-10-17 09:37:47,984 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 33.606414
2011-10-17 09:37:48,485 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 33.861816
2011-10-17 09:37:48,986 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.011535
2011-10-17 09:37:49,488 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.095201
2011-10-17 09:37:49,989 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.108411
2011-10-17 09:37:50,490 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.280147
2011-10-17 09:37:50,992 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.425462
2011-10-17 09:37:51,493 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.504725
2011-10-17 09:37:51,994 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.672058
2011-10-17 09:37:52,496 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.777741
2011-10-17 09:37:52,997 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 34.993512
2011-10-17 09:37:53,498 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.006723
2011-10-17 09:37:53,999 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.103599
2011-10-17 09:37:54,501 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.328177
2011-10-17 09:37:55,002 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.416247
2011-10-17 09:37:55,503 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.499913
2011-10-17 09:37:56,004 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.605597
2011-10-17 09:37:56,505 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.605597
2011-10-17 09:37:57,007 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.856595
2011-10-17 09:37:57,508 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.944665
2011-10-17 09:37:58,010 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.010717
2011-10-17 09:37:58,511 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.054752
2011-10-17 09:37:59,012 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.063559
2011-10-17 09:37:59,514 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.186857
2011-10-17 09:38:00,015 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.222085
2011-10-17 09:38:00,516 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.261716
2011-10-17 09:38:01,017 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.310154
2011-10-17 09:38:01,519 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.376207
2011-10-17 09:38:02,020 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.437855
2011-10-17 09:38:02,521 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.503908
2011-10-17 09:38:03,022 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.503908
2011-10-17 09:38:03,524 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.649223
2011-10-17 09:38:04,025 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.719678
2011-10-17 09:38:04,526 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.750503
2011-10-17 09:38:05,027 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.803345
2011-10-17 09:38:05,528 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.878204
2011-10-17 09:38:06,030 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.931046
2011-10-17 09:38:06,531 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.931046
2011-10-17 09:38:07,032 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.001502
2011-10-17 09:38:07,533 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.049940
2011-10-17 09:38:08,034 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.107185
2011-10-17 09:38:08,536 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.138010
2011-10-17 09:38:09,037 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.168834
2011-10-17 09:38:09,537 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.199658
2011-10-17 09:38:10,038 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.230483
2011-10-17 09:38:10,540 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:11,041 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:11,542 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:12,044 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:12,546 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:13,047 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:13,548 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:14,049 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:14,551 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:15,052 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:15,553 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.265711
2011-10-17 09:38:16,054 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.274518
2011-10-17 09:38:16,556 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.292132
2011-10-17 09:38:17,057 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.322956
2011-10-17 09:38:17,558 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.349377
2011-10-17 09:38:18,060 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.358184
2011-10-17 09:38:18,561 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:19,062 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:19,564 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:20,065 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:20,567 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:21,068 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:21,569 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.393412
2011-10-17 09:38:22,070 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:22,572 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:23,073 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:23,574 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:24,075 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:24,576 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:25,077 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:25,579 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:26,080 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:26,581 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.419833
2011-10-17 09:38:27,082 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.428640
2011-10-17 09:38:27,583 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.477078
2011-10-17 09:38:28,085 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.503499
2011-10-17 09:38:28,586 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.529920
2011-10-17 09:38:29,088 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.595972
2011-10-17 09:38:29,589 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:30,090 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:30,592 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:31,093 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:31,594 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:32,096 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.631200
2011-10-17 09:38:32,597 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.657621
2011-10-17 09:38:33,098 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.688445
2011-10-17 09:38:33,600 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:34,101 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:34,602 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:35,104 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:35,605 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:36,106 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.714866
2011-10-17 09:38:36,607 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.723673
2011-10-17 09:38:37,109 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.754498
2011-10-17 09:38:37,610 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.776515
2011-10-17 09:38:38,111 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.807339
2011-10-17 09:38:38,612 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.873392
2011-10-17 09:38:39,114 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.904216
2011-10-17 09:38:39,615 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.979075
2011-10-17 09:38:40,116 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.031917
2011-10-17 09:38:40,617 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.031917
2011-10-17 09:38:41,118 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.031917
2011-10-17 09:38:41,620 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.040724
2011-10-17 09:38:42,121 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.058338
2011-10-17 09:38:42,622 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.119987
2011-10-17 09:38:43,123 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.155215
2011-10-17 09:38:43,625 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.155215
2011-10-17 09:38:44,126 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.155215
2011-10-17 09:38:44,627 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.155215
2011-10-17 09:38:45,128 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.164022
2011-10-17 09:38:45,630 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.164022
2011-10-17 09:38:46,131 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.164022
2011-10-17 09:38:46,632 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.164022
2011-10-17 09:38:47,133 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.172829
2011-10-17 09:38:47,635 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.190443
2011-10-17 09:38:48,136 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.203653
2011-10-17 09:38:48,637 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.282916
2011-10-17 09:38:49,139 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.326951
2011-10-17 09:38:49,640 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.344565
2011-10-17 09:38:50,142 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.344565
2011-10-17 09:38:50,643 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.362179
2011-10-17 09:38:51,144 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.410617
2011-10-17 09:38:51,645 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.445845
2011-10-17 09:38:52,147 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.507494
2011-10-17 09:38:52,649 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.547125
2011-10-17 09:38:53,151 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.635195
2011-10-17 09:38:53,652 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.683633
2011-10-17 09:38:54,153 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.732071
2011-10-17 09:38:54,655 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.780510
2011-10-17 09:38:55,156 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.833352
2011-10-17 09:38:55,657 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.877386
2011-10-17 09:38:56,158 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.877386
2011-10-17 09:38:56,660 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.991877
2011-10-17 09:38:57,161 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.071140
2011-10-17 09:38:57,662 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.119578
2011-10-17 09:38:58,163 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.181227
2011-10-17 09:38:58,665 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.247279
2011-10-17 09:38:59,166 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.291314
2011-10-17 09:38:59,667 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.339752
2011-10-17 09:39:00,168 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.379384
2011-10-17 09:39:00,670 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.379384
2011-10-17 09:39:01,171 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.445436
2011-10-17 09:39:01,672 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.524699
2011-10-17 09:39:02,173 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.621576
2011-10-17 09:39:02,674 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.670014
2011-10-17 09:39:03,175 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.775698
2011-10-17 09:39:03,676 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 39.943030
2011-10-17 09:39:04,179 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.172011
2011-10-17 09:39:04,680 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.370168
2011-10-17 09:39:05,181 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.594746
2011-10-17 09:39:05,682 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.700430
2011-10-17 09:39:06,184 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.700430
2011-10-17 09:39:06,685 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 41.360952
2011-10-17 09:39:07,192 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 41.792494
2011-10-17 09:39:07,698 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.074317
2011-10-17 09:39:08,200 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.232843
2011-10-17 09:39:08,701 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.435403
2011-10-17 09:39:09,202 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.633560
2011-10-17 09:39:09,704 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.888962
2011-10-17 09:39:10,205 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.888962
2011-10-17 09:39:10,706 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 43.144364
2011-10-17 09:39:11,208 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 43.342521
2011-10-17 09:39:11,709 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 43.597923
2011-10-17 09:39:12,210 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 43.831308
2011-10-17 09:39:12,712 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.038272
2011-10-17 09:39:13,213 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.192394
2011-10-17 09:39:13,714 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.232025
2011-10-17 09:39:14,216 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.531462
2011-10-17 09:39:14,717 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.804478
2011-10-17 09:39:15,218 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.804478
2011-10-17 09:39:15,719 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.830899
2011-10-17 09:39:16,220 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.830899
2011-10-17 09:39:16,721 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.328493
2011-10-17 09:39:17,223 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.328493
2011-10-17 09:39:17,724 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.553071
2011-10-17 09:39:18,225 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.843701
2011-10-17 09:39:18,727 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.843701
2011-10-17 09:39:19,228 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.116717
2011-10-17 09:39:19,729 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.116717
2011-10-17 09:39:20,231 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.513031
2011-10-17 09:39:20,732 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.513031
2011-10-17 09:39:21,233 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.909344
2011-10-17 09:39:21,734 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.909344
2011-10-17 09:39:22,236 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 47.252816
2011-10-17 09:39:22,737 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 47.327675
2011-10-17 09:39:23,238 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 47.327675
2011-10-17 09:39:23,740 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 47.917743
2011-10-17 09:39:24,241 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 47.917743
2011-10-17 09:39:24,742 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.230390
2011-10-17 09:39:25,244 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.230390
2011-10-17 09:39:25,745 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.494599
2011-10-17 09:39:26,246 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.719177
2011-10-17 09:39:26,748 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.824861
2011-10-17 09:39:27,249 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.824861
2011-10-17 09:39:27,750 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.296034
2011-10-17 09:39:28,253 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.498594
2011-10-17 09:39:28,754 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.498594
2011-10-17 09:39:29,255 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.683540
2011-10-17 09:39:29,757 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.881697
2011-10-17 09:39:30,258 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.925732
2011-10-17 09:39:30,760 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.079854
2011-10-17 09:39:31,261 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.339660
2011-10-17 09:39:31,762 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.590658
2011-10-17 09:39:32,264 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.850464
2011-10-17 09:39:32,765 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.912113
2011-10-17 09:39:33,266 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 51.215953
2011-10-17 09:39:33,768 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 51.370075
2011-10-17 09:39:34,269 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 51.665109
2011-10-17 09:39:34,770 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 51.995370
2011-10-17 09:39:35,271 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 52.365263
2011-10-17 09:39:35,773 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 52.655893
2011-10-17 09:39:36,274 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 52.655893
2011-10-17 09:39:36,775 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 53.320819
2011-10-17 09:39:37,277 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 53.637870
2011-10-17 09:39:37,778 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 53.994553
2011-10-17 09:39:38,280 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 54.377656
2011-10-17 09:39:38,781 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 54.787180
2011-10-17 09:39:39,283 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 54.892864
2011-10-17 09:39:39,784 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 55.231932
2011-10-17 09:39:40,286 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 55.271564
2011-10-17 09:39:40,787 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 55.949700
2011-10-17 09:39:41,288 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 56.284365
2011-10-17 09:39:41,790 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 56.619030
2011-10-17 09:39:42,291 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 56.953695
2011-10-17 09:39:42,792 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 57.112221
2011-10-17 09:39:43,294 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 57.543762
2011-10-17 09:39:43,795 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 57.807971
2011-10-17 09:39:44,296 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 57.944479
2011-10-17 09:39:44,797 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 58.138233
2011-10-17 09:39:45,299 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 58.402442
2011-10-17 09:39:45,800 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 58.402442
2011-10-17 09:39:46,301 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 58.869211
2011-10-17 09:39:46,802 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.018930
2011-10-17 09:39:47,304 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.071772
2011-10-17 09:39:47,805 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.155438
2011-10-17 09:39:48,306 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.243508
2011-10-17 09:39:48,808 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.318367
2011-10-17 09:39:49,309 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.494506
2011-10-17 09:39:49,811 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.767522
2011-10-17 09:39:50,312 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.899627
2011-10-17 09:39:50,813 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 60.185854
2011-10-17 09:39:51,314 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 60.780324
2011-10-17 09:39:51,815 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 60.780324
2011-10-17 09:39:52,317 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 61.445250
2011-10-17 09:39:52,817 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 61.674232
2011-10-17 09:39:53,319 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 62.088159
2011-10-17 09:39:53,820 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 62.330351
2011-10-17 09:39:54,321 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 62.563736
2011-10-17 09:39:54,822 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 62.871980
2011-10-17 09:39:55,323 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 63.479661
2011-10-17 09:39:55,825 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 63.801115
2011-10-17 09:39:56,326 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 64.377972
2011-10-17 09:39:56,827 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 64.699426
2011-10-17 09:39:57,328 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 65.020881
2011-10-17 09:39:57,829 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 65.646176
2011-10-17 09:39:58,331 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 65.844333
2011-10-17 09:39:58,832 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 66.095331
2011-10-17 09:39:59,333 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 66.447610
2011-10-17 09:39:59,834 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 66.725030
2011-10-17 09:40:00,336 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 67.064098
2011-10-17 09:40:00,837 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 67.680586
2011-10-17 09:40:01,339 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 67.993234
2011-10-17 09:40:01,840 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 68.310285
2011-10-17 09:40:02,341 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 68.904755
2011-10-17 09:40:02,842 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 69.301069
2011-10-17 09:40:03,343 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 69.697383
2011-10-17 09:40:03,845 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 69.697383
2011-10-17 09:40:04,346 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 70.472396
2011-10-17 09:40:04,848 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 70.622115
2011-10-17 09:40:05,349 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 70.886324
2011-10-17 09:40:05,850 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 71.375111
2011-10-17 09:40:06,351 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 71.568864
2011-10-17 09:40:06,852 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 71.960774
2011-10-17 09:40:07,353 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 72.220580
2011-10-17 09:40:07,855 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 72.748998
2011-10-17 09:40:08,356 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 73.264206
2011-10-17 09:40:08,857 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 73.541626
2011-10-17 09:40:09,359 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 73.819045
2011-10-17 09:40:09,860 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 74.096465
2011-10-17 09:40:10,361 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 74.651304
2011-10-17 09:40:10,863 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 74.849461
2011-10-17 09:40:11,365 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 75.135687
2011-10-17 09:40:11,866 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 75.549615
2011-10-17 09:40:12,367 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 75.862263
2011-10-17 09:40:12,868 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 76.196927
2011-10-17 09:40:13,369 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 76.738556
2011-10-17 09:40:13,870 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 76.738556
2011-10-17 09:40:14,372 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 77.271378
2011-10-17 09:40:14,873 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 77.416693
2011-10-17 09:40:15,374 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 77.764568
2011-10-17 09:40:15,875 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 77.914287
2011-10-17 09:40:16,377 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 78.218127
2011-10-17 09:40:16,878 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 78.438302
2011-10-17 09:40:17,379 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 78.684897
2011-10-17 09:40:17,880 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.032772
2011-10-17 09:40:18,382 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.208912
2011-10-17 09:40:18,882 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.627243
2011-10-17 09:40:19,384 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.803382
2011-10-17 09:40:19,885 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.865031
2011-10-17 09:40:20,386 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 80.331800
2011-10-17 09:40:20,888 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 80.596010
2011-10-17 09:40:21,389 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 80.992323
2011-10-17 09:40:21,890 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 81.586794
2011-10-17 09:40:22,391 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 82.181264
2011-10-17 09:40:22,892 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 82.234106
2011-10-17 09:40:23,393 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 83.119207
2011-10-17 09:40:23,894 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 83.370206
2011-10-17 09:40:24,395 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 83.669643
2011-10-17 09:40:24,897 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 83.889817
2011-10-17 09:40:25,398 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.162833
2011-10-17 09:40:25,899 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.554743
2011-10-17 09:40:26,400 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.686848
2011-10-17 09:40:26,902 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.845373
2011-10-17 09:40:27,403 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.955460
2011-10-17 09:40:27,904 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 85.153617
2011-10-17 09:40:28,405 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 85.549931
2011-10-17 09:40:28,906 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 85.748088
2011-10-17 09:40:29,407 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 85.946245
2011-10-17 09:40:29,908 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 86.144402
2011-10-17 09:40:30,410 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 86.443839
2011-10-17 09:40:30,911 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 86.937029
2011-10-17 09:40:31,412 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.333343
2011-10-17 09:40:31,912 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.333343
2011-10-17 09:40:32,413 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.795709
2011-10-17 09:40:32,914 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.848551
2011-10-17 09:40:33,415 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.874971
2011-10-17 09:40:33,916 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.874971
2011-10-17 09:40:34,417 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.883778
2011-10-17 09:40:34,918 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.901392
2011-10-17 09:40:35,418 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.901392
2011-10-17 09:40:35,919 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.901392
2011-10-17 09:40:36,420 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.910199
2011-10-17 09:40:36,921 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.927813
2011-10-17 09:40:37,421 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.029093
2011-10-17 09:40:37,922 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.125970
2011-10-17 09:40:38,423 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.236057
2011-10-17 09:40:38,925 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.385776
2011-10-17 09:40:39,426 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.522284
2011-10-17 09:40:39,927 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.680809
2011-10-17 09:40:40,428 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.918598
2011-10-17 09:40:40,929 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 89.187210
2011-10-17 09:40:41,430 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 89.389770
2011-10-17 09:40:41,931 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 89.790488
2011-10-17 09:40:42,432 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 90.195608
2011-10-17 09:40:42,933 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 90.609536
2011-10-17 09:40:43,433 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 91.067499
2011-10-17 09:40:43,934 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 91.463812
2011-10-17 09:40:44,434 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 91.943792
2011-10-17 09:40:44,935 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 92.023055
2011-10-17 09:40:45,436 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 92.718806
2011-10-17 09:40:45,937 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 92.881735
2011-10-17 09:40:46,438 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 93.278048
2011-10-17 09:40:46,939 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 93.551064
2011-10-17 09:40:47,439 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 93.762432
2011-10-17 09:40:47,940 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 94.255622
2011-10-17 09:40:48,441 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 94.466989
2011-10-17 09:40:48,942 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 94.863303
2011-10-17 09:40:49,443 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 95.272827
2011-10-17 09:40:49,943 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 95.647124
2011-10-17 09:40:50,444 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 95.920140
2011-10-17 09:40:50,945 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.096279
2011-10-17 09:40:51,446 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.303243
2011-10-17 09:40:51,947 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.312050
2011-10-17 09:40:52,448 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.426541
2011-10-17 09:40:52,948 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.646715
2011-10-17 09:40:53,449 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.783223
2011-10-17 09:40:53,950 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.932941
2011-10-17 09:40:54,451 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.153116
2011-10-17 09:40:54,663 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.159773
2011-10-17 09:40:54,663 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.165356
2011-10-17 09:40:55,164 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.345539
2011-10-17 09:40:55,665 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.504064
2011-10-17 09:40:56,166 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.790291
2011-10-17 09:40:56,666 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.975237
2011-10-17 09:40:57,167 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 98.177798
2011-10-17 09:40:57,668 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 98.424393
2011-10-17 09:40:58,169 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 98.930794
2011-10-17 09:40:58,669 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 98.983635
2011-10-17 09:40:59,170 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 99.503247
2011-10-17 09:40:59,594 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 100.000000
2011-10-17 09:41:00,651 DEBUG: install progress dpkg-exec 0.000000
2011-10-17 09:41:02,628 DEBUG: install progress nvidia-current-updates 0.000000
2011-10-17 09:41:02,628 DEBUG: install progress nvidia-current-updates 10.000000
2011-10-17 09:41:07,802 DEBUG: install progress nvidia-current-updates 20.000000
2011-10-17 09:41:07,876 DEBUG: install progress nvidia-current-updates 30.000000
2011-10-17 09:41:08,213 DEBUG: install progress nvidia-settings-updates 30.000000
2011-10-17 09:41:08,213 DEBUG: install progress nvidia-settings-updates 40.000000
2011-10-17 09:41:08,522 DEBUG: install progress nvidia-settings-updates 50.000000
2011-10-17 09:41:08,595 DEBUG: install progress nvidia-settings-updates 60.000000
2011-10-17 09:41:08,688 DEBUG: install progress man-db 60.000000
2011-10-17 09:41:10,281 DEBUG: install progress dpkg-exec 60.000000
2011-10-17 09:41:10,306 DEBUG: install progress nvidia-current-updates 60.000000
2011-10-17 09:41:10,393 DEBUG: install progress nvidia-current-updates 70.000000
2011-10-17 09:41:45,898 DEBUG: install progress nvidia-current-updates 80.000000
2011-10-17 09:41:46,338 DEBUG: install progress nvidia-settings-updates 80.000000
2011-10-17 09:41:46,430 DEBUG: install progress nvidia-settings-updates 90.000000
2011-10-17 09:41:46,717 DEBUG: install progress nvidia-settings-updates 100.000000
2011-10-17 09:41:46,967 DEBUG: install progress bamfdaemon 100.000000
2011-10-17 09:41:47,159 DEBUG: install progress gnome-menus 100.000000
2011-10-17 09:41:48,262 DEBUG: Selecting previously deselected package nvidia-current-updates.
(Reading database ... 138999 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_280.13-0ubuntu5_i386.deb) ...
Selecting previously deselected package nvidia-settings-updates.
Unpacking nvidia-settings-updates (from .../nvidia-settings-updates_280.13-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (280.13-0ubuntu5) ...
Loading new nvidia-current-updates-280.13 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic-pae
Building for architecture i686
Building initial module for 3.0.0-12-generic-pae
Done.

nvidia_current_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic-pae/updates/dkms/

depmod.......

DKMS: install Completed.
Setting up nvidia-settings-updates (280.13-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-settings-updates/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...

2011-10-17 09:41:48,899 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n']})
2011-10-17 09:42:15,185 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:15,244 DEBUG: KMH enabled: True
2011-10-17 09:42:15,325 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:15,378 DEBUG: KMH enabled: True
2011-10-17 09:42:15,551 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:15,552 DEBUG: nvidia_current is not the alternative in use
2011-10-17 09:42:15,628 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:15,678 DEBUG: KMH enabled: True
2011-10-17 09:42:15,756 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:15,815 DEBUG: KMH enabled: True
2011-10-17 09:42:15,963 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:16,020 DEBUG: KMH enabled: True
2011-10-17 09:42:16,096 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:16,153 DEBUG: KMH enabled: True
2011-10-17 09:42:16,327 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:16,328 DEBUG: nvidia_current is not the alternative in use
2011-10-17 09:42:16,414 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:16,476 DEBUG: KMH enabled: True
2011-10-17 09:42:16,552 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 09:42:16,609 DEBUG: KMH enabled: True
2011-10-17 09:53:38,014 DEBUG: Shutting down
2011-10-17 10:11:43,767 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c>
2011-10-17 10:11:45,647 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 10:11:45,738 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 10:11:45,746 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 10:11:45,774 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 10:11:45,785 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 10:11:45,835 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 10:11:45,847 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 10:11:45,847 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 10:11:45,847 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 10:11:45,868 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 10:11:45,869 DEBUG: Firmware for DVB cards not available
2011-10-17 10:11:45,869 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 10:11:45,906 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 10:11:45,908 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 10:11:45,909 DEBUG: fglrx.available: falling back to default
2011-10-17 10:11:45,999 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:11:46,002 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 10:11:46,004 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 10:11:46,004 DEBUG: fglrx.available: falling back to default
2011-10-17 10:11:46,024 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 10:11:46,024 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 10:11:46,027 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 10:11:46,028 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 10:11:46,028 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 10:11:46,028 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 10:11:46,030 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 10:11:46,030 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 10:11:46,052 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 10:11:46,052 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 10:11:46,063 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 10:11:46,079 DEBUG: Software modem not available
2011-10-17 10:11:46,079 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 10:11:46,084 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 10:11:46,087 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 10:11:46,087 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,107 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:11:46,109 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:11:46,111 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 10:11:46,111 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,132 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:11:46,134 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 10:11:46,136 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 10:11:46,136 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,156 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:11:46,156 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 10:11:46,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 10:11:46,172 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,193 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:11:46,195 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 10:11:46,197 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 10:11:46,197 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,217 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:11:46,219 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 10:11:46,222 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 10:11:46,222 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:46,242 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:11:46,242 DEBUG: all custom handlers loaded
2011-10-17 10:11:46,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:11:46,435 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 10:11:46,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:11:46,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:46,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:11:46,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:11:46,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:11:46,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:11:46,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:11:46,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:46,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:11:46,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 10:11:46,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 10:11:46,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:11:46,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:11:46,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:46,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:11:46,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:11:46,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:11:46,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:11:46,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 10:11:46,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:11:46,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:11:46,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:11:46,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 10:11:46,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 10:11:46,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:46,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2011-10-17 10:11:46,941 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,005 DEBUG: KMH enabled: True
2011-10-17 10:11:46,730 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:11:47,049 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:47,073 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,115 DEBUG: KMH enabled: True
2011-10-17 10:11:47,060 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:11:47,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 10:11:47,171 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,171 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:11:47,158 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:11:47,173 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:11:47,175 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:47,199 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,199 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:11:47,186 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:11:47,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 10:11:47,211 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,254 DEBUG: KMH enabled: True
2011-10-17 10:11:47,199 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:11:47,300 DEBUG: nvidia.available: falling back to default
2011-10-17 10:11:47,323 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,365 DEBUG: KMH enabled: True
2011-10-17 10:11:47,310 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:11:47,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:11:47,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:11:47,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:11:47,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:11:47,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:11:47,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:11:47,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 10:11:47,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:11:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:11:47,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 10:11:47,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:11:47,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 10:11:47,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:11:47,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:11:47,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:11:47,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:11:47,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 10:11:47,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:11:47,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:11:47,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:11:47,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:11:47,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:11:47,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:11:47,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:11:47,446 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 10:11:47,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,446 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 10:11:47,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:11:47,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:11:47,452 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 10:11:47,452 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:11:47,452 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,452 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:11:47,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:11:47,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 10:11:47,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:11:47,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:11:47,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:11:47,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:11:47,456 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:11:47,456 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,456 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:11:47,456 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:11:47,457 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:11:47,457 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,457 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 10:11:47,457 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:11:47,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:11:47,459 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 10:11:47,459 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:11:47,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 10:11:47,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:11:47,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:11:47,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:11:47,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,460 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:11:47,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,461 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:11:47,461 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:11:47,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:11:47,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:11:47,467 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 10:11:47,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,467 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 10:11:47,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:11:47,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:11:47,467 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:11:47,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:11:47,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:11:47,470 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:11:47,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb732b64c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:11:47,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:11:47,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:11:47,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a1f6ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:11:47,527 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:47,527 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:11:48,186 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:48,228 DEBUG: KMH enabled: True
2011-10-17 10:11:48,895 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:48,895 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:11:48,933 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:48,933 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:11:48,960 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:11:49,002 DEBUG: KMH enabled: True
2011-10-17 10:11:51,356 DEBUG: Shutting down
2011-10-17 10:27:22,812 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c>
2011-10-17 10:27:23,855 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 10:27:23,923 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 10:27:23,923 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 10:27:23,944 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 10:27:23,977 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 10:27:23,985 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 10:27:24,020 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 10:27:24,020 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 10:27:24,020 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 10:27:24,062 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 10:27:24,063 DEBUG: Firmware for DVB cards not available
2011-10-17 10:27:24,064 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 10:27:24,075 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 10:27:24,083 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 10:27:24,083 DEBUG: fglrx.available: falling back to default
2011-10-17 10:27:24,188 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:27:24,195 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 10:27:24,202 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 10:27:24,203 DEBUG: fglrx.available: falling back to default
2011-10-17 10:27:24,271 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 10:27:24,271 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 10:27:24,280 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 10:27:24,281 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 10:27:24,281 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 10:27:24,281 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 10:27:24,288 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 10:27:24,289 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 10:27:24,324 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 10:27:24,324 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 10:27:24,361 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 10:27:24,377 DEBUG: Software modem not available
2011-10-17 10:27:24,377 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 10:27:24,390 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 10:27:24,398 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 10:27:24,398 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,465 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:27:24,472 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:27:24,480 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 10:27:24,480 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,548 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:27:24,555 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 10:27:24,563 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 10:27:24,563 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,631 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:27:24,631 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 10:27:24,646 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 10:27:24,647 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,716 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:27:24,723 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 10:27:24,731 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 10:27:24,731 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,799 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:27:24,805 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 10:27:24,813 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 10:27:24,814 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:24,881 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:27:24,882 DEBUG: all custom handlers loaded
2011-10-17 10:27:24,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:27:25,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 10:27:25,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:27:25,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:25,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:27:25,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:27:25,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:27:25,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:27:25,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:27:25,145 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:25,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:27:25,145 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 10:27:25,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,145 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 10:27:25,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:27:25,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:27:25,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:25,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:27:25,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:27:25,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:27:25,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:27:25,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 10:27:25,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:27:25,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:27:25,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:27:25,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 10:27:25,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 10:27:25,350 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:25,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2011-10-17 10:27:25,374 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:25,427 DEBUG: KMH enabled: True
2011-10-17 10:27:25,350 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:27:25,477 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:25,551 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:25,608 DEBUG: KMH enabled: True
2011-10-17 10:27:25,507 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:27:25,652 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 10:27:25,681 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:25,682 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:25,652 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:27:25,688 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:27:25,696 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:25,774 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:25,775 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:25,731 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:27:25,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 10:27:25,818 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:25,873 DEBUG: KMH enabled: True
2011-10-17 10:27:25,776 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:27:25,923 DEBUG: nvidia.available: falling back to default
2011-10-17 10:27:25,995 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:26,052 DEBUG: KMH enabled: True
2011-10-17 10:27:25,951 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, enabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:27:26,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:27:26,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:27:26,130 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:27:26,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:27:26,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:27:26,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:27:26,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 10:27:26,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:27:26,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:27:26,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:27:26,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:27:26,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:27:26,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:27:26,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 10:27:26,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:27:26,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 10:27:26,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:27:26,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:27:26,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:27:26,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:27:26,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 10:27:26,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:27:26,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:27:26,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:27:26,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:27:26,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:27:26,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:27:26,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:27:26,151 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 10:27:26,151 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,152 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 10:27:26,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:27:26,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:27:26,157 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 10:27:26,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:27:26,157 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:27:26,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:27:26,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 10:27:26,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:27:26,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:27:26,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:27:26,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:27:26,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:27:26,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:27:26,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:27:26,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:27:26,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 10:27:26,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:27:26,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:27:26,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 10:27:26,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:27:26,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 10:27:26,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:27:26,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:27:26,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:27:26,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:27:26,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:27:26,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:27:26,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:27:26,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:27:26,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 10:27:26,172 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 10:27:26,172 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:27:26,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:27:26,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,172 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:27:26,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:27:26,174 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:27:26,175 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:27:26,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a064c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:27:26,175 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:27:26,176 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:27:26,177 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:27:26,178 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a946ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:27:26,230 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:26,231 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:26,901 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:26,958 DEBUG: KMH enabled: True
2011-10-17 10:27:27,700 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:27,701 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:27,831 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:27,832 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:27,922 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:27,987 DEBUG: KMH enabled: True
2011-10-17 10:27:30,396 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-17 10:27:30,397 DEBUG: nvidia_current is not the alternative in use
2011-10-17 10:27:32,594 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:27:32,595 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 10:28:04,521 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:04,522 DEBUG: KMH enabled: False
2011-10-17 10:28:04,570 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:04,570 DEBUG: KMH enabled: False
2011-10-17 10:28:07,535 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:07,535 DEBUG: KMH enabled: False
2011-10-17 10:28:07,583 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:07,584 DEBUG: KMH enabled: False
2011-10-17 10:28:07,759 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:07,759 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:28:07,870 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:07,871 DEBUG: KMH enabled: False
2011-10-17 10:28:07,919 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:07,920 DEBUG: KMH enabled: False
2011-10-17 10:28:08,112 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:08,112 DEBUG: KMH enabled: False
2011-10-17 10:28:08,165 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:28:08,165 DEBUG: KMH enabled: False
2011-10-17 10:29:53,210 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c>
2011-10-17 10:29:54,271 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 10:29:54,339 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 10:29:54,339 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 10:29:54,360 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 10:29:54,371 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 10:29:54,373 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 10:29:54,383 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 10:29:54,383 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 10:29:54,383 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 10:29:54,396 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 10:29:54,397 DEBUG: Firmware for DVB cards not available
2011-10-17 10:29:54,397 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 10:29:54,400 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 10:29:54,402 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 10:29:54,403 DEBUG: fglrx.available: falling back to default
2011-10-17 10:29:54,471 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:29:54,473 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 10:29:54,476 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 10:29:54,476 DEBUG: fglrx.available: falling back to default
2011-10-17 10:29:54,496 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 10:29:54,497 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 10:29:54,499 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 10:29:54,499 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 10:29:54,500 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 10:29:54,500 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 10:29:54,502 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 10:29:54,502 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 10:29:54,514 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 10:29:54,514 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 10:29:54,526 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 10:29:54,531 DEBUG: Software modem not available
2011-10-17 10:29:54,531 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 10:29:54,535 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 10:29:54,537 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 10:29:54,537 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,558 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:29:54,560 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:29:54,563 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 10:29:54,563 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,583 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:29:54,585 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 10:29:54,587 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 10:29:54,587 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,608 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:29:54,608 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 10:29:54,612 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 10:29:54,613 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,633 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:29:54,635 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 10:29:54,637 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 10:29:54,637 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,657 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:29:54,659 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 10:29:54,662 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 10:29:54,662 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:54,682 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:29:54,682 DEBUG: all custom handlers loaded
2011-10-17 10:29:54,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:29:54,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 10:29:54,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:29:54,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:54,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:29:54,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:29:54,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:29:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:29:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:29:54,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:54,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:29:54,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 10:29:54,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 10:29:54,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:29:54,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:29:54,985 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:54,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:29:54,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:29:54,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:29:54,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:29:54,991 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 10:29:54,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:54,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:29:54,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:29:54,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:29:55,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 10:29:55,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 10:29:55,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2011-10-17 10:29:55,417 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,417 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:29:55,182 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:29:55,419 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:55,443 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,443 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:29:55,430 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:29:55,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 10:29:55,455 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,456 DEBUG: KMH enabled: False
2011-10-17 10:29:55,443 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:29:55,458 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:29:55,460 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:55,483 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,483 DEBUG: KMH enabled: False
2011-10-17 10:29:55,470 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:29:55,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 10:29:55,496 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,496 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:29:55,483 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:29:55,498 DEBUG: nvidia.available: falling back to default
2011-10-17 10:29:55,522 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,522 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:29:55,509 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:29:55,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:29:55,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:29:55,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:29:55,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:29:55,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:29:55,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:29:55,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 10:29:55,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:29:55,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:29:55,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:29:55,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:29:55,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:29:55,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:29:55,547 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 10:29:55,547 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:29:55,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 10:29:55,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:29:55,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:29:55,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:29:55,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:29:55,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 10:29:55,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:29:55,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:29:55,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:29:55,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:29:55,553 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:29:55,553 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,553 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:29:55,553 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:29:55,562 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 10:29:55,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,563 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 10:29:55,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:29:55,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:29:55,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 10:29:55,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:29:55,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:29:55,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:29:55,570 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 10:29:55,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:29:55,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:29:55,571 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:29:55,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:29:55,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:29:55,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:29:55,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:29:55,574 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:29:55,574 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,574 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 10:29:55,574 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:29:55,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:29:55,576 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 10:29:55,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:29:55,576 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 10:29:55,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:29:55,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:29:55,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:29:55,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:29:55,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:29:55,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:29:55,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:29:55,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:29:55,583 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 10:29:55,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 10:29:55,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:29:55,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:29:55,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:29:55,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:29:55,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:29:55,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:29:55,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731764c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:29:55,587 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:29:55,588 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:29:55,589 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:29:55,590 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a0b6ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:29:55,666 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:55,666 DEBUG: KMH enabled: False
2011-10-17 10:29:56,341 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:56,341 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:29:56,936 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:56,936 DEBUG: KMH enabled: False
2011-10-17 10:29:56,972 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:56,972 DEBUG: KMH enabled: False
2011-10-17 10:29:56,997 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:29:56,998 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:30:01,065 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:01,065 DEBUG: KMH enabled: False
2011-10-17 10:30:01,433 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:01,433 DEBUG: KMH enabled: False
2011-10-17 10:30:01,691 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:01,691 DEBUG: KMH enabled: False
2011-10-17 10:30:01,872 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:01,872 DEBUG: KMH enabled: False
2011-10-17 10:30:02,021 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:02,021 DEBUG: KMH enabled: False
2011-10-17 10:30:02,191 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:02,191 DEBUG: KMH enabled: False
2011-10-17 10:30:02,989 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:02,990 DEBUG: KMH enabled: False
2011-10-17 10:30:04,859 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:30:04,859 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 10:30:21,982 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:21,982 DEBUG: KMH enabled: False
2011-10-17 10:30:21,996 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:21,996 DEBUG: KMH enabled: False
2011-10-17 10:30:27,176 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,177 DEBUG: KMH enabled: False
2011-10-17 10:30:27,190 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,191 DEBUG: KMH enabled: False
2011-10-17 10:30:27,218 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,218 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:30:27,246 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,247 DEBUG: KMH enabled: False
2011-10-17 10:30:27,261 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,261 DEBUG: KMH enabled: False
2011-10-17 10:30:27,298 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,298 DEBUG: KMH enabled: False
2011-10-17 10:30:27,312 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,312 DEBUG: KMH enabled: False
2011-10-17 10:30:27,338 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:30:27,338 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:30:28,272 DEBUG: Shutting down
2011-10-17 10:32:08,542 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c>
2011-10-17 10:32:09,613 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 10:32:09,682 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 10:32:09,683 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 10:32:09,704 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 10:32:09,714 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 10:32:09,717 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 10:32:09,727 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 10:32:09,727 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 10:32:09,727 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 10:32:09,740 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 10:32:09,740 DEBUG: Firmware for DVB cards not available
2011-10-17 10:32:09,741 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 10:32:09,744 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 10:32:09,747 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 10:32:09,747 DEBUG: fglrx.available: falling back to default
2011-10-17 10:32:09,817 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:32:09,819 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 10:32:09,821 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 10:32:09,821 DEBUG: fglrx.available: falling back to default
2011-10-17 10:32:09,842 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 10:32:09,842 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 10:32:09,845 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 10:32:09,845 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 10:32:09,845 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 10:32:09,845 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 10:32:09,848 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 10:32:09,848 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 10:32:09,858 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 10:32:09,858 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 10:32:09,869 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 10:32:09,874 DEBUG: Software modem not available
2011-10-17 10:32:09,874 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 10:32:09,878 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 10:32:09,880 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 10:32:09,881 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:09,901 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:32:09,903 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:32:09,905 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 10:32:09,905 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:09,925 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:32:09,927 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 10:32:09,930 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 10:32:09,930 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:09,950 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:32:09,950 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 10:32:09,955 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 10:32:09,955 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:09,975 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:32:09,977 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 10:32:09,979 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 10:32:09,979 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:09,999 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 10:32:10,001 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 10:32:10,004 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 10:32:10,004 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:10,024 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 10:32:10,024 DEBUG: all custom handlers loaded
2011-10-17 10:32:10,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:32:10,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 10:32:10,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:32:10,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:32:10,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:32:10,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:32:10,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:32:10,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:32:10,308 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:32:10,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 10:32:10,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 10:32:10,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:32:10,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:32:10,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:32:10,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:32:10,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:32:10,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:32:10,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 10:32:10,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:32:10,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:32:10,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:32:10,526 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 10:32:10,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,526 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 10:32:10,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,526 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2011-10-17 10:32:10,729 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,729 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:10,526 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:32:10,732 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:10,755 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,755 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:10,742 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:32:10,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 10:32:10,768 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,769 DEBUG: KMH enabled: False
2011-10-17 10:32:10,756 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:32:10,771 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 10:32:10,773 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:10,797 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,797 DEBUG: KMH enabled: False
2011-10-17 10:32:10,784 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 10:32:10,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 10:32:10,810 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,810 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:10,797 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:32:10,813 DEBUG: nvidia.available: falling back to default
2011-10-17 10:32:10,836 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,836 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:10,823 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 10:32:10,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:32:10,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:32:10,857 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:32:10,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:32:10,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:32:10,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:32:10,860 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 10:32:10,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:32:10,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:32:10,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:32:10,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:32:10,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:32:10,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:32:10,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 10:32:10,863 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:32:10,865 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 10:32:10,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:32:10,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:32:10,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:32:10,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:32:10,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 10:32:10,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:32:10,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:32:10,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:32:10,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:32:10,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:32:10,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 10:32:10,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:32:10,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 10:32:10,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 10:32:10,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:32:10,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:32:10,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 10:32:10,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:32:10,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:32:10,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:32:10,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 10:32:10,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:32:10,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:32:10,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:32:10,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:32:10,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:32:10,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 10:32:10,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:32:10,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 10:32:10,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 10:32:10,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:32:10,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:32:10,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 10:32:10,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:32:10,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 10:32:10,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:32:10,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:32:10,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:32:10,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:32:10,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,895 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 10:32:10,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:32:10,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:32:10,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:32:10,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 10:32:10,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 10:32:10,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:32:10,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:32:10,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:32:10,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:32:10,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 10:32:10,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb731564c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 10:32:10,905 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 10:32:10,906 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 10:32:10,907 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 10:32:10,908 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a096ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 10:32:10,952 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:10,952 DEBUG: KMH enabled: False
2011-10-17 10:32:11,612 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:11,612 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:12,184 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:12,185 DEBUG: KMH enabled: False
2011-10-17 10:32:12,220 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:12,220 DEBUG: KMH enabled: False
2011-10-17 10:32:12,245 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:12,245 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:13,714 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:13,715 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 10:32:14,462 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:14,463 DEBUG: KMH enabled: False
2011-10-17 10:32:14,867 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 10:32:14,867 DEBUG: KMH enabled: False
2011-10-17 10:32:15,996 DEBUG: Shutting down
2011-10-17 14:18:05,779 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c>
2011-10-17 14:18:07,032 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-17 14:18:07,131 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-17 14:18:07,139 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-17 14:18:07,167 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-17 14:18:07,206 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-17 14:18:07,267 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-17 14:18:07,313 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-17 14:18:07,314 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-17 14:18:07,314 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-17 14:18:07,368 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-17 14:18:07,369 DEBUG: Firmware for DVB cards not available
2011-10-17 14:18:07,370 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-17 14:18:07,411 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-17 14:18:07,418 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-17 14:18:07,418 DEBUG: fglrx.available: falling back to default
2011-10-17 14:18:07,575 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 14:18:07,582 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-17 14:18:07,589 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-17 14:18:07,590 DEBUG: fglrx.available: falling back to default
2011-10-17 14:18:07,658 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-17 14:18:07,659 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-17 14:18:07,667 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-17 14:18:07,668 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-17 14:18:07,669 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-17 14:18:07,669 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-17 14:18:07,676 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-17 14:18:07,677 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-17 14:18:07,727 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-17 14:18:07,727 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-17 14:18:07,765 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-17 14:18:07,794 DEBUG: Software modem not available
2011-10-17 14:18:07,795 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-17 14:18:07,808 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-17 14:18:07,816 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-17 14:18:07,817 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:07,888 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 14:18:07,895 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 14:18:07,903 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-17 14:18:07,903 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:07,973 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 14:18:07,980 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-17 14:18:07,988 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-17 14:18:07,989 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:08,058 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 14:18:08,058 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-17 14:18:08,123 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-17 14:18:08,123 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:08,193 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 14:18:08,200 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-17 14:18:08,208 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-17 14:18:08,209 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:08,278 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-17 14:18:08,285 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-17 14:18:08,293 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-17 14:18:08,293 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:08,363 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-17 14:18:08,363 DEBUG: all custom handlers loaded
2011-10-17 14:18:08,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 14:18:08,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-17 14:18:08,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 14:18:08,685 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:08,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 14:18:08,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 14:18:08,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 14:18:08,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 14:18:08,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 14:18:08,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:08,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 14:18:08,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-17 14:18:08,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-17 14:18:08,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 14:18:08,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 14:18:08,703 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:08,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 14:18:08,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 14:18:08,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 14:18:08,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 14:18:08,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-17 14:18:08,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 14:18:08,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 14:18:08,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 14:18:08,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-17 14:18:08,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-17 14:18:08,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:08,893 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates'}
2011-10-17 14:18:09,276 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,276 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:08,893 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 14:18:09,284 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:09,368 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,368 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:09,322 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 14:18:09,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-17 14:18:09,414 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,415 DEBUG: KMH enabled: False
2011-10-17 14:18:09,369 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 14:18:09,422 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 14:18:09,430 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:09,506 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,507 DEBUG: KMH enabled: False
2011-10-17 14:18:09,466 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-17 14:18:09,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-17 14:18:09,545 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,546 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:09,508 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 14:18:09,554 DEBUG: nvidia.available: falling back to default
2011-10-17 14:18:09,635 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,635 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:09,589 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-17 14:18:09,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 14:18:09,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 14:18:09,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 14:18:09,670 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 14:18:09,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 14:18:09,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 14:18:09,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-10-17 14:18:09,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 14:18:09,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 14:18:09,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 14:18:09,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 14:18:09,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 14:18:09,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 14:18:09,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2011-10-17 14:18:09,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 14:18:09,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-17 14:18:09,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 14:18:09,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 14:18:09,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 14:18:09,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 14:18:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-17 14:18:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 14:18:09,679 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,679 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 14:18:09,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 14:18:09,679 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 14:18:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 14:18:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-17 14:18:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 14:18:09,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-17 14:18:09,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2011-10-17 14:18:09,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 14:18:09,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 14:18:09,696 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-10-17 14:18:09,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 14:18:09,696 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 14:18:09,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 14:18:09,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-10-17 14:18:09,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 14:18:09,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 14:18:09,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 14:18:09,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 14:18:09,701 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 14:18:09,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,701 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-17 14:18:09,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 14:18:09,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-17 14:18:09,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-17 14:18:09,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 14:18:09,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 14:18:09,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-17 14:18:09,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 14:18:09,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-17 14:18:09,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 14:18:09,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 14:18:09,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 14:18:09,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 14:18:09,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-17 14:18:09,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 14:18:09,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'platform:eisa')
2011-10-17 14:18:09,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 14:18:09,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-17 14:18:09,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-17 14:18:09,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 14:18:09,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 14:18:09,713 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 14:18:09,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,715 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 14:18:09,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-17 14:18:09,715 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb725664c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd000004B6bc07sc80i00')
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-17 14:18:09,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001028sd000004B6bc0Csc03i20')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0003v0408p2FB1e0901-e0,1,kD4,ramlsfw')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:dcdbas')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001028sd000004B6bc02sc00i00')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:regulatory')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v000010DEd00000DF5sv00001028sd000004B6bc03sc00i00')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-669A0C200008')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc00ip00')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:SMO8800:')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd000004B6bc03sc00i00')
2011-10-17 14:18:09,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d0000008Asv00008086sd00005325bc02sc80i00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd000004B6bc0Csc05i00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip02')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd000004B6bc04sc03i00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd05/04/2011:svnDellInc.:pnDellSystemXPSL502X:pvr:rvnDellInc.:rn0YR8NN:rvrA00:cvnDellInc.:ct8:cvr0.1:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc01ip00')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:DLL04B6:PNP0F13:')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-10-17 14:18:09,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd000004B6bc01sc06i01')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v046DpC52Bd1300dc00dsc00dp00ic03isc01ip01')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd000004B6bc06sc01i00')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001028sd000004B6bc0Csc03i30')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v0408p2FB1d0901dcEFdsc02dp01ic0Eisc02ip00')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'platform:eisa')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd000004B6bc0Csc03i20')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-17 14:18:09,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694c6ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-17 14:18:09,786 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:09,786 DEBUG: KMH enabled: False
2011-10-17 14:18:10,538 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:10,539 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:11,219 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:11,220 DEBUG: KMH enabled: False
2011-10-17 14:18:11,323 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:11,323 DEBUG: KMH enabled: False
2011-10-17 14:18:11,411 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:11,412 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:12,649 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:12,650 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-17 14:18:13,301 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:13,301 DEBUG: KMH enabled: False
2011-10-17 14:18:15,164 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:15,164 DEBUG: KMH enabled: False
2011-10-17 14:18:17,731 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-17 14:18:17,732 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-17 14:18:49,803 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:49,804 DEBUG: KMH enabled: False
2011-10-17 14:18:49,855 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-17 14:18:49,855 DEBUG: KMH enabled: False
```

---

### Post by haresear on 2011-10-17
There has been an update to jockey-gtk since the 11.10 release iso -- you might want to try updating before trying to install the nvidia proprietary drivers via jockey-gtk.

---

