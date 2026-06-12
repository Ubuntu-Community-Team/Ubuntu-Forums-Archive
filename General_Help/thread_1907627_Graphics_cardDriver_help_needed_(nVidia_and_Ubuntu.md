---
title: "Graphics card/Driver help needed (nVidia and Ubuntu Lucid)"
date: 2012-01-11
forum: General Help
---

### Post by Kir_B on 2012-01-11
I purchased a new graphics card quite some time ago and after sending my computer in for servicing (I was convinced that this was a faulty motherboard issue), I have learnt that this actually an issue with Ubuntu (or more accurately, my installation), because when I ran the Linux Mint 11 LiveCD, it's hardware jockey recognized the card immediately, where as in my installation, the hardware jockey just tells me that there are "no proprietary drivers are in use on this system"!

Here's the pertinent details:
The motherboard is an ASUS M4A89GTD Pro/USB3.
I did a fresh install of Ubuntu 10.04, but at the time I didn't have the new graphics card (an MSI GTS450), so the fresh install was done while using the onboard ATI graphics (Radeon HD 4290). I'm currently using the open source drivers, but I have tried out ATI's drivers repeatedly over the last year, or so (hoping that they would at some point provide us with an up to date version).

Please, someone tell me that I don't need to do a fresh install to solve this issue.

Thanks a tonne in advance.
Kirby

---

### Post by grahammechanical on 2012-01-11
The distributors of Ubuntu believe very strongly in the Free Open Source Software (FOSS) philosophy. Ubuntu does not install closed source or proprietary software by default or as standard. Other Linux distributors have no such qualms.

Ubuntu at installation time asks us if we want to install proprietary codecs licensed by Ubuntu. But as for video drivers we install them after installation using a utility called Additional Drivers.

In your case you installed Ubuntu with an ATI video card and have now put in a Nvidia card. Can you see the problem? Ubuntu recognised your card alright and it is correct in saying that there are not proprietary drivers in use. But then again I remember a couple of years back getting that message on my system when I knew that I was using the Nvidia driver. The message was faulty.

So, do you have a Nvidia driver installed and does the Additional Drivers utility say the driver is activated? When we install a Nvidia driver it also installs a Nvidia X-Server Settings utility. Do you have one of those?

Regards.

---

### Post by topsites on 2012-01-11
The only difference is that you went from Radeon > Nvidia while I stayed brand loyal but I just replaced my 8600gs with a N550gtx-ti and experienced that same not so very nice blank screen problem...

What I had to do was first remove the new card and re-install the old one so I'd at least have a screen!
Granted you don't have to do this if you are comfortable using command-line interfaces you can simply Ctrl-Alt-F1
But I tried that and apparently I am not that good with command line interfaces.

So then once I could actually boot to where I could SEE my desktop again I REMOVED the Additional drivers.
Shut down.
Removed the old card and installed the new one.
Then Rebooted and went back to Additional drivers and let Ubuntu pick the right one, installed it.

All went well.

In summary and to save a headache in the future, before removing the old card, UNINSTALL the drivers.

One other thing:
Newer Nvidia cards will FAIL to boot if the fan isn't plugged in (thankfully) so make sure that is spinning.

---

### Post by Kir_B on 2012-01-11
> **grahammechanical said:**
> The distributors of Ubuntu believe very strongly in the Free Open Source Software (FOSS) philosophy. Ubuntu does not install closed source or proprietary software by default or as standard. Other Linux distributors have no such qualms.

Ubuntu at installation time asks us if we want to install proprietary codecs licensed by Ubuntu. But as for video drivers we install them after installation using a utility called Additional Drivers.

In your case you installed Ubuntu with an ATI video card and have now put in a Nvidia card. Can you see the problem? Ubuntu recognised your card alright and it is correct in saying that there are not proprietary drivers in use. But then again I remember a couple of years back getting that message on my system when I knew that I was using the Nvidia driver. The message was faulty.

Regards.

Thanks so much for the response.

"hardware jockey just tells me that there are "no proprietary drivers are in use on this system"

Sorry, I guess it's called "Additional drivers" now, where as in my installation, it is called "Hardware Drivers", but in the past I've seen people refer to it as the "Hardware Jockey".

Sorry for any confusion that I may have caused.

So, when I bring up "Additional Drivers" (Hardware Drivers is the applications name in my Administration menu), the application does a scan for additional drivers before showing the driver selection window and when the scan is finished the App says "no proprietary drivers are in use on this system" and there are no drivers to be selected either, unlike my experiences in the past.

I do understand what you are saying about the system using the former setup with the open source driver, which I'm sure isn't meant to run both nVidia and ATI's cards. So I guess my question is, How does a person undo the old ATI setup and get the new nVidia card to work with either the open source driver stack, or the proprietary drivers. I'd really like to try out both, but if the open source drivers work as well as they did with the onboard ATI Radeon HD 4290, I'll probably stick to those to avoid the problems I've encountered in the past (suddenly un-bootable systems!).

> So, do you have a Nvidia driver installed and does the Additional  Drivers utility say the driver is activated? When we install a Nvidia  driver it also installs a Nvidia X-Server Settings utility. Do you have  one of those?The answer to that question is: No and no.
Thanks again.
Kirby

---

### Post by Kir_B on 2012-01-11
> **topsites said:**
> The only difference is that you went from Radeon > Nvidia while I stayed brand loyal but I just replaced my 8600gs with a N550gtx-ti and experienced that same not so very nice blank screen problem...

What I had to do was first remove the new card and re-install the old one so I'd at least have a screen!
Granted you don't have to do this if you are comfortable using command-line interfaces you can simply Ctrl-Alt-F1
But I tried that and apparently I am not that good with command line interfaces.

So then once I could actually boot to where I could SEE my desktop again I REMOVED the Additional drivers.
Shut down.
Removed the old card and installed the new one.
Then Rebooted and went back to Additional drivers and let Ubuntu pick the right one, installed it.

All went well.

One other thing:
Newer Nvidia cards will FAIL to boot if the fan isn't plugged in (thankfully) so make sure that is spinning.

Thanks for the info.

> In summary and to save a headache in the future, before removing the old card, UNINSTALL the drivers.

The problem with that, is that I have absoluteley no idea what I should do in this case and am more than a little nervous about messing with drivers, especially without some kiind of documentation to guide me (two years using Ubuntu and I still feel like a complete greenhorn!).

Should I just simply uninstall the open source driver? And what package would I be looking for?

Thanks again for the help.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-11
so you switched from a ati gpu to a nvida gpu?
```
sudo apt-get purge fgrlx
sudo rm /etc/X11/xorg.conf
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```line 3 is only needed if you have not added that ppa already
that should get everything working
in the event of a horrible failure from recovery mode (if you cant get to the main login)
```
sudo apt-get install ppa-purge;sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

EDIT:
use **nomodeset** in your kernels boot paramaters

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> so you switched from a ati gpu to a nvida gpu?

Well, not ATI's driver, but the open source driver, and yes I'm switching fro the onboards ATI graphics to an nVidia add-on card.

> ```
sudo apt-get purge fgrlx
sudo rm /etc/X11/xorg.conf
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```line 3 is only needed if you have not added that ppa already
that should get everything working
in the event of a horrible failure from recovery mode (if you cant get to the main login)
```
sudo apt-get install ppa-purge;sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

Awesome info! Thanks a metric tonne! I'll get started on it as soon as I'm done typing my response.

> EDIT:
use **nomodeset** in your kernels boot paramaters

And that does what exactly?

Thanks yet again. I'll let you all know if it works.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-11
it prevents the open source nvidia drive from causing problems loading the closed source one tends to solve the driver not in use error for me a lot

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> it prevents the open source nvidia drive from causing problems loading the closed source one tends to solve the driver not in use error for me a lot

Thanks. I thought I knew a long time ago, but it turns out I had no idea.

Thanks
Kirby

---

### Post by Kir_B on 2012-01-11
[FONT=monospace]Well, the following worked... Somewhat.
[/FONT]> [FONT=monospace]
[/FONT]sudo apt-get purge fgrlx
sudo rm /etc/X11/xorg.conf
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot The driver is installed, but the hardware jockey will not allow me to activate it (see log at the bottom) and when I try to set the monitor resolution (via preferences>monitors), which is the only method available (nvidia-settings isn't in the menu yet for some odd reason), it tells me I have to use the "nvidia-settings", but when it opens, there are next to no options and certainly nothing that would allow me to change the monitor resolution.

I'm more than a little bit puzzled.

Thanks again for the help.
Kirby

```
2012-01-11 14:53:09,092 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec>
2012-01-11 14:53:09,092 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 14:53:09,202 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 14:53:09,211 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 14:53:09,234 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 14:53:09,244 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 14:53:09,246 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 14:53:09,252 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 14:53:09,267 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 14:53:09,468 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 14:53:09,540 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 14:53:09,540 DEBUG: Firmware for DVB cards not available
2012-01-11 14:53:09,540 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 14:53:09,562 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 14:53:09,562 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 14:53:09,569 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 14:53:09,569 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 14:53:09,572 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 14:53:09,572 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 14:53:09,572 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 14:53:09,572 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 14:53:09,576 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 14:53:09,576 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 14:53:09,582 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:53:09,584 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-11 14:53:09,584 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 14:53:09,591 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:53:09,591 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 14:53:09,600 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 14:53:09,600 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 14:53:09,606 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:53:09,606 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 14:53:09,655 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 14:53:09,655 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 14:53:09,672 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 14:53:09,672 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 14:53:09,672 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 14:53:09,678 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 14:53:09,709 DEBUG: Software modem not available
2012-01-11 14:53:09,709 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 14:53:09,711 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 14:53:09,717 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 14:53:09,717 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 14:53:09,717 DEBUG: all custom handlers loaded
2012-01-11 14:53:09,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 14:53:09,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 14:53:10,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 14:53:10,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 14:53:10,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 14:53:10,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 14:53:10,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 14:53:10,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 14:53:10,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 14:53:10,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 14:53:10,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 14:53:10,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,339 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 14:53:10,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 14:53:10,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 14:53:10,362 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 14:53:10,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 14:53:10,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 14:53:10,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 14:53:10,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 14:53:10,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 14:53:10,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 14:53:10,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:53:10,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 14:53:10,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:53:10,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 14:53:10,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 14:53:10,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 14:53:10,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:53:10,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 14:53:10,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 14:53:10,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 14:53:10,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 14:53:10,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 14:53:10,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 14:53:10,396 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 14:53:10,396 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:53:10,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 14:53:10,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 14:53:10,440 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 14:53:10,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 14:53:10,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 14:53:10,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 14:53:10,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:53:10,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 14:53:10,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 14:53:10,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 14:53:10,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 14:53:10,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 14:53:10,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:53:10,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 14:53:10,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 14:53:10,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 14:53:10,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 14:53:10,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcfec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'platform:eisa')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:device:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:53:10,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 14:53:10,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 14:53:10,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8aeb8cc> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 14:53:15,246 DEBUG: Shutting down
2012-01-11 14:57:41,956 WARNING: cannot connect to cups; printer detection is not available
2012-01-11 14:57:41,958 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec>
2012-01-11 14:57:41,959 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 14:57:42,043 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 14:57:42,052 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 14:57:42,077 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 14:57:42,085 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 14:57:42,087 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 14:57:42,092 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 14:57:42,097 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 14:57:42,304 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 14:57:42,358 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 14:57:42,358 DEBUG: Firmware for DVB cards not available
2012-01-11 14:57:42,359 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 14:57:42,378 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 14:57:42,378 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 14:57:42,384 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 14:57:42,384 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 14:57:42,387 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 14:57:42,387 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 14:57:42,387 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 14:57:42,387 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 14:57:42,391 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 14:57:42,391 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 14:57:42,398 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:57:42,400 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-11 14:57:42,400 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 14:57:42,407 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:57:42,407 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 14:57:42,416 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 14:57:42,416 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 14:57:42,421 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 14:57:42,422 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 14:57:42,453 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 14:57:42,453 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 14:57:42,462 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 14:57:42,463 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 14:57:42,463 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 14:57:42,469 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 14:57:42,499 DEBUG: Software modem not available
2012-01-11 14:57:42,499 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 14:57:42,502 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 14:57:42,507 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 14:57:42,508 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 14:57:42,508 DEBUG: all custom handlers loaded
2012-01-11 14:57:42,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 14:57:42,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 14:57:42,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:42,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:42,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 14:57:42,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 14:57:42,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 14:57:42,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 14:57:42,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 14:57:42,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:42,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 14:57:42,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:42,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 14:57:42,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:42,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 14:57:42,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 14:57:43,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 14:57:43,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 14:57:43,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 14:57:43,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 14:57:43,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 14:57:43,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 14:57:43,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:57:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 14:57:43,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:57:43,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 14:57:43,179 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 14:57:43,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 14:57:43,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:57:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 14:57:43,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 14:57:43,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 14:57:43,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 14:57:43,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 14:57:43,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 14:57:43,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 14:57:43,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:57:43,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 14:57:43,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 14:57:43,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 14:57:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 14:57:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 14:57:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 14:57:43,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:57:43,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 14:57:43,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 14:57:43,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 14:57:43,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 14:57:43,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 14:57:43,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:57:43,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 14:57:43,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 14:57:43,286 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,286 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 14:57:43,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 14:57:43,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9432fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 14:57:43,289 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'platform:eisa')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:device:')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 14:57:43,290 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 14:57:43,291 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 14:57:43,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 14:57:43,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 14:57:43,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 14:57:43,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x985950c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 14:57:45,138 DEBUG: Shutting down
2012-01-11 15:27:30,585 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec>
2012-01-11 15:27:30,594 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 15:27:30,686 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 15:27:30,695 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 15:27:30,729 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 15:27:30,737 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 15:27:30,740 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 15:27:30,745 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 15:27:30,752 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 15:27:30,960 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 15:27:31,058 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 15:27:31,059 DEBUG: Firmware for DVB cards not available
2012-01-11 15:27:31,060 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 15:27:31,093 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 15:27:31,094 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 15:27:31,117 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 15:27:31,118 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 15:27:31,126 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 15:27:31,128 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 15:27:31,128 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 15:27:31,128 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 15:27:31,140 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 15:27:31,141 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 15:27:31,165 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 15:27:31,171 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-11 15:27:31,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 15:27:31,193 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 15:27:31,193 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 15:27:31,206 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 15:27:31,207 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 15:27:31,228 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 15:27:31,228 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 15:27:31,284 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 15:27:31,284 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 15:27:31,307 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 15:27:31,308 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 15:27:31,308 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 15:27:31,325 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 15:27:31,395 DEBUG: Software modem not available
2012-01-11 15:27:31,395 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 15:27:31,404 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 15:27:31,420 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 15:27:31,421 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 15:27:31,421 DEBUG: all custom handlers loaded
2012-01-11 15:27:31,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 15:27:31,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 15:27:31,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:31,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:31,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 15:27:31,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 15:27:31,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 15:27:31,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 15:27:31,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 15:27:31,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:31,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 15:27:31,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:31,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 15:27:31,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:31,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 15:27:31,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 15:27:32,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 15:27:32,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 15:27:32,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 15:27:32,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 15:27:32,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 15:27:32,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 15:27:32,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 15:27:32,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 15:27:32,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 15:27:32,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 15:27:32,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 15:27:32,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 15:27:32,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 15:27:32,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 15:27:32,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 15:27:32,172 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 15:27:32,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 15:27:32,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 15:27:32,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 15:27:32,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 15:27:32,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 15:27:32,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 15:27:32,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 15:27:32,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 15:27:32,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 15:27:32,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 15:27:32,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 15:27:32,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 15:27:32,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 15:27:32,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 15:27:32,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 15:27:32,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 15:27:32,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 15:27:32,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 15:27:32,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 15:27:32,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 15:27:32,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 15:27:32,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 15:27:32,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 15:27:32,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 15:27:32,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9607fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'platform:eisa')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 15:27:32,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:device:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 15:27:32,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 15:27:32,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 15:27:32,274 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 15:27:32,274 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 15:27:32,274 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 15:27:32,274 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9a368cc> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 15:27:40,294 DEBUG: Shutting down
2012-01-11 16:51:22,568 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec>
2012-01-11 16:51:22,570 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 16:51:22,647 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 16:51:22,647 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 16:51:22,672 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 16:51:22,672 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 16:51:22,674 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 16:51:22,675 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 16:51:22,677 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 16:51:22,883 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 16:51:22,897 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 16:51:22,897 DEBUG: Firmware for DVB cards not available
2012-01-11 16:51:22,897 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 16:51:22,901 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 16:51:22,902 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 16:51:22,913 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 16:51:22,913 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 16:51:22,920 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 16:51:22,921 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 16:51:22,921 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 16:51:22,921 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 16:51:22,933 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 16:51:22,934 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 16:51:22,952 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 16:51:22,956 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-11 16:51:22,957 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 16:51:22,970 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 16:51:22,971 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 16:51:22,976 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 16:51:22,977 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 16:51:22,990 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 16:51:22,990 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 16:51:23,021 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 16:51:23,022 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 16:51:23,030 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 16:51:23,031 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 16:51:23,031 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 16:51:23,055 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 16:51:23,073 DEBUG: Software modem not available
2012-01-11 16:51:23,073 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 16:51:23,082 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 16:51:23,103 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 16:51:23,103 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 16:51:23,104 DEBUG: all custom handlers loaded
2012-01-11 16:51:23,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 16:51:23,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 16:51:23,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 16:51:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 16:51:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 16:51:23,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 16:51:23,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 16:51:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 16:51:23,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 16:51:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 16:51:23,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 16:51:23,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,701 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 16:51:23,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 16:51:23,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 16:51:23,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 16:51:23,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 16:51:23,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 16:51:23,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 16:51:23,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 16:51:23,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 16:51:23,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 16:51:23,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 16:51:23,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 16:51:23,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 16:51:23,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 16:51:23,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 16:51:23,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 16:51:23,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 16:51:23,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 16:51:23,748 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,748 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 16:51:23,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 16:51:23,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 16:51:23,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 16:51:23,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 16:51:23,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 16:51:23,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 16:51:23,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 16:51:23,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 16:51:23,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 16:51:23,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 16:51:23,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 16:51:23,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 16:51:23,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 16:51:23,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 16:51:23,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 16:51:23,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 16:51:23,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 16:51:23,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 16:51:23,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 16:51:23,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 16:51:23,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 16:51:23,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 16:51:23,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 16:51:23,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87c8fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 16:51:23,850 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'platform:eisa')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:device:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 16:51:23,851 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 16:51:23,852 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 16:51:23,853 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8bf78cc> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 17:17:14,858 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec>
2012-01-11 17:17:14,860 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 17:17:14,942 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 17:17:14,943 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 17:17:14,966 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 17:17:14,967 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 17:17:14,968 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 17:17:14,969 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 17:17:14,971 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 17:17:15,177 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 17:17:15,199 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 17:17:15,201 DEBUG: Firmware for DVB cards not available
2012-01-11 17:17:15,201 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 17:17:15,211 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 17:17:15,212 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 17:17:15,234 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 17:17:15,235 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 17:17:15,241 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 17:17:15,242 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 17:17:15,242 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 17:17:15,242 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 17:17:15,254 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 17:17:15,255 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 17:17:15,272 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 17:17:15,279 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-11 17:17:15,280 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 17:17:15,297 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 17:17:15,298 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 17:17:15,305 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 17:17:15,306 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 17:17:15,326 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 17:17:15,327 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 17:17:15,355 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 17:17:15,355 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 17:17:15,360 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 17:17:15,360 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 17:17:15,361 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 17:17:15,385 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 17:17:15,402 DEBUG: Software modem not available
2012-01-11 17:17:15,402 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 17:17:15,408 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 17:17:15,419 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 17:17:15,419 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 17:17:15,420 DEBUG: all custom handlers loaded
2012-01-11 17:17:15,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 17:17:15,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 17:17:15,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:15,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:15,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 17:17:15,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 17:17:15,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 17:17:15,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 17:17:15,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 17:17:15,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:15,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 17:17:15,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:15,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 17:17:15,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:15,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 17:17:15,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 17:17:16,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 17:17:16,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 17:17:16,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 17:17:16,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 17:17:16,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 17:17:16,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 17:17:16,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 17:17:16,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 17:17:16,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 17:17:16,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 17:17:16,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 17:17:16,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 17:17:16,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 17:17:16,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 17:17:16,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 17:17:16,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 17:17:16,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 17:17:16,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 17:17:16,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 17:17:16,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 17:17:16,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 17:17:16,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 17:17:16,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 17:17:16,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 17:17:16,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 17:17:16,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 17:17:16,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 17:17:16,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 17:17:16,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 17:17:16,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 17:17:16,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 17:17:16,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 17:17:16,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 17:17:16,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 17:17:16,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 17:17:16,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 17:17:16,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 17:17:16,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 17:17:16,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 17:17:16,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 17:17:16,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87e1fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 17:17:16,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 17:17:16,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'platform:eisa')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 17:17:16,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:device:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 17:17:16,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 17:17:16,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 17:17:16,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c108cc> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 17:41:04,947 DEBUG: Shutting down
2012-01-11 18:45:23,839 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec>
2012-01-11 18:45:23,850 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 18:45:23,937 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 18:45:23,947 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 18:45:23,971 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 18:45:23,980 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 18:45:23,982 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 18:45:23,987 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 18:45:24,002 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 18:45:24,206 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 18:45:24,269 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 18:45:24,269 DEBUG: Firmware for DVB cards not available
2012-01-11 18:45:24,269 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 18:45:24,289 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 18:45:24,289 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 18:45:24,297 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 18:45:24,297 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 18:45:24,299 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 18:45:24,300 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 18:45:24,300 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 18:45:24,300 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 18:45:24,303 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 18:45:24,304 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 18:45:24,311 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:45:24,336 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 18:45:24,343 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:45:24,343 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 18:45:24,352 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 18:45:24,353 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 18:45:24,359 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:45:24,359 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 18:45:24,396 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 18:45:24,397 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 18:45:24,407 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 18:45:24,407 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 18:45:24,407 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 18:45:24,414 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 18:45:24,444 DEBUG: Software modem not available
2012-01-11 18:45:24,444 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 18:45:24,447 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 18:45:24,453 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 18:45:24,453 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 18:45:24,453 DEBUG: all custom handlers loaded
2012-01-11 18:45:24,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 18:45:24,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 18:45:24,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 18:45:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 18:45:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 18:45:24,875 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 18:45:24,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 18:45:24,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:24,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 18:45:24,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:24,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 18:45:24,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:24,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 18:45:24,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 18:45:25,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 18:45:25,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 18:45:25,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 18:45:25,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 18:45:25,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 18:45:25,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 18:45:25,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,631 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:45:25,102 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-01-11 18:45:25,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 18:45:25,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 18:45:25,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 18:45:25,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 18:45:25,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:45:25,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 18:45:25,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:45:25,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 18:45:25,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 18:45:25,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 18:45:25,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:45:25,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 18:45:25,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 18:45:25,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 18:45:25,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 18:45:25,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 18:45:25,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 18:45:25,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 18:45:25,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:45:25,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 18:45:25,662 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 18:45:25,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 18:45:25,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 18:45:25,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 18:45:25,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 18:45:25,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:45:25,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 18:45:25,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 18:45:25,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 18:45:25,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 18:45:25,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 18:45:25,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:45:25,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 18:45:25,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 18:45:25,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 18:45:25,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 18:45:25,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 18:45:25,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e14fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 18:45:25,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 18:45:25,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 18:45:25,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa2439ec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 18:45:25,860 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:45:26,093 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:45:26,254 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:45:29,235 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:45:31,766 DEBUG: Shutting down
2012-01-11 18:51:56,219 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec>
2012-01-11 18:51:56,221 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic-pae/modules.alias
2012-01-11 18:51:56,301 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-01-11 18:51:56,301 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-11 18:51:56,324 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-01-11 18:51:56,325 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-01-11 18:51:56,326 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-01-11 18:51:56,327 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-01-11 18:51:56,329 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-11 18:51:56,539 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-11 18:51:56,562 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-11 18:51:56,563 DEBUG: Firmware for DVB cards not available
2012-01-11 18:51:56,563 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-11 18:51:56,573 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-11 18:51:56,574 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-11 18:51:56,598 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-11 18:51:56,598 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-11 18:51:56,604 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-11 18:51:56,605 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-11 18:51:56,605 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-11 18:51:56,605 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-11 18:51:56,617 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-11 18:51:56,618 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-11 18:51:56,645 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:51:56,649 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-11 18:51:56,661 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:51:56,662 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-11 18:51:56,667 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-11 18:51:56,668 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-11 18:51:56,682 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-11 18:51:56,683 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-01-11 18:51:56,711 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-01-11 18:51:56,712 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-01-11 18:51:56,720 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-01-11 18:51:56,720 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-01-11 18:51:56,721 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-11 18:51:56,741 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-11 18:51:56,749 DEBUG: Software modem not available
2012-01-11 18:51:56,749 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-11 18:51:56,756 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-11 18:51:56,769 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-11 18:51:56,770 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-11 18:51:56,770 DEBUG: all custom handlers loaded
2012-01-11 18:51:56,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 18:51:57,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 18:51:57,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 18:51:57,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 18:51:57,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 18:51:57,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 18:51:57,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 18:51:57,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 18:51:57,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 18:51:57,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 18:51:57,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 18:51:57,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 18:51:57,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 18:51:57,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 18:51:57,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 18:51:57,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,472 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:51:57,402 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-01-11 18:51:57,473 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 18:51:57,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 18:51:57,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 18:51:57,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 18:51:57,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:51:57,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 18:51:57,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:51:57,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 18:51:57,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 18:51:57,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 18:51:57,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:51:57,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 18:51:57,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 18:51:57,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 18:51:57,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 18:51:57,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 18:51:57,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 18:51:57,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 18:51:57,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:51:57,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 18:51:57,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 18:51:57,558 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 18:51:57,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 18:51:57,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 18:51:57,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 18:51:57,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:51:57,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 18:51:57,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 18:51:57,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 18:51:57,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 18:51:57,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 18:51:57,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:51:57,597 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 18:51:57,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 18:51:57,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 18:51:57,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 18:51:57,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 18:51:57,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-11 18:51:57,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x94e2fec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v000010DEd00000BE9sv00001462sd00002360bc04sc03i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0003v046Dp0A1De0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,m4,lsfw')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'platform:pcspkr')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'platform:eisa')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd00008410bc04sc03i00')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-11 18:51:57,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001022sd00009601bc06sc00i00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc01ip00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:device:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v000010DEd00000DC4sv00001462sd00002360bc03sc00i00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0501:')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D8,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,110,111,112,113,114,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v18A5p022Ad0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001002sd00004390bc01sc06i01')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v0000197Bd00000368sv0000197Bsd00001368bc01sc01i85')
2012-01-11 18:51:57,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1703:bd11/16/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A89GTD-PRO/USB3:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc02ip00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic01isc01ip00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0003v046Dp081Be0010-e0,1,kD4,ramlsfw')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc01ip00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc01ip01')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp0A1Dd4001dc00dsc00dp00ic01isc02ip00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001106d00003044sv00001043sd000081FEbc0Csc00i10')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v0930p6544d0100dc00dsc00dp00ic08isc06ip50')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v0000197Bd00002361sv00001043sd0000824Fbc01sc06i01')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-11 18:51:57,605 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v045Ep00F9d0003dc00dsc00dp00ic03isc00ip00')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001002sd0000439Cbc01sc01i8a')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'usb:v046Dp081Bd0010dcEFdsc02dp01ic0Eisc02ip00')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2012-01-11 18:51:57,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x99119ec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-11 18:51:57,771 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:51:58,022 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:51:58,289 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:01,791 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:03,197 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:03,406 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:12,230 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:18,718 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
2012-01-11 18:52:29,109 DEBUG: Removing package: nvidia-current
2012-01-11 18:52:29,867 DEBUG: remove progress statusChange dpkg-exec 0.000000
2012-01-11 18:52:33,938 DEBUG: remove progress statusChange nvidia-current 0.000000
2012-01-11 18:52:34,039 DEBUG: remove progress statusChange nvidia-current 33.333300
2012-01-11 18:52:41,241 DEBUG: remove progress statusChange nvidia-current 66.666700
2012-01-11 18:52:41,540 DEBUG: remove progress statusChange nvidia-current 100.000000
2012-01-11 18:52:41,622 DEBUG: remove progress statusChange python-gmenu 100.000000
2012-01-11 18:52:41,967 DEBUG: remove progress statusChange libc-bin 100.000000
2012-01-11 18:52:42,143 DEBUG: remove progress statusChange man-db 100.000000
2012-01-11 18:52:42,946 DEBUG: remove progress statusChange python-support 100.000000
2012-01-11 18:52:45,756 DEBUG: (Reading database ... 490558 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching gl_conf to auto mode
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...

2012-01-11 18:52:46,038 DEBUG: XorgDriverHandler.disable(nvidia): previously had no xorg.conf, deleting xorg.conf
2012-01-11 18:52:46,125 DEBUG: Removing package: nvidia-settings
2012-01-11 18:52:46,965 DEBUG: remove progress statusChange dpkg-exec 0.000000
2012-01-11 18:52:47,468 DEBUG: remove progress statusChange nvidia-settings 0.000000
2012-01-11 18:52:47,501 DEBUG: remove progress statusChange nvidia-settings 33.333300
2012-01-11 18:52:47,502 DEBUG: remove progress statusChange nvidia-settings 66.666700
2012-01-11 18:52:47,684 DEBUG: remove progress statusChange nvidia-settings 100.000000
2012-01-11 18:52:47,881 DEBUG: remove progress statusChange man-db 100.000000
2012-01-11 18:52:48,584 DEBUG: (Reading database ... 490393 files and directories currently installed.)
Removing nvidia-settings ...
Processing triggers for man-db ...

2012-01-11 18:52:56,994 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,063 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,266 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,331 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,551 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,642 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,904 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:57,973 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:58,202 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:52:58,278 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,052 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,121 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,326 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,391 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,617 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:36,682 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:38,683 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:38,749 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:39,480 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:39,550 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:39,760 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:39,845 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:42,421 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:42,486 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,241 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,310 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,519 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,592 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,801 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:43,889 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:44,175 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:44,240 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:44,449 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:53:44,514 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:54:04,685 DEBUG: nvidia_current is not the alternative in use
2012-01-11 18:54:04,765 DEBUG: nvidia_current is not the alternative in use
```

---

### Post by pqwoerituytrueiwoq on 2012-01-11
```
sudo apt-get install nvidia-settings
```
are you using nomodeset?
if not use it reboot
if still not working
generate a xorg.conf file
and post what is in it

---

### Post by pqwoerituytrueiwoq on 2012-01-11
looks like it is still trying to use the official ati driver fglrx did you do something special when installing it?
removing xorg.conf and uninstalling the ati driver should have done it

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> looks like it is still trying to use the official ati driver fglrx did you do something special when installing it?
removing xorg.conf and uninstalling the ati driver should have done it

Thanks for the response.

 > did you do something special when installing it?I did absolutely nothing and now, I am completely stumped!

Kirby

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install nvidia-settings
```are you using nomodeset?
if not use it reboot
if still not working
generate a xorg.conf file
and post what is in it

Thanks for the response.

How exactly does a person generate a new xorg.conf file?

Thanks again.
Kirby

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install nvidia-settings
```are you using nomodeset?
if not use it reboot

How and/or where do you put nomodeset?

Thanks again.
Kirby

---

### Post by Kir_B on 2012-01-11
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install nvidia-settings
```

Okay, so I didn't think I needed to do this, but when I ran the command, it appeared as though it wasn't installed, but even after rebooting, the result is exactly the same - no options for changing the resolution.

Thanks again.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-12
```
Xorg -configure
``` will make a xorg.conf file in the current directory (typically [FONT=Courier New]/home/$USER[/FONT])
post what is in it
```
gksu nvidia-settings
``` you should be able to set the resolution system wide then

when i switched my moms computer to a nvidia chip from a intigrated ati chip i was banging my head why is it not working i removed the xorg file and it worked but i had a resolution issue i assumed auto detect was having issues with a vga cord but a made a edit to xorg.conf and it works just fine

---

### Post by Kir_B on 2012-01-13
Thanks so much for all your help pqwoerituytrueiwoq.
Sorry it's taken so long to get back to you, but life always has to get in the way of the things that are really important!:P

> **pqwoerituytrueiwoq said:**
> ```
Xorg -configure
``` will make a xorg.conf file in the current directory (typically [FONT=Courier New]/home/$USER[/FONT])
post what is in it.

The following, is the result of that command:

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```> ```
gksu nvidia-settings
``` you should be able to set the resolution system wide thenThe following is the message that comes up when I run that last command (along with an almost optionless nvidia-settings window):

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

When I run _**sudo nvidia-xconfig,**_ I just get "command not found"

What's really mysterious, is that I had it running last night, but I couldn't get it to run my two monitors in twinview, but instead, would only run separate Xscreens. So I uninstalled it, repeated all the commands that I did to get it installed and I cannot for the life of me repeat my former success.](*,)

And I thought I was stumped before!:confused:

Thanks again.
Kirby

---

### Post by mastablasta on 2012-01-13
IF and only IF you were using fglrx drivers (proprietary drivers from ATI) before then you need to fully remove them i am not sure the commands given remove the drivery fully (i never did this). but here is a how to: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
if however ,you only used opensource drivers and you are talking about onboard graphics and you now want to use the other one, the easiest way would be to:
go to bios and disable onboard video
boot and select nomodeset (if necessary -if it doesn't want to boot) - to get into grub and get boot parameters hold shift on boot.
once in desktop, install proprietary nvidia driver for the new card
 
 
additionally drivers in linux are often part of kernel. so to get newer opensource drivers and support you need newer kernel, which means upgrading to latest version. or adding a PPA. 
one more thing you can do if newer proprietary drivers are available - you can donwload them form their website and install them manually. just using 10.04 and installing them from jockey will (i think) only install same old version of drivers. to get a new version you owuld need to do it manually. someone can maybe make a better comment on this issue, but i really think this is how things go.

---

### Post by Kir_B on 2012-01-13
Thanks so much for the response mastablasta.

> **mastablasta said:**
> IF and only IF you were using fglrx drivers (proprietary drivers from ATI) before then you need to fully remove them i am not sure the commands given remove the drivery fully (i never did this). but here is a how to: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I was very optimistic that the commands given in that last link would finally address the problem, as that appeared to do a more thorough job of removing the fglrx drivers, but after doing the commands in the "[Problem: Need to purge -fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx")" section, I tried to once again get the nvidia drivers installed with the result being that I get the driver installed, but the nvidia- settings window refuses to give me an option to change the resolution.

 
> if however ,you only used opensource drivers and you are talking about onboard graphics and you now want to use the other one, the easiest way would be to:
go to bios and disable onboard video
boot and select nomodeset (if necessary -if it doesn't want to boot) - to get into grub and get boot parameters hold shift on boot.
once in desktop, install proprietary nvidia driver for the new cardDuring the past year, I've tried Ubuntu's ATI drivers several times hoping that Canonical would at some point upgrade the driver to a newer version that fully supports the hd 4290 graphics chipset, but every time I tried them, I was forced to put up with an annoying message in the bottom left of my desktop (with no way to disable it), so each time, I wound up uninstalling the driver and went back to the open source driver.

I did as you said, and disabled the onboard, but I get the exact same result. I've also been using the nomodeset option, with every attempt, but again, with the exact same results.
 
 > 
additionally drivers in linux are often part of kernel. so to get newer opensource drivers and support you need newer kernel, which means upgrading to latest version. or adding a PPA. I am indeed using the latest kernel.

> one more thing you can do if newer proprietary drivers are available - you can donwload them form their website and install them manually. just using 10.04 and installing them from jockey will (i think) only install same old version of drivers. to get a new version you owuld need to do it manually. someone can maybe make a better comment on this issue, but i really think this is how things go.I'm really reluctant to do it this way, as I've read that this may complicate things down the road, and at the same time, I have absolutely no need to be on the bleeding edge.

Thanks again for the information. I really appreciate the time you put into your response.

Thanks again.
Kirby

---

### Post by Kir_B on 2012-01-14
So, it dawned on me that it may paint a better picture of what I'm talking about, when I say that my nvidia-settings is lacking options, so I've attached a picture of what it looks like.

Edit: I forgot to add that nvidia-settings doesn't show up in the administration menu, like it does on my old dinosaur, that is also running Ubuntu Lucid.

Thanks again
Kirby

---

### Post by mastablasta on 2012-01-14
> **Kir_B said:**
> 
I'm really reluctant to do it this way, as I've read that this may complicate things down the road, and at the same time, I have absolutely no need to be on the bleeding edge.


Me too, but here it is not so much about being on the beleding edge as having it works drivers and having drivers that work as they should in the first place. Things in linux are sometimes a bit different than in windows. newer drivers often means better general support not just extra features.

.
.
.
.

so, where is the picture? :-) :-P

same goes for nvidia. if you have a card that came out after 10.04 (april 2010) or drivers for the card came after that you are better off using latest version of ubuntu or you woul have to porbably use soem PPA to install the correct newer drivers. someone with nvidia card will be able to give better info on that.

for example 10.04 sort of recognises my sound card. often it just stopped working and it took 40 minutes to fix things. i had two choices either use a PPA from newer drivers, compile them from the soruce or upgrade. i did an upgrade to 10.10. now things are much better though sound still goes out. when 12.04 come out i will upgrade to it. hopefully card will have full support (including digital audio output) in that version.

---

### Post by pqwoerituytrueiwoq on 2012-01-14
another example of what mastablasta said would be using a ssd on lucid
lucid's default kernel does not support trim so i am using the back-ported kernel from 10.10
can you post the output of [FONT=Courier New]lspci -v[/FONT]


just got a idea blacklist the fglrx driver
[FONT=Courier New]gksu gedit /etc/modprobe.d/blacklist.conf[/FONT]
add this to the end on its own line
[FONT=Courier New]blacklist fglrx[/FONT]

---

### Post by Kir_B on 2012-01-14
> **mastablasta said:**
> Me too, but here it is not so much about being on the beleding edge as having it works drivers and having drivers that work as they should in the first place. Things in linux are sometimes a bit different than in windows. newer drivers often means better general support not just extra features.

same goes for nvidia. if you have a card that came out after 10.04 (april 2010) or drivers for the card came after that you are better off using latest version of ubuntu or you woul have to porbably use soem PPA to install the correct newer drivers. someone with nvidia card will be able to give better info on that.

for example 10.04 sort of recognizes my sound card. often it just stopped working and it took 40 minutes to fix things. i had two choices either use a PPA from newer drivers, compile them from the soruce or upgrade. i did an upgrade to 10.10. now things are much better though sound still goes out. when 12.04 come out i will upgrade to it. hopefully card will have full support (including digital audio output) in that version.

The card in question, is an MSI gts 450, which I'm pretty sure came out before Lucid. I'll try the Lucid live cd and see if it's recognized over there.

The one problem I have with installing the drivers from the nvidia site, is that, if I'm understanding this properly, I'll have to re-install the drivers every time I get a kernel upgrade (please correct me if I'm wrong) and that just sounds like a huge pain in the neck.

> so, where is the picture? :smile: :razz:It's there. At least it's there for me...???

Thanks again mastablasta.
Kirby

---

### Post by Kir_B on 2012-01-14
> **pqwoerituytrueiwoq said:**
> another example of what mastablasta said would be using a ssd on lucid
lucid's default kernel does not support trim so i am using the back-ported kernel from 10.10
can you post the output of [FONT=Courier New]lspci -v[/FONT]

```
jaun@jaun-desktop:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fc000000-fe6fffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fe700000-fe7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe800000-fe8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40) (prog-if 01)
    Subsystem: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 28
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=8]
    I/O ports at 7000 [size=4]
    I/O ports at 6000 [size=16]
    Memory at fbfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbfff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbfff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: ATI Technologies Inc SB700/SB800 IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 8410
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbffc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbff7000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbfff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation Device 0dc4 (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 2360
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    Expansion ROM at fe680000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau

01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 2360
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at fe67c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03) (prog-if 30)
    Subsystem: ASUSTeK Computer Inc. Device 8413
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe7fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci

03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 10) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe8ffc00 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

03:00.1 IDE interface: JMicron Technology Corp. Device 0368 (rev 10) (prog-if 85 [Master SecO PriO])
    Subsystem: JMicron Technology Corp. Device 1368
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=8]
    I/O ports at c480 [size=4]
    I/O ports at c400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

04:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81fe
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at dc00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8432
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at e800 [size=256]
    Memory at fafff000 (64-bit, prefetchable) [size=4K]
    Memory at faff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```


> just got a idea blacklist the fglrx driver
[FONT=Courier New]gksu gedit /etc/modprobe.d/blacklist.conf[/FONT]
add this to the end on its own line
[FONT=Courier New]blacklist fglrx[/FONT]

Now that may be a great idea!!! I'm going to give it a go and get back to you guys.

Thanks again.
Kirby

---

### Post by Shazaam on 2012-01-14
You may also need to do this....
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add these to the end (bottom)...
```
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveaub
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

---

### Post by Kir_B on 2012-01-14
> **Shazaam said:**
> You may also need to do this....
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```and add these to the end (bottom)...
```
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveaub
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

I'm not sure that will help. I just tried the Ubuntu 10.04.1 live cd (the same cd I installed this system with) and the result is the same over there: "No proprietary drivers are in use on this system".](*,)

Is there a back-ported kernel out there that will solve my problem?

Or it looks like I'm doing a fresh install. The only question is what version to install.

If anyone has any suggestions, I'd really appreciate any ideas you all may have.

Thanks again.
Kirby

---

### Post by Shazaam on 2012-01-14
I am using the x-swat repo and their nvidia-current and nvidia-settings. Here is a screeshot. You will see that mine says the same "No proprietary drivers are in use on this system" as yours. It is a known bug. I am running Lucid at the moment.

---

### Post by pqwoerituytrueiwoq on 2012-01-14
> **Kir_B said:**
> I'm not sure that will help. I just tried the Ubuntu 10.04.1 live cd (the same cd I installed this system with) and the result is the same over there: "No proprietary drivers are in use on this system".](*,)

Is there a back-ported kernel out there that will solve my problem?

Or it looks like I'm doing a fresh install. The only question is what version to install.

If anyone has any suggestions, I'd really appreciate any ideas you all may have.

Thanks again.
Kirby
i am using a backborted kernel but i got it for my ssd it is 2.6.35-25
but i was able to switch my moms system to a gt 430 from a integrated ati 3000 using ubuntu 10.04 with the default kernel fglrx was in use for the record
i purged the fglrx installed nvidia removed xorg.conf and blacklisted fglrx set the res in nivia settings (as root) and it has no issues
this is the xorg.conf on her system
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 290.10  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Nov 16 18:47:40 PST 2011

# Section "ServerLayout"
#     Identifier     "Layout0"
#     Screen      0  "Screen0"
#     InputDevice    "Keyboard0" "CoreKeyboard"
#     InputDevice    "Mouse0" "CorePointer"
# EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

# Section "InputDevice"
    # generated from default
#     Identifier     "Keyboard0"
#     Driver         "kbd"
# EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```and here are my mods to blacklist.conf
```
# ati drvier is blaclisted since we are uing a nvidia gpu
blacklist fglrx

# nvidia hdmi audio is disabled so apps will use the correct audio output
blacklist snd_hda_codec_nvhdmi

# dont need the open source nvidia driver have the nvidia one
blacklist nouveau
```from grub.cfg
```
menuentry "Ubuntu, with Linux 2.6.32-37-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8497a121-ebea-42e5-af82-8b15ad546005
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=8497a121-ebea-42e5-af82-8b15ad546005 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-37-generic
}
```

---

### Post by Kir_B on 2012-01-14
> **Shazaam said:**
> I am using the x-swat repo and their nvidia-current and nvidia-settings. Here is a screeshot. You will see that mine says the same "No proprietary drivers are in use on this system" as yours. It is a known bug. I am running Lucid at the moment.

Yeah, that's the repo that I'm using.

I just finished purging everything again, then blacklisted the following:
```
blacklist fglrx
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveaub
blacklist rivafb
blacklist nvidiafb
```Rebooted, reinstalled nvidia-current and nvidia-settings, rebooted again (using nomodeset each time) and when I got back again, nvidia-settings still contains very limited options, of which a resolution option isn't one of them.](*,)

I've attached the pics of what happens when I start nvidia-settings.

Thanks again everyone.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-14
any change in the output of "[FONT=Courier New]sudo nvida-xconfig[/FONT]"?

---

### Post by Kir_B on 2012-01-14
> **pqwoerituytrueiwoq said:**
> any change in the output of "[FONT=Courier New]sudo nvida-xconfig[/FONT]"?

Nope!

> jaun@jaun-desktop:~$ sudo nvida-xconfig
sudo: nvida-xconfig: command not foundI think I live on some kind of strange vortex or something. Somehow, on the last three machines I've run Ubuntu on over the last two and a half years, I've run into an issue or two on each of the machines, that have stumped the Linux community. Granted, the one box was a true fossil, that now serves as a very effective doorstop. 

I fear that this may very well be one of those times again.

Thanks again.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-14
reinstall/reconfigure nvidia-current via synaptic (reinstall apps has never helped me on linux but i am not you)

---

### Post by Kir_B on 2012-01-14
> **pqwoerituytrueiwoq said:**
> reinstall/reconfigure nvidia-current via synaptic (reinstall apps has never helped me on linux but i am not you)

What do you mean by reconfigure via synaptic?

Kirby

---

### Post by Kir_B on 2012-01-14
I just did a complete removal of both the nvidia-current & nvidia-settings, rebooted, reinstalled both via synaptic and then rebooted to the exact same situation, including the sudo nvida-xconfig command (sudo: nvida-xconfig: command not found).

It was worth a try.

Thanks again.
Kirby

---

### Post by Kir_B on 2012-01-14
> **pqwoerituytrueiwoq said:**
> i am using a backborted kernel but i got it for my ssd it is 2.6.35-25
but i was able to switch my moms system to a gt 430 from a integrated ati 3000 using ubuntu 10.04 with the default kernel fglrx was in use for the record
i purged the fglrx installed nvidia removed xorg.conf and blacklisted fglrx set the res in nivia settings (as root) and it has no issues

That's what I've done also, with the exception of setting the res, as I can get no such option.

> this is the xorg.conf on her system
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 290.10  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Nov 16 18:47:40 PST 2011

# Section "ServerLayout"
#     Identifier     "Layout0"
#     Screen      0  "Screen0"
#     InputDevice    "Keyboard0" "CoreKeyboard"
#     InputDevice    "Mouse0" "CorePointer"
# EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

# Section "InputDevice"
    # generated from default
#     Identifier     "Keyboard0"
#     Driver         "kbd"
# EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```I'd have responded earlier, but I didn't know what to make of the information in that last section.

Unfortunately, when I run sudo nvidia-xconfig, I get:
```
sudo: nvida-xconfig: command not found
```> and here are my mods to blacklist.conf
```
# ati drvier is blaclisted since we are uing a nvidia gpu
blacklist fglrx

# nvidia hdmi audio is disabled so apps will use the correct audio output
blacklist snd_hda_codec_nvhdmi

# dont need the open source nvidia driver have the nvidia one
blacklist nouveau
```The only ones that I don't have blacklisted, is the snd_hda_codec_nvhdmi and the nouveu, which at this point, I'd love to try!!!

> from grub.cfg
```
menuentry "Ubuntu, with Linux 2.6.32-37-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8497a121-ebea-42e5-af82-8b15ad546005
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=8497a121-ebea-42e5-af82-8b15ad546005 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-37-generic
}
```Yup, I am indeed running the same kernel.

Could someone please provide me with the path to the grub.cfg, I'd like to do a quick comparison. It might reveal something for me. Thanks

Edit: I found grub.cfg's path.

Wow, thanks for all that.
Kirby

---

### Post by Kir_B on 2012-01-15
> Originally Posted by [B]pqwoerituytrueiwoq
[/B]from grub.cfg
     Code:
     ```
menuentry "Ubuntu, with Linux 2.6.32-37-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8497a121-ebea-42e5-af82-8b15ad546005
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=8497a121-ebea-42e5-af82-8b15ad546005 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-37-generic
}
``` Wow. My grub.cfg's boot command is very different!

Did you set the res and does that only affect the boot, or is that a system wide parameter?

Here's what mine looks like:

```
menuentry 'Ubuntu, with Linux 2.6.32-37-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 32a48f5a-210d-4b14-9228-237d8c3c4516
    linux    /boot/vmlinuz-2.6.32-37-generic-pae root=UUID=32a48f5a-210d-4b14-9228-237d8c3c4516 ro splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-37-generic-pae
```

---

### Post by pqwoerituytrueiwoq on 2012-01-15
[FONT=Courier New]nomodeset[/FONT] should be in that like but it is not so unless you are manually enabling [FONT=Courier New]nomodeset[/FONT] at every boot it is not in use
[FONT=Courier New]
video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap[/FONT] is a thing used to get the boot splash screen to be in the right resolution (close to 1600x900 as fremebuffer gives without going over)
google fix boot resolution ubuntu for more on that

edit:
2.6.32-37-generic-**pae** why not just use 64bit?


also only disable [FONT=Courier New]snd_hda_codec_nvhdmi[/FONT] if you are not using hdmi for audio

---

### Post by Kir_B on 2012-01-15
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]nomodeset[/FONT] should be in that like but it is not so unless you are manually enabling [FONT=Courier New]nomodeset[/FONT] at every boot it is not in use

I hear ya. I am going to incorporate that very soon. I also noticed that you've removed splash quiet. What does that do?

> [FONT=Courier New]video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap[/FONT] is a thing used to get the boot splash screen to be in the right resolution (close to 1600x900 as framebuffer gives without going over)
google fix boot resolution ubuntu for more on thatThat's what I thought.

> edit:
2.6.32-37-generic-**pae** why not just use 64bit?
I have never seen my conky tell me that I'm using any more than a gig and a half, no matter how much I've got going on.

> also only disable [FONT=Courier New]snd_hda_codec_nvhdmi[/FONT] if you are not using hdmi for audioExcellent. I'll have to remember that.

It looks as though I'm going to have to either upgrade my install or perhaps install a backported kernel, though, researching the latter solution is eluding my googling skills

Thanks again.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-15
> **Kir_B said:**
> I hear ya. I am going to incorporate that very soon. I also noticed that you've removed splash quiet. What does that do?

i did not it is still in there just the words are in the other order i think splash tell it to show the plymouth theme and quiet i think tells it not to show everything that is in the dmesg log

your issue has to be some config like xorg.conf/blacklist.conf/remnants of fglrx
can you disable the ati chip in the bios?

you could try reinstalling fglrx just so you could purge it

---

### Post by Kir_B on 2012-01-15
> **pqwoerituytrueiwoq said:**
> i did not it is still in there just the words are in the other order i think splash tell it to show the plymouth theme and quiet i think tells it not to show everything that is in the dmesg log

Nice to Know. But why did mine come with a redundancy?

```
ro splash quiet  quiet splash
```> your issue has to be some config like xorg.conf/blacklist.conf/remnants of fglrx
can you disable the ati chip in the bios?Yeah, that was done a couple of nights ago.

[QUOTE]you could try reinstalling fglrx just so you could purge itYeah, I had the same thought, so I have, about three or four times for good measure.](*,)

