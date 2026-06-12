---
title: "Wammu - finding usb port for my Nokia 6303i"
date: 2010-07-26
forum: General Help
---

### Post by 71GA on 2010-07-26
Hello i did a search on this already but i cant find the solution. I start Wammu phone wizzard and i select:

[LIST=1]
[*]guided configuration
[*]USB cable
[*]Nokia phone
[*]Nokia proprietary protocol
[*]DKU5 cable **(i am noob at this question totaly and am not sure if i choose right one)**
[*][COLOR=Green]**Here in step six I need to type something like "/dev/ttyS7" or something similar, but I don't know what exactly.**[/COLOR]
[/LIST]
I did a search in console writing command "**lsusb**" and here is what i get:

**Bus 002 Device 007: ID 0421:01b2 Nokia Mobile Phones **
Bus 002 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 002 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[COLOR=Green]**sooo... how do i know what to write in step 6. ???**[/COLOR]


Thank you!

---

### Post by elricscripts on 2010-08-10
This might help:
[http://z0manifest.blogspot.com/2009/03/wammu-and-finding-usb-ports.html](http://z0manifest.blogspot.com/2009/03/wammu-and-finding-usb-ports.html)

---

### Post by pdc124 on 2010-12-17
heres my hardware  - i dont know what option to select either !
> 3: udi = '/org/freedesktop/Hal/devices/usb_device_421_1b2_356036038146522'
  info.vendor = 'Nokia Mobile Phones'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1057 (0x421)
  usb_device.product_id = 434 (0x1b2)
  usb_device.vendor = 'Nokia Mobile Phones'
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_421_1b2_356036038146522'
  usb_device.max_power = 8 (0x8)
  usb_device.product = 'Nokia 6303 classic'
  usb_device.num_ports = 0 (0x0)
  usb_device.serial = '356036038146522'
  info.product = 'Nokia 6303 classic'
  usb_device.speed = 12.0000
  usb_device.version = 2.00000
  usb_device.can_wake_up = false
  usb_device.linux.device_number = 6 (0x6)
  usb_device.device_revision_bcd = 2192 (0x890)
  linux.device_file = '/dev/bus/usb/001/006'
  usb_device.bus_number = 1 (0x1)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_605_noserial'
  info.linux.driver = 'usb'


---

### Post by dining_philosopher on 2010-12-27
I also failed to connect Nokia 6303i with wammu. Given article contains very obscure suggestions about which bloody string shouid be in device name. My linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1' leads to "Error opening device. Unknown, busy or no permissions" (code 2) (even from sudo).

wormball@wormball-desktop:~$ lsusb | grep -i nokia
Bus 005 Device 006: ID 0421:035a Nokia Mobile Phones 

hwinfo
>   1: udi = '/org/freedesktop/Hal/devices/usb_device_421_35a_354345049823512'
  info.vendor = 'Nokia Mobile Phones'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_421_35a_354345049823512'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1'
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1057 (0x421)
  usb_device.product_id = 858 (0x35a)
  usb_device.vendor = 'Nokia Mobile Phones'
  info.subsystem = 'usb_device'
  usb_device.product = 'Nokia 6303i classic'
  info.product = 'Nokia 6303i classic'
  usb_device.num_ports = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2'
  usb_device.serial = '354345049823512'
  usb_device.device_revision_bcd = 1808 (0x710)
  usb_device.version = 2.00000
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 6 (0x6)
  usb_device.is_self_powered = false
  usb_device.can_wake_up = false
  usb_device.bus_number = 5 (0x5)
  linux.device_file = '/dev/bus/usb/005/006'


---

