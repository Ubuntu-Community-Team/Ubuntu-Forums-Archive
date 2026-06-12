---
title: "udev rules for Sierra 598u"
date: 2009-10-27
forum: General Help
---

### Post by levesqu6 on 2009-10-27
I have a Sprint Sierra Wireless 598u working on 8.10 using wvdial. Issue is that the card changes what ttyUSB# it is on at bootup so wvdial cant always find it. So i have set out to create a udev rule for the device. However it registers itself as 4 identical ttyUSB# devices. I want to set things up so that whatever it gets registered as has a symbolic link to /dev/ttyS30 so wvdial can merely be pointed to /dev/ttyS30 all the time. In the example below the modem was put at ttyUSB2 in this particular boot up. So i would want ttyUSB2 linked to /dev/ttyS30.

```
 dmesg | grep tty
[   10.209587] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   10.290005] usb 2-1: pl2303 converter now attached to ttyUSB1
[   12.688059] usb 1-2: Sierra USB modem converter now attached to ttyUSB2
[   12.688183] usb 1-2: Sierra USB modem converter now attached to ttyUSB3
[   12.688288] usb 1-2: Sierra USB modem converter now attached to ttyUSB4
[   12.688395] usb 1-2: Sierra USB modem converter now attached to ttyUSB5
 
```

my output from 
udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB2) > ttyUSB2.info

```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB2/tty/ttyUSB2':
    KERNEL=="ttyUSB2"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB2/tty':
    KERNELS=="tty"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB2':
    KERNELS=="ttyUSB2"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="sierra"
    ATTRS{suspend_status}=="0"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="sierra"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="09"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v1199p0025d0003dc00dsc00dp00icFFiscFFipFF"
    ATTRS{interface}=="Data Interface"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="3465"
    ATTRS{idVendor}=="1199"
    ATTRS{idProduct}=="0025"
    ATTRS{bcdDevice}=="0003"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sierra Wireless, Incorporated"
    ATTRS{product}=="Sierra Wireless USB 598"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="110"
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
    ATTRS{manufacturer}=="Linux 2.6.27-14-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27c8"
    ATTRS{subsystem_vendor}=="0x1462"
    ATTRS{subsystem_device}=="0x7265"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d000027C8sv00001462sd00007265bc0Csc03i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

output from
udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB3) > ttyUSB3.info

```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB3/tty/ttyUSB3':
    KERNEL=="ttyUSB3"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB3/tty':
    KERNELS=="tty"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/ttyUSB3':
    KERNELS=="ttyUSB3"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="sierra"
    ATTRS{suspend_status}=="0"
    ATTRS{port_number}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="sierra"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="09"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v1199p0025d0003dc00dsc00dp00icFFiscFFipFF"
    ATTRS{interface}=="Data Interface"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="3495"
    ATTRS{idVendor}=="1199"
    ATTRS{idProduct}=="0025"
    ATTRS{bcdDevice}=="0003"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sierra Wireless, Incorporated"
    ATTRS{product}=="Sierra Wireless USB 598"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="110"
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
    ATTRS{manufacturer}=="Linux 2.6.27-14-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27c8"
    ATTRS{subsystem_vendor}=="0x1462"
    ATTRS{subsystem_device}=="0x7265"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d000027C8sv00001462sd00007265bc0Csc03i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

as you can see the devices are the same except for 
KERNELS
ATTRS{port_number}
ATTRS{urbnum}

the first variable is the original problem, so its not useful for rule making. If i use port_number as a rule, the machine locks up when i reset udev. ATTRS{urbnum} seems to be a randomly assigned value, so it is not useful for rule making. I think i need to make a bash script to pass the name, but cannot find anything unique amongst the sierra devices to find the one that is the actual modem. I have found examples where ls 

here are my current rules. The first two work great. The last one doesnt do anything useful since the symbolic link location still changes with different ttyUSB# numbers.

```
cat /etc/udev/rules.d/50-local.rules
KERNEL=="ttyUSB?", ATTRS{idProduct}=="6001", ATTRS{manufacturer}=="FTDI", SYMLINK+="ttyS20"
KERNEL=="ttyUSB?", ATTRS{idProduct}=="2303", ATTRS{manufacturer}=="Prolific Technology Inc.", SYMLINK+="ttyS21"
KERNEL=="ttyUSB*", ATTRS{product}=="Sierra Wireless USB 598", SYMLINK+="ttyS3%n"

```

```
ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2009-10-27 14:47 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-10-27 14:47 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-10-27 14:47 /dev/ttyS2
lrwxrwxrwx 1 root root        7 2009-10-27 14:47 /dev/ttyS20 -> ttyUSB0
lrwxrwxrwx 1 root root        7 2009-10-27 15:14 /dev/ttyS21 -> ttyUSB1
crw-rw---- 1 root dialout 4, 67 2009-10-27 14:47 /dev/ttyS3
lrwxrwxrwx 1 root root        7 2009-10-27 15:07 /dev/ttyS32 -> ttyUSB2
lrwxrwxrwx 1 root root        7 2009-10-27 15:07 /dev/ttyS33 -> ttyUSB3
lrwxrwxrwx 1 root root        7 2009-10-27 15:07 /dev/ttyS34 -> ttyUSB4
lrwxrwxrwx 1 root root        7 2009-10-27 15:07 /dev/ttyS35 -> ttyUSB5

```

---

### Post by levesqu6 on 2009-10-29
i was unable to fix this using udev. i attempted to write a bash script that passed udev the number for the symbolic links, but it didnt work. So i put a script in /etc/rc.local and 

rc.local
```

#create symbolic links for modem
/usr/bin/FindSierraModem.sh &

# connect to cell network
ifdown eth1
#open wvdial in a screen
screen -d -m wvdial
ifup eth1

```

i have to ifdown and ifup here otherwise the PPO connection doesnt work. things appear to get routed through the ethernet connection instead.

heres FindSierraModem.sh

```

#!/bin/bash

dir=/sys/bus/usb-serial/drivers/sierra
search=$dir/tty*

let NUM=0

for file in $search
do
#create symbolic links to modem starting at ttyS30
echo `ln -s /dev/${file##/*/} /dev/ttyS3$NUM`
#increment counter
let NUM=NUM+1
done

exit 0

```

this probably isnt the best way to do this, but it works well enough for now.

---

### Post by RussNelson on 2011-03-07
s3:# cat 93-sierra.rules 
SUBSYSTEMS=="usb-serial", DRIVERS=="sierra", SYMLINK+="modem$ATTR{port_number}" 

Gives me /dev/modem0 /dev/modem1 /dev/modem2 and /dev/modem3 even though they're /dev/ttyS1 through 4.

---