The thing for me, is that I get the same result with the 10.04.1 livecd, but I didn't have any problems with the linux Mint 11 LiveCd (Katya).

Thanks again
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-15
which nvidia gpu are you using?

---

### Post by Kir_B on 2012-01-15
> **pqwoerituytrueiwoq said:**
> which nvidia gpu are you using?

Its an MSI GTS 450. It satisfied my desire for a low power consumption at idle.

Thanks, yet again.
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-16
i do not remember getting a copy of yo xorg.conf file
ctrl+alt+F1 (read ahead now)
login to the tty
```
cd Desktop
sudo service gdm stop
Xorg -configure
sudo service gdmstart
```then login into the GUI and on your desktop should be a file lets see what is in it

and what is your recommended screen resolution

---

### Post by bogan on 2012-01-16
Hi!, **Kir_B**,

I have read through your Posts in this thread, and although I am no expert I have learnt a lot from my own problems with getting the correct nvidia driver, and ditto for WiFi drivers.

First: your lspci Post showed both nvidiafb and nouveau modules loaded as well as nvidia. nouveau is known to be incompatible with recent nvidia drivers, NVIDIA recommend it should be purged, but at least blacklist it, and nvidiafb as well.
 The list of blacklists you posted shows "nouveau[COLOR=DarkRed]b[/COLOR]" *THAT WILL NOT DO IT.* You should also blacklist "lbm-nouveau".

