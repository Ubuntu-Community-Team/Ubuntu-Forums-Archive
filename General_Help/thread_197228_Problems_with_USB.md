---
title: "Problems with USB"
date: 2006-06-15
forum: General Help
---

### Post by jphantom on 2006-06-15
Hi, I am trying to use a usb device.  

 The device's power light comes on when I connect it but ls /dev   shows nothing like  /dev/ttyUSB0  which is what I need.

tail -f /var/log/messages shows the following when I have connected the device:

Jun 15 11:52:43 localhost kernel: [4295053.693000] usb 3-1: new full speed USB device using uhci_hcd and address 2


Does anyone have any ideas as to how to fix this?

---

### Post by mlind on 2006-06-15
What kind of device is it? Log entry shows that kernel has detected it.

If you're attaching removable storage, /media should contain mount point for
your device device and it should be mounted automatically.

---

### Post by jphantom on 2006-06-15
It is a programmer used for microprocessors.  All I need is some sort of link like /dev/ttyUSB0  for the makefile to work.

---

### Post by mlind on 2006-06-15
usb devices are located on /sys/bus/usb/devices/

Can you find your device using 

```

systool -vb usb

```

udevinfo is much better, but I'm not sure about the syntax.. 
```

udevinfo -a -p /sys/bus/usb/devices

```

Then you can write udev rule for the device that will create the /dev node
using [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by mlind on 2006-06-15
I tried this with my Logitech gamepad using the html document on my earlier post.

USB devices are listed on /sys/bus/usb/devices, but I didn't quite get it how to
query them using **udevinfo** tool if you don't know the actual device node.

Here's a little script that iterates the info and views it
```

for i in /sys/bus/usb/devices/*; do udevinfo -a -p $i; done | less

```

Scrolling down the output I found my USB joypad from there which looked like
```

looking at class device '/sys/devices/pci0000:00/0000:00:10.0/usb1/1-2':
    KERNEL=="1-2"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0288"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="4"
    SYSFS{idProduct}=="8866"
    SYSFS{idVendor}=="0925"
    SYSFS{manufacturer}=="WiseGroup._Ltd"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="MP-8866 Dual USB Joypad"
    SYSFS{speed}=="1.5"
    SYSFS{version}==" 1.00"

```

Then I created a new rule based on "product" field. I guess you can use any other
field too, as long as it's unique and static.

```

sudo touch /etc/udev/rules.d/10-local.rules

```

then I opened file using nano and created a rule
```

## my joypad
BUS="usb", SYSFS{**product**}="MP-8866*" NAME="my_joypad" SYMLINK+="mythingy"

```

SYSFS attributes allows string matching, so asterisk (*) means zero or more characters.

then I saved the rule file and restarted udev
```

sudo /etc/init.d/udev restart

```

after this I had
```

$ ls -la /dev/my*
crw-rw-r-- 1 root root 189, 3 2006-06-16 03:21 /dev/my_joypad
lrwxrwxrwx 1 root root      9 2006-06-16 03:21 /dev/mythingy -> my_joypad

```

That SYMLINK rule isnt' necessary if you don't need it.

---

### Post by flashbackk on 2006-06-15
I need help with this ,also. I am trying to setup Gnome PPP to use my motorola phone with an usb cable.  I would like to find where it is. It appears I need a /dev/tty* designation.

---

### Post by mlind on 2006-06-16
[QUOTE=flashbackk]I need help with this ,also. I am trying to setup Gnome PPP to use my motorola phone with an usb cable.  I would like to find where it is. It appears I need a /dev/tty* designation.[/QUOTE]

when you plug your phone in, can you see if it gets a block device assigned ?
use 'dmesg' command which will print out kernel buffer ring.

It should be /dev/sg0 or similar.
if you see the device, post output of 
```

udevinfo -a -p $(udevinfo -q path -n /dev/sg0)

```

If you can't get any info if block device is beign assigned to your phone, 
try the command that iterates usb devices, find your phone from there and
post the printed output.

---

