---
title: "Logitech Cordless Trackman Optical"
date: 2009-07-10
forum: General Help
---

### Post by Garath531 on 2009-07-10
Can someone help me get my Logitech Cordless Trackman Optical working on Ubuntu 9.04 (Jaunty Jakalope). I have a Compaq Presario C727us Notebook, and have no idea where to start, so any help would be greatly appreciated.

---

### Post by Canuck.old on 2009-12-02
Hello
  It seem that HAL has taken over devices like
trackballs. 
  I am having trouble making the left button on
my Cordless Optical Trackman work properly. The tracking seems
to work but...
  My system is a up to date 9.10 32 bit machine.

  A few tidbits:
A lsusb delivers - Bus 002 Device 002: ID 046d:c508 Logitech, Inc. Cordless Trackball
A lshal delivers - 
snip
udi = '/org/freedesktop/Hal/devices/usb_device_46d_c508_noserial'
  battery.charge_level.current = 7  (0x7)  (int)
  battery.charge_level.design = 7  (0x7)  (int)
  battery.charge_level.last_full = 7  (0x7)  (int)
  battery.charge_level.percentage = 100  (0x64)  (int)
  battery.command_interface = 'csr'  (string)
  battery.csr.has_res = false  (bool)
  battery.csr.has_sms = true  (bool)
  battery.csr.is_dual = false  (bool)
  battery.is_rechargeable = true  (bool)
  battery.present = true  (bool)
  battery.type = 'mouse'  (string)
  info.addons = {'hald-addon-usb-csr'} (string list)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.product = 'Cordless Optical TrackMan'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c508_noserial'  (string)
  info.vendor = 'Logitech, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/002/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 5376  (0x1500)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2'  (string)
  usb_device.max_power = 50  (0x32)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Cordless Trackball'  (string)
  usb_device.product_id = 50440  (0xc508)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Logitech, Inc.'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 1.1 (1.1) (double)
snip

A xinput list  "Cordless Optical Trackman" delivers
unable to find device Cordless Optical Trackman

Anybody understand what is happening? It seem to me that the
trackball is being misidentified. (??) I could use some help
here!

Thank you for your time.
dkr

---