Second: I was, like you, very reluctant to go the direct route to download and install the correct nvidia drivers, but once I bit the biscuit it turned out to be quite straight forward and quick and easy.
It is true that, after the last kernel update to 11.10-14 , I had to reinstall both the nvidia 290.10 driver and the WiFi driver as well.
But as I had it all at my fingertips it only took ten minutes to do both, and all was well.

Third: I suggest you do a system search for nvidia-xconfig and if it shows, cd to the directory it is in and repeat "sudo ./nvidia-xconfig".

Fourth: Regarding editing the grub menu and the significance of splash, single, nomodset etc see Posts 1&2 of MaFoElffen's magnum opus in the "Black Screen" 'Sticky' thread of the Installation and Upgrades Forum.
[http://ubuntuforums.org/showthread.php?t=1743535&page=93]("http://http//ubuntuforums.org/showthread.php?t=1743535&page=93") * Edit1: Ignore This Link if it does not work. Edit2: Or Copy-Paste it to the address bar of a new Tab in your Browser.*
You will also find there a full set of instructions for installing the nvidia drivers, dealing with changing from integral to separate video cards, and problems specific to ati cards.

Good Luck, and do not let the thought of "Compiling" drivers daunt you; the NVIDIA driver is a self-extracting executable file that does everything for you, including asking if you wish to run config and settings. Just that you have to run it from a Text Terminal as there must not be an Xsession running when it is installed.

Chao!, **bogan**.
Edited: Note re link added.

---

### Post by Kir_B on 2012-01-16
> **pqwoerituytrueiwoq said:**
> i do not remember getting a copy of yo xorg.conf file
ctrl+alt+F1 (read ahead now)
login to the tty
```
cd Desktop
sudo service gdm stop
Xorg -configure
sudo service gdm start
```then login into the GUI and on your desktop should be a file lets see what is in it

The result of Xorg -configure is: 
```
Fatal server error :
Cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"
```> and what is your recommended screen resolution1920x1080 

I also blacklisted nvidiafb and lbm-nouveau before I did the above commands. 

Thanks again. 
Kirby

---

### Post by Kir_B on 2012-01-16
> **bogan said:**
> Hi!, **Kir_B**,

I have read through your Posts in this thread, and although I am no expert I have learnt a lot from my own problems with getting the correct nvidia driver, and ditto for WiFi drivers.

First: your lspci Post showed both nvidiafb and nouveau modules loaded as well as nvidia. nouveau is known to be incompatible with recent nvidia drivers, NVIDIA recommend it should be purged, but at least blacklist it, and nvidiafb as well.
 The list of blacklists you posted shows "nouveau[COLOR=DarkRed]b[/COLOR]" *THAT WILL NOT DO IT.* You should also blacklist "lbm-nouveau".

Second: I was, like you, very reluctant to go the direct route to download and install the correct nvidia drivers, but once I bit the biscuit it turned out to be quite straight forward and quick and easy.
It is true that, after the last kernel update to 11.10-14 , I had to reinstall both the nvidia 290.10 driver and the WiFi driver as well.
But as I had it all at my fingertips it only took ten minutes to do both, and all was well.

Third: I suggest you do a system search for nvidia-xconfig and if it shows, cd to the directory it is in and repeat "sudo ./nvidia-xconfig".

Fourth: Regarding editing the grub menu and the significance of splash, single, nomodset etc see Posts 1&2 of MaFoElffen's magnum opus in the "Black Screen" 'Sticky' thread of the Installation and Upgrades Forum.
[http://ubuntuforums.org/showthread.php?t=1743535&page=93]("http://http//ubuntuforums.org/showthread.php?t=1743535&page=93") Ignore This Link if it does not work.
You will also find there a full set of instructions for installing the nvidia drivers, dealing with changing from integral to separate video cards, and problems specific to ati cards.

Good Luck, and do not let the thought of "Compiling" drivers daunt you; the NVIDIA driver is a self-extracting executable file that does everything for you, including asking if you wish to run config and settings. Just that you have to run it from a Text Terminal as there must not be an Xsession running when it is installed.

Chao!, **bogan**.
Edited: Note re link added.

Thank you very much bogan.

I did a search for nvidia-xconfig and it is not on my system.

It's getting late right now, so I'm going to do some more research tomorrow and I will get back to you.

Thanks again 
Kirby

---

### Post by pqwoerituytrueiwoq on 2012-01-17
you must have done something that caused this trying to get it to work
try to switch back to the ati chip and get it working then switch to the nvidia card using the 1st thing i said
hopefully your computer is in a more accessible location than mine, lol
this is from my sudo lspci -v as yuo can see it has  nouveau and nvidiafb loaded so that should not be the issue
```
01:00.0 VGA compatible controller: nVidia Corporation Device 1244 (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 83be
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fbd00000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

---

### Post by bogan on 2012-01-17
Hi!, **Kir_B,**
I noticed that you answered the request for the GPU with the name of the Video card.
 It is the actual GPU built into the card, that is needed to find the correct latest driver, though NVIDIA has an automatic scan program that is built into their driver Downloads web page, that may tell you, as well as recommend the best driver.

 One thing worth trying is to run: ```
sudo nvidia-installer --latest
```If it is installed. This  will show the driver version installed and the latest available version, both  as the version number and as the bin file name, but will not change anything. You may have to search for it .

Another thing is that before installing a video driver, or re-installing  one suspected of faults, the Gurus recommend updating the  Linux-headers, uninstalling  any previous drivers, purging them to  remove any orphaned items, and running```
 sudo update-grub 
```afterwards.
For example, vide MAFoElffen:
> Especially for nvidia cards, I usually just [boot] into a text mode by going to   a text console via grub [menu] edit (key 'e") append " text " to the end of the   kernel boot line and boot{"ctrl-x') and after a login type  
```
sudo apt-get update
 sudo nvidia-installer --uninstall
 sudo apt-get remove nvidia-*
 sudo apt-get install linux-headers-'uname -r'
 sudo apt-get install nvidia-current # or nvidia-'version number'
 sudo nvidia-xconfig
 sudo apt-get update
```(Note- This example assumes that you have a GeoForce 6xxx or better card) then try to start the GUI via ```
sudo service gdm  start
``` Edit bogan: { If running 11.10 or later, that last line would be:```
sudo service lightdm  start
```You will find fully detailed instructions in the link I put in my #45 Post. That is an extract. *[ Note: " -'uname -r' " is the output you get from entering 'uname -r' in a terminal.*]

{ The link did not work last time, I'll try again here: [http://ubuntuforums.org/showthread.php?t=1743535&page=93](http://ubuntuforums.org/showthread.php?t=1743535&page=93)
Hopefully }.

Chao!, **bogan**.

---

### Post by bogan on 2012-01-17
Hi,** Kir_B,**

I just checked out the NVIDIA site on the assumption your MSI gts450 card has a nvidia GTS 450 GPU installed. It shows 290.10 as the correct driver. Which is the same one I needed to get for my GT520 1Gb card.
Even in Ubuntu 11.10 Synaptic Manager shows nvidia-current to be only v280. Whilst my 10.04 installation shows it to be v195.36.24, which is presumably what you have installed, though I saw in one of your Posts a reference to nvidia-173.

It might be a good idea to add both nvidia-173 and nvidia-96 to your file of blacklists, as both are listed by the 10.04 version of Synaptic.

As far as I understand it, your problem is that you can boot into one Linux installation but get a Blank Screen in another and cannot set the resolution to allow it to boot, or alternatively you can boot to a tty login prompt but nvidia-settings does not allow the resolution to be changed.

Which suggests to me that the main problem is that the driver is using the Auto selection to set the resolution, or colour depth, to something that is not compatible with your Monitor.
 Have you tried setting the resolution, to something your Monitor will display, in the grub menu, or in Startup-Manager?. 

For example my Linux boot line after "ro" has the entry "vga=795" which is 1280x1024x24
```
Sudo hwinfo --monitor
``` will tell you which resolutions are supported.```
{ sudo apt-get install hwinfo
# if you do not have it.}
```In my 10.04 System Menu>Preferences, nvidia-settings is shown as "NVIDIA X Server Settings".
 Running it gives a display the same as your Thumbnail except that the left side bar is full of options, the second of which is: "X Server Display Configuration".
 Select that and it shows the monitor with the resolution currently operative and a Resolution box set to 'Auto'.
 Click on the button and a list drops down showing all the available choices; there is also an option to save settings to the configuration file.

Remember that this is with the 290.10 driver, but there is something clearly wrong with the installation you are getting.

Chao!, **bogan**.

*Edit: I first Posted this two hours ago but it did not turn up in the forum, not the first time that has happened.*

---

### Post by Kir_B on 2012-01-18
First of all, I'd like to thank _**pqwoerituytrueiwoq**_ and **_bogan_** for all of your guys help - I know I couldn't have gotten this far without you saints.

So thanks to you guys filling my head with a tonne of information, which will stay with me forever, with result being that I've managed to get everything working properly.

Now, I can't possibly remember everything that I've done over the past few days, so I'll just post what I did today.

> **bogan said:**
> Hi,** Kir_B,**

It might be a good idea to add both nvidia-173 and nvidia-96 to your  file of blacklists, as both are listed by the 10.04 version of Synaptic.

So I did just that (with high hopes), but it didn't seem to have helped, but I thought, you never know and left them blacklisted.

Heres my entire blacklist at the end of all that troubleshooting:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
``````
blacklist amd76x_edac
blacklist fglrx
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveaub
blacklist rivafb
blacklist nvidiafb
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidiafb
blacklist nvidia-96
blacklist nvidia-173
```Then I tried (as suggested by bogan) 
> sudo apt-get update
sudo nvidia-installer --uninstallBut there was no installer present on my system.

Then:
```
sudo apt-get remove nvidia-*
```And:
```

sudo apt-get install linux-headers-2.6.32-37
```Of course after I did:

```
uname -r
```(For the newbee, that tell's you what to put after the "linux-headers-" part of the previous command).

That didn't do anything, as the correct headers were already installed.

Then I did:

```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```But still, the nvidia xconfig command did not exist.


Then I purged the nvidia packages yet again, with:
```

sudo apt-get --purge remove nvidia* nvidia-settings
```We then found [this page]("http://ubuntuforums.org/showthread.php?t=1684988") and it had the following command:

```
sudo update-alternatives --config gl_conf
```That was very revealing, as it told us that there were ati and or radeon remnants still in the system!

So I got to thinking, there's got to be some remnants of the ati driver in the system somewhere and did an awesome search (using [startpage]("https://startpage.com/do/mypage.pl?prf=e4896c3144b637d83a1419d9015ec2c7")  - Awesome search engine for google haters) for "(purge Or uninstall)  +ubuntu +lucid (ati OR radeon)" and came accross someones blog that had  the following command, which looked like it might just do it:

```
sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
```That command removed the fglrx-modaliases package (and maybe something else - I can't remember now), then we ran the following command again:

```
sudo update-alternatives --config gl_conf
```But since we'd purged every fglrx, nvidia, ati and or radeon package, it didn't give us the necessary options, so time to reinstall "nvidia-current" again.

Then as was suggested [here]("http://ubuntuforums.org/showpost.php?p=10445095&postcount=6"), I did the following set of commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
```This also installed the nvidia-settings package, which wasn't happening before (I had to install it with _sudo apt-get install nvidia-settings_)

 (we might have done a reboot at this point) and then repeated the command again which now came with nvidia choices:

```
jaun@jaun-desktop:~$ sudo update-alternatives --config gl_conf
[sudo] password for jaun: 
There are 2 choices for the alternative gl_conf (providing /etc/ld.so.conf.d/GL.conf).

  Selection    Path                                Priority   Status
------------------------------------------------------------
**[COLOR=Red]* 0[/COLOR] **           /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
  1            /usr/lib/mesa/ld.so.conf             500       manual mode
  2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

Press enter to keep the current choice
[*], or type selection number: 

```As you can see, we chose the "**[COLOR=Red]0[/COLOR]**" option.

Then we tried:
```

sudo nvidia-xconfig
```But this time it wrote a new xorg.conf file.

I then rebooted and when I got to my desktop, I went into administration and low and behold, Nvidia X Server Settings was there and once opened contained all the normal options. WOW!!! That was quite the ride. I learned something and hopefully , more than just some of it will stick.

Thanks a million metric tonnes guys. If you guys lived close enough, I'd gladly buy you beers.

Kirby :biggrin:  ):P

---

### Post by bogan on 2012-01-18
Hi!,** Kir_B**,
You Posted:> I then rebooted and when I got to my desktop, I went into administration  and low and behold, Nvidia X Server Settings was there and once opened  contained all the normal options. WOW!!! That was quite the ride. I  learned something and hopefully , more than just some of it will stick.

Thanks a million metric tonnes guys. If you guys lived close enough, I'd gladly buy you beers.
GREAT!  Glad it all worked out, I learnt a lot too!.** bogan**

Chao!

---

