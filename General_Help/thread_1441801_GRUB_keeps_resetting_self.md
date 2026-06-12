---
title: "GRUB keeps resetting self"
date: 2010-03-29
forum: General Help
---

### Post by MasterMIKE on 2010-03-29
Every now and then when on windows if it decides to crash (as windows does lol) sometimes when I boot the machine back up I'll find that the Grub would be saying that it cannot fid a symbol ?2 or something like that. This also sometimes happens after having shut down my comp from windows or Linux. Its extremely annoying having to reinstall the GRUB from a live disk every time. Since Friday when I got my new comp and inmstalled Ubuntu on it, the GRUB has reset itself 6 times. Does anyone know why this is happening and how too stop it.

NOTE: I'm using the 64-bit version of Ubuntu... and sorry if this post is in the wrong section I wasn't sure where to put it.

---

### Post by ibuclaw on 2010-03-29
Hi,

There's no bug here. You installed different versions of GRUB to different drives using the same /boot/grub/. One of them stopped booting because of ABI incompatibility.

Just tell the debconf template to install GRUB to each drive and you'll be ok.

For GRUB
```
sudo dpkg-reconfigure grub
```
For GRUB2
```
sudo dpkg-reconfigure grub-pc
```
Regards
Iain

---

### Post by MasterMIKE on 2010-03-29
I did what you said although I'm not sure if its worked. It displayed:

> michael@michael-desktop:~$ sudo dpkg-reconfigure grub-pc
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
Generating grub.cfg ...
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
done


As far as I know sdf does not even exist. I( have two drives sda the main drive and sdb the external drive.

---

### Post by ibuclaw on 2010-03-30
What is the output of:
```
udevadm info -a -p $(udevadm info -q path -n /dev/sdf)
```

Regards
Iain

---

### Post by MasterMIKE on 2010-03-31
> Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:3/block/sdf':
    KERNEL=="sdf"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="       0        0        0        0        0        0        0        0        0        0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:3':
    KERNELS=="7:0:0:3"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="Generic-"
    ATTRS{model}=="MS/MS-Pro       "
    ATTRS{rev}=="1.03"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x1cb"
    ATTRS{iodone_cnt}=="0x1cb"
    ATTRS{ioerr_cnt}=="0x1ca"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host7/target7:0:0':
    KERNELS=="target7:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host7':
    KERNELS=="host7"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0':
    KERNELS=="2-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v058Fp6362d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5':
    KERNELS=="2-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="9215"
    ATTRS{idVendor}=="058f"
    ATTRS{idProduct}=="6362"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Generic"
    ATTRS{product}=="Mass Storage Device"
    ATTRS{serial}=="058F63626420"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="41"
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
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.31-20-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a3a"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x0439"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="00000000,0000000f"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{modalias}=="pci:v00008086d00003A3Asv00001028sd00000439bc0Csc03i20"
    ATTRS{numa_node}=="0"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


I'd assume this in fact means that sdf is the external drive and I was just getting mixed up?

---

### Post by ibuclaw on 2010-04-01
> **MasterMIKE said:**
> I'd assume this in fact means that sdf is the external drive and I was just getting mixed up?

Correct. :)

Since you've worked out that it is just a harmless message, may I suggest that what you have probably done is selected sdf in the debconf options menu, and now grub tries to install itself to the external drive/card too.

Regards
Iain

---

### Post by MasterMIKE on 2010-04-01
lol, oops. Well thankyou very much for your help, its all working great now. I'll mark this as solved :)

---

