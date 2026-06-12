---
title: "Hardware to remember which tty port?"
date: 2009-11-17
forum: General Help
---

### Post by Nekativ on 2009-11-17
I have multiple hardware modules, a transceiver, a relay board, a GPS puck, and a data acquisition board that plugs into ttyUSB0, ttyUSB1, and ttyUSB2 and so on. I am wondering if there is a way to permanently assign say the tranceiver for example to ttyUSB0. The issue is that I am remotely terminaling through the transceiver which is on ttyUSB0 but sometimes the transceiver ends up as ttyUSB1 which is a problem since I have a getty setup for ttyUSB0 and I can't setup a getty for ttyUSB1 since it uses a different BAUD rate for the relay board/gps puck/data aquisition boards. 

Any help would be greatly appreciated :) Also if you have any useful advice about tty ports I am all ears.

---

### Post by sisco311 on 2009-11-17
check if you have symbolic links to the ttyUSB[012] devices:
```
find /dev/ -type l -exec ls -al '{}' \; | grep ttyUSB
```

a symbolic link will always point to the same physical device.

i.e. my mouse usually is /dev/input/event1, but sometimes ends up as /dev/input/event2. I have symbolic link (/dev/input/by-path/pci-0000:00:0b.0-usb-0:2:1.0-event-mouse) which points always to the right /dev/input/event.

If you don't have symbolic links to the ttyUSB devices you can write your own udev rules to create them.

---

### Post by Nekativ on 2009-11-17
> **sisco311 said:**
> check if you have symbolic links to the ttyUSB[012] devices:
```
find /dev/ -type l -exec ls -al '{}' \; | grep ttyUSB
```a symbolic link will always point to the same physical device.

i.e. my mouse usually is /dev/input/event1, but sometimes ends up as /dev/input/event2. I have symbolic link (/dev/input/by-path/pci-0000:00:0b.0-usb-0:2:1.0-event-mouse) which points always to the right /dev/input/event.

If you don't have symbolic links to the ttyUSB devices you can write your own udev rules to create them.

Thanks for the help, but

I can't figure out how to find the hardware ID of the transceiver that is plugged into ttyUSB0 to create a udev rule with.

Also I do not really know how to write udev rules, help will be appreciated, thank you for bearing with my novice.

---

### Post by sisco311 on 2009-11-18
> **Nekativ said:**
> Thanks for the help, but

I can't figure out how to find the hardware ID of the transceiver that is plugged into ttyUSB0 to create a udev rule with.

Also I do not really know how to write udev rules, help will be appreciated, thank you for bearing with my novice.

this guide should help: [http://noctis.de/archives/16-HowTo-fixed-name-for-a-udev-device.html]("http://noctis.de/archives/16-HowTo-fixed-name-for-a-udev-device.html")

---

### Post by Nekativ on 2009-11-18
> **sisco311 said:**
> this guide should help: [http://noctis.de/archives/16-HowTo-fixed-name-for-a-udev-device.html](http://noctis.de/archives/16-HowTo-fixed-name-for-a-udev-device.html)

udevinfo does not work so I tried udevadm, however the output is very confusing and unclear since I do not really know how to use udevadm. 

I attempted to write my own udev rules for without much success with the confusing information I got from udevadm, here is what I wrote under the file I created /etc/udev/rules.d/44-my-device.rule:

KERNELS=="1-2:1.0", DRIVER="FTDI_SIO", SYMLINK="USBTranceiver1"

Basically I used my best guess from the output of 'udevadm' and wrote in what was listed as "KERNELS" and then I wrote in the driver, and then I attempted to create a SYMLINK called USBTransceiver1 which by my understanding would show up in the "/dev" folder like a ttyUSB node. I am probably wrong tho.

Any clarification will help me out a lot, thanks for the help so far.

---

### Post by sisco311 on 2009-11-18
please post the output of *udevadm*.

---

### Post by Nekativ on 2009-11-18
> **sisco311 said:**
> please post the output of *udevadm*.


I am not really sure if I did udevadm right, but here it is, as I said I am a novice :P

```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{latency_timer}=="1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v0403p6001d0400dc00dsc00dp00icFFiscFFipFF"
    ATTRS{supports_autosuspend}=="0"
    ATTRS{interface}=="USB <-> Serial"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{urbnum}=="23210819"
    ATTRS{idVendor}=="0403"
    ATTRS{idProduct}=="6001"
    ATTRS{bcdDevice}=="0400"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="6"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{product}=="USB <-> Serial"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="144"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.31-14-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2658"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d8"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00002658sv00001043sd000082D8bc0Csc03i00"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Nekativ on 2009-11-19
Alright after reading up a little more I got a slightly different version (with what I believe is the right information to get started with highlighted in red) of the parent chain, hopefully it will help, let me know if I a wrong:

```
kristof@Spectra1:~$ CLUE=ttyUSB0
kristof@Spectra1:~$ for DEVICE in $(find /sys ! -type l -iname "*${CLUE}*"); do ls -dl $DEVICE; udevadm info -a -p $DEVICE; done
drwxr-xr-x 4 root root 0 2009-11-18 23:11 /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB0

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="usb-serial"
    DRIVER=="ftdi_sio"
    ATTR{latency_timer}=="1"
    ATTR{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v0403p6001d0400dc00dsc00dp00icFFiscFFipFF"
    ATTRS{supports_autosuspend}=="0"
    ATTRS{interface}=="USB <-> Serial"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{urbnum}=="11"
    ATTRS{idVendor}=="0403"
    ATTRS{idProduct}=="6001"
    ATTRS{bcdDevice}=="0400"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{product}=="USB <-> Serial"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="2316"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.31-14-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

[COLOR=Red]  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2658"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d8"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00002658sv00001043sd000082D8bc0Csc03i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""[/COLOR]

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Nekativ on 2009-11-19
Alright I managed to write my own rule under /etc/udev/rules.d/10-persistent-transceiver.conf

```
ATTRS{device}=="0x2658", NAME="transceiver1"
```

I then had to restart udev with 'restart udev' command.

Works great, thanks for the help sisco311.

---

