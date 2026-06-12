---
title: "Problem with udev rules"
date: 2011-01-29
forum: General Help
---

### Post by gordtulloch on 2011-01-29
Hi there:

I'm trying to get a camera (Meade Deep Sky Imager Pro) working with Ubuntu 10.04 64bit. I added the following as /etc/dev/rules.d/deepskyimager (owned by root perms 644 same as the other files in the folder) - the camera has an 8051 in it that needs firmware loaded before it can be used so the first rule loads the firmware and the second sets up the device...

# 1. Pre-renumeration IDs
# Meade DSI
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="156c", SYSFS{idProduct}=="0100", ENV{DEVICE}!="", \
RUN+="/sbin/fxload -t fx2 -D $ENV{DEVICE} -I /lib/firmware/meade-deepskyimager.hex"

# 2. Post-renumeration IDs
# Meade DSI
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="156c", SYSFS{idProduct}=="0101", ENV{DEVICE}!="", \
MODE="0666", SYMLINK+="deepskyimager.%n"

After doing a 'service restart udev' and 'sudo udevadm control --log-priority=debug' I see the following when I plug the device in:

Jan 29 09:59:51 GordT-PC kernel: [508902.200028] usb 1-2: new high speed USB device using ehci_hcd and address 14
Jan 29 09:59:51 GordT-PC udevd[1562]: seq 1937 queued, 'add' 'usb'
Jan 29 09:59:51 GordT-PC udevd[1562]: passed 250 bytes to monitor 0x7f001519f2d0
Jan 29 09:59:51 GordT-PC udevd-work[1603]: seq 1937 running
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b8370 has devpath '/devices/pci0000:00/0000:00:1a.7/usb1/1-2'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b84c0 has devpath '/devices/pci0000:00/0000:00:1a.7/usb1'
Jan 29 09:59:51 GordT-PC udevd[1562]: seq 1938 queued, 'add' 'usb'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151a6a00 has devpath '/devices/pci0000:00/0000:00:1a.7'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b4020 has devpath '/devices/pci0000:00'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: IMPORT 'usb_id --export /devices/pci0000:00/0000:00:1a.7/usb1/1-2' /lib/udev/rules.d/40-libgphoto2-2.rules:11
Jan 29 09:59:51 GordT-PC udevd-work[1603]: 'usb_id --export /devices/pci0000:00/0000:00:1a.7/usb1/1-2' started
Jan 29 09:59:51 GordT-PC usb_id[1733]: custom logging function 0x7f2e36f9f010 registered
Jan 29 09:59:51 GordT-PC usb_id[1733]: device 0x7f2e36f9f160 has devpath '/devices/pci0000:00/0000:00:1a.7/usb1/1-2'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=156c'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ENC=156c'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ID=156c'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_MODEL=0100'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ENC=0100'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ID=0100'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0000'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=156c_0100'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACES=:ffffff:'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: 'usb_id --export /devices/pci0000:00/0000:00:1a.7/usb1/1-2' returned with exitcode 0
Jan 29 09:59:51 GordT-PC udevd-work[1603]: LINK 'char/189:13' /lib/udev/rules.d/50-udev-default.rules:4
Jan 29 09:59:51 GordT-PC udevd-work[1603]: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:62
Jan 29 09:59:51 GordT-PC udevd-work[1603]: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
Jan 29 09:59:51 GordT-PC udevd-work[1603]: no node name set, will use kernel supplied name 'bus/usb/001/014'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: created db file for '/devices/pci0000:00/0000:00:1a.7/usb1/1-2' in '/dev/.udev/db/usb:1-2'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: creating device node '/dev/bus/usb/001/014', devnum=189:13, mode=0664, uid=0, gid=0
Jan 29 09:59:51 GordT-PC udevd-work[1603]: preserve file '/dev/bus/usb/001/014', because it has correct dev_t
Jan 29 09:59:51 GordT-PC udevd-work[1603]: chmod(/dev/bus/usb/001/014, 020664)
Jan 29 09:59:51 GordT-PC udevd-work[1603]: creating symlink '/dev/char/189:13' to '../bus/usb/001/014'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: passed 471 bytes to monitor 0x7f00151b8370
Jan 29 09:59:51 GordT-PC udevd-work[1603]: passed -1 bytes to monitor 0x7f00151a7530
Jan 29 09:59:51 GordT-PC udevd[1562]: seq 1937 done with 0
Jan 29 09:59:51 GordT-PC udevd[1562]: passed 273 bytes to monitor 0x7f001519f2d0
Jan 29 09:59:51 GordT-PC udevd-work[1603]: seq 1937 processed with 0
Jan 29 09:59:51 GordT-PC udevd-work[1603]: seq 1938 running
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f001519f140 has devpath '/devices/pci0000:00/0000:00:1a.7/usb1/1-2'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b4680 has devpath '/devices/pci0000:00/0000:00:1a.7/usb1'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b84c0 has devpath '/devices/pci0000:00/0000:00:1a.7'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: device 0x7f00151b8a60 has devpath '/devices/pci0000:00'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: RUN '/sbin/modprobe -b $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jan 29 09:59:51 GordT-PC udevd-work[1603]: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/sbin/modprobe -b usb:v156Cp0100d0000dcFFdscFFdpFFicFFiscFFipFF' started
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/sbin/modprobe' (stderr) 'FATAL: Module usb:v156Cp0100d0000dcFFdscFFdpFFicFFiscFFipFF not found.'
Jan 29 09:59:51 GordT-PC udevd-work[1603]: '/sbin/modprobe -b usb:v156Cp0100d0000dcFFdscFFdpFFicFFiscFFipFF' returned with exitcode 1
Jan 29 09:59:51 GordT-PC udevd-work[1603]: passed 295 bytes to monitor 0x7f00151b3800
Jan 29 09:59:51 GordT-PC udevd-work[1603]: passed -1 bytes to monitor 0x7f00151a7530
Jan 29 09:59:51 GordT-PC udevd-work[1603]: seq 1938 processed with 0
Jan 29 09:59:51 GordT-PC udevd[1562]: seq 1938 done with 0
Jan 29 09:59:51 GordT-PC kernel: [508902.350451] usb 1-2: configuration #1 chosen from 1 choice

I can't see anything that gives me a hint why the rules aren't being executed, any pointers on what to look at?

Regards,
  Gord

---

