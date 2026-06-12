---
title: "Usb to Serial udev rule"
date: 2011-03-22
forum: General Help
---

### Post by Lance_shade on 2011-03-22
Hey,

Attempting to connect an Opticon Bar code scanner, which uses a USB to SERIAL connection.  The problem is, I need the USB port it connects via to be dynamically detected.  using Ubuntu 10.4.

Presently, I've attempted :
```
kernel=="ttyUSB*", SYSFS(idVendor)=="065a", SYSFS(idProduct)=="0009", MODE="0666", SYMLINK+="Opticon"

#I've also separately attempted:

kernel=="ttyUSB*", ATTR(idVendor)=="065a", ATTR(idProduct)=="0009", MODE="0666", SYMLINK+="Opticon"
```Saved in the /etc/udev/rules.d/50_opticon.rules

lsusb -v yields:
```

Bus 002 Device 004: ID 065a:0009 Optoelectronics Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x065a Optoelectronics Co., Ltd
  idProduct          0x0009 
  bcdDevice            9.00
  iManufacturer           1 Optoelectronics Co., Ltd.
  iProduct                2 Barcode Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
Device Status:     0x0000
  (Bus Powered)

```Udevadm info yielded: 

```


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="opticon"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0':
    KERNELS=="2-10:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="opticon"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{modalias}=="usb:v065Ap0009d0900dc00dsc00dp00icFFisc00ip00"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-10':
    KERNELS=="2-10"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="15"
    ATTRS{idVendor}=="065a"
    ATTRS{idProduct}=="0009"
    ATTRS{bcdDevice}=="0900"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="4"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Optoelectronics Co., Ltd."
    ATTRS{product}=="Barcode Device"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="118"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-30-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:02.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x036c"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x8239"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd0000036Csv00001043sd00008239bc0Csc03i10"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```The Symlink created is not being registered by the program I'm using to access the Opticon reader.  

Thanks for your time and help,
~Mike

---

