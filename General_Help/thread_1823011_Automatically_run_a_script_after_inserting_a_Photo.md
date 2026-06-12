---
title: "Automatically run a script after inserting a Photo memory card?"
date: 2011-08-11
forum: General Help
---

### Post by krumpy on 2011-08-11
I want to run a script automatically after inserting my photo memory card into the memory card reader.  I have a Dell that accepts several different types of memory cards, but I'm pretty sure I'm working on the right device.

```

df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             20157076   5025296  14107784  27% /
none                   2021528       408   2021120   1% /dev
none                   2027140       168   2026972   1% /dev/shm
none                   2027140       116   2027024   1% /var/run
none                   2027140         0   2027140   0% /var/lock
/dev/sda7            462012392  67525216 371018228  16% /home
/dev/sdb1              3991136   1201408   2789728  31% /media/401C-F38D
MyBookWorld:/DataVolume/Public
                     973391616 280717984 692673632  29% /media/netdrive
[B]/dev/sdf1              3971584      6624   3964960   1% /media/CANON_DC
[/B] 

```I'm assuming that I need to modify the rules for /dev/sdf/

```

udevadm info -a -p /sys/block/sdf/

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/host7/target7:0:0/7:0:0:3/block/sdf':
    KERNEL=="sdf"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="7959552"
    ATTR{alignment_offset}=="0"
    ATTR{discard_alignment}=="0"
    ATTR{capability}=="51"
    ATTR{stat}=="     287     3249     5867     1108       58        0      124      420        0     1232     1524"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/host7/target7:0:0/7:0:0:3':
    KERNELS=="7:0:0:3"
[B]    SUBSYSTEMS=="scsi"
[/B]    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="DELL    "
[B]    ATTRS{model}=="USB   HS-SD Card"
[/B]    ATTRS{rev}=="7.12"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x208d3"
    ATTRS{iodone_cnt}=="0x208d3"
    ATTRS{ioerr_cnt}=="0x1e7ec"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/host7/target7:0:0':
    KERNELS=="target7:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/host7':
    KERNELS=="host7"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0':
    KERNELS=="2-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v0644p0201d0712dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}==" 98mA"
    ATTRS{urbnum}=="2932107"
    ATTRS{idVendor}=="0644"
    ATTRS{idProduct}=="0201"
    ATTRS{bcdDevice}=="0712"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="DELL"
    ATTRS{product}=="CAB-200"
    ATTRS{serial}=="000001187BA7"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="42"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.35-30-generic-pae ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x293a"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x0215"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d0000293Asv00001028sd00000215bc0Csc03i20"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```So I created a file in /etc/udev/rules.d/ called 91-usbautorunrules

```

cat 91-usbautorun.rules 
SUBSYSTEM=="scsi" ,ATTRS{model}=="USB   HS-SD Card", RUN+="/usr/local/bin/photoscript.sh"

```However when I insert the card nothing happens.  I was working off the information provided in this tutorial.  ([http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/](http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/))

---

